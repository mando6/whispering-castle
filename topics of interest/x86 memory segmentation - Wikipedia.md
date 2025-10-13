---
title: "x86 memory segmentation - Wikipedia"
source: "https://en.wikipedia.org/wiki/X86_memory_segmentation"
author:
  - "[[Contributors to Wikimedia projects]]"
published: 2002-11-23
created: 2025-06-06
description:
tags:
  - "clippings"
---
**x86 memory segmentation** is a term for the kind of [memory segmentation](https://en.wikipedia.org/wiki/Memory_segmentation "Memory segmentation") characteristic of the Intel [x86](https://en.wikipedia.org/wiki/X86 "X86") computer [instruction set architecture](https://en.wikipedia.org/wiki/Instruction_set_architecture "Instruction set architecture"). The x86 architecture has supported memory segmentation since the original [Intel 8086](https://en.wikipedia.org/wiki/Intel_8086 "Intel 8086") (1978), but *x86 memory segmentation* is a plainly descriptive [retronym](https://en.wikipedia.org/wiki/Retronym "Retronym"). The introduction of memory segmentation mechanisms in this architecture reflects the legacy of earlier 80xx processors, which initially [^1] could only address 16, or later [^2] 64 KB of memory (16,384 or 65,536 [bytes](https://en.wikipedia.org/wiki/Byte "Byte")), and whose instructions and registers were optimised for the latter. Dealing with larger addresses and more memory was thus comparably slower, as that capability was somewhat grafted-on in the Intel 8086. Memory segmentation could keep programs compatible, relocatable in memory, and by confining significant parts of a program's operation to 64 KB segments, the program could still run faster.

In 1982, the [Intel 80286](https://en.wikipedia.org/wiki/Intel_80286 "Intel 80286") added support for [virtual memory](https://en.wikipedia.org/wiki/Virtual_memory "Virtual memory") and [memory protection](https://en.wikipedia.org/wiki/Memory_protection "Memory protection"); the original mode was renamed **[real mode](https://en.wikipedia.org/wiki/Real_mode "Real mode")**, and the new version was named **[protected mode](https://en.wikipedia.org/wiki/Protected_mode "Protected mode")**. The [x86-64](https://en.wikipedia.org/wiki/X86-64 "X86-64") architecture, introduced in 2003, has largely dropped support for segmentation in 64-bit mode.

In both real and protected modes, the system uses 16-bit *segment registers* to derive the actual memory address. In real mode, the registers CS, DS, SS, and ES point to the currently used program [code segment](https://en.wikipedia.org/wiki/Code_segment "Code segment") (CS), the current [data segment](https://en.wikipedia.org/wiki/Data_segment "Data segment") (DS), the current [stack segment](https://en.wikipedia.org/wiki/Stack_segment "Stack segment") (SS), and one *extra* segment determined by the system programmer (ES). The [Intel 80386](https://en.wikipedia.org/wiki/Intel_80386 "Intel 80386"), introduced in 1985, adds two additional segment registers, FS and GS, with no specific uses defined by the hardware. The way in which the segment registers are used differs between the two modes.[^3]

The choice of segment is normally defaulted by the processor according to the function being executed. Instructions are always fetched from the code segment. Any data reference to the stack, including any stack push or pop, uses the stack segment; data references indirected through the BP register typically refer to the stack and so they default to the stack segment. The extra segment is the mandatory destination for string operations (for example MOVS or CMPS); for this one purpose only, the automatically selected segment register cannot be overridden. All other references to data use the data segment by default. The data segment is the default source for string operations, but it can be overridden. FS and GS have no hardware-assigned uses. The instruction format allows an optional *segment prefix* byte which can be used to override the default segment for selected instructions if desired.[^4]

## Real mode

![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/db/Overlapping_realmode_segments.svg/330px-Overlapping_realmode_segments.svg.png)

Three segments in real mode memory (click on image to enlarge). There is an overlap between segment 2 and segment 3; the bytes in the turquoise area can be used from both segment selectors. If however the program code dealing with segment 2 never uses offsets large enough to reach 0x77D0, then it can be thought of as a shorter, non-overlapping, and at most 30,672-byte segment.

In [real mode](https://en.wikipedia.org/wiki/Real_mode "Real mode") or [V86 mode](https://en.wikipedia.org/wiki/Virtual_8086_mode "Virtual 8086 mode"), the fundamental size of a *segment* is 65,536  [bytes](https://en.wikipedia.org/wiki/Byte "Byte"), with individual bytes being addressed using 16-bit *offsets*.

The 16-bit segment selector in the segment register is interpreted as the most significant 16 bits of a linear 20-bit address, called a segment address, of which the remaining four least significant bits are all zeros. The segment address is always added to a 16-bit offset in the instruction to yield a *linear* address, which is the same as [physical address](https://en.wikipedia.org/wiki/Physical_address "Physical address") in this mode. For instance, the segmented address 06EFh:1234h (here the suffix "h" means [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal")) has a segment selector of 06EFh, representing a segment address of 06EF0h, to which the offset is added, yielding the linear address 06EF0h + 1234h = 08124h.

(The leading zeros of the linear address, segmented addresses, and the segment and offset fields are shown here for clarity. They are usually omitted.)

| `0000 0110 1110 1111` `0000` | **Segment** | 16 bits, shifted 4 bits left (or multiplied by 0x10) |
| --- | --- | --- |
| `+     ` `0001 0010 0011 0100` | **Offset** | 16 bits |
|  |  |
| `0000 1000 0001 0010 0100` | **Address** | 20 bits |

Because of the way the segment address and offset are added, a single linear address can be mapped to up to 2 <sup>12</sup> = 4096 distinct segment:offset pairs. For example, the linear address 08124h can have the segmented addresses 06EFh:1234h, 0812h:0004h, 0000h:8124h, etc. This could be confusing to programmers accustomed to unique addressing schemes, but it can also be used to advantage, for example when addressing multiple nested data structures.

While real mode segments are *technically* always 64  [KB](https://en.wikipedia.org/wiki/Kilobyte "Kilobyte") long, the practical effect is only that no segment can be *longer* than 64 KB, rather than that every segment as actually used in a program *must* be treated as 64 KB long – dealing with effectively smaller segments is possible: usable sizes range from 16 through 65,536 bytes, in 16-byte steps. Because there is no protection or privilege limitation in real mode, it is still entirely up to the program to coordinate and keep within the bounds of any segments. This is true both when a segment is programmatically treated as smaller than, or the full 64 KB, but it is also true that any program can always access any memory by just changing segments, since it can arbitrarily set segment selectors to change segment addresses with absolutely no supervision. Therefore, while real mode can be thought of as allowing different segment lengths, and as allowing segments to be overlapping or non-overlapping as desired, none of this is restrictively enforced by the CPU.

The effective 20-bit [address space](https://en.wikipedia.org/wiki/Address_space "Address space") of PC/XT-generation CPUs limits the [addressable memory](https://en.wikipedia.org/wiki/Memory_address "Memory address") to 2 <sup>20</sup>  bytes, or 1,048,576 bytes (1  [MB](https://en.wikipedia.org/wiki/Megabyte "Megabyte")). This derived directly from the hardware design of the Intel 8086 (and, subsequently, the closely related 8088), which had exactly 20 [address pins](https://en.wikipedia.org/wiki/Address_bus "Address bus"). (Both were packaged in 40-pin DIP packages; even with only 20 address lines, the address and data buses were multiplexed to fit all the address and data lines within the limited pin count.)

Each segment begins at a multiple of 16 bytes, called a *paragraph*, from the beginning of the linear (flat) address space. That is, at 16 byte intervals. Since all segments are technically 64 KB long, this explains how overlap can occur between segments and why any location in the linear memory address space can be accessed with many segment:offset pairs. The actual location of the beginning of a segment in the linear address space can be calculated with *segment* × 16. Such address translations are carried out by the segmentation unit of the CPU.

### End-of-address-space quirkiness

The last segment, FFFFh (65535), begins at linear address FFFF0h (1048560), 16 bytes before the end of the 20-bit address space, and thus can access, with an offset of up to 65,536 bytes, up to 65,520 (65536−16) bytes past the end of the 20-bit address space of the 8086 or 8088 CPU. A further 4,094 next-highest 64K-segments also still cross that 1MB-threshold, but by less and less. On the 8086 and 8088 CPUs, these address accesses were wrapped around to the beginning of the address space such that 65535:16 would access address 0, and e.g. 65533:1000 would access address 952 of the linear address space. The fact that some programs written for the 8088 and 8086 relied on this quirky wrap-around as a feature led to the [Gate A20](https://en.wikipedia.org/wiki/Gate_A20 "Gate A20") compatibility issues in later CPU generations, with the [Intel 286](https://en.wikipedia.org/wiki/Intel_286 "Intel 286") and above, where the linear address space was expanded past 20 bits.

In 16-bit real mode, enabling applications to make use of multiple memory segments for a single data structure (in order to access more memory than available in any one 64K-segment) is quite complex, but was viewed as a necessary evil for all but the smallest tools (which could do with less memory). The root of the problem is that no appropriate address-arithmetic instructions suitable for flat addressing of the entire memory range are available. Flat addressing is possible by applying multiple instructions, which however leads to slower programs.

The *[memory model](https://en.wikipedia.org/wiki/X86_memory_models "X86 memory models")* concept derives from the setup of the segment registers. For example, in the *tiny model* CS=DS=SS, that is the program's code, data, and stack are all contained within a single 64 KB segment. In the *small* memory model DS=SS, so both data and stack reside in the same segment; CS points to a different code segment of up to 64 KB.

## Protected mode

![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Protected_mode_segments.svg/330px-Protected_mode_segments.svg.png)

Three segments in protected mode memory (click on image to enlarge), with the local descriptor table.

The [80286](https://en.wikipedia.org/wiki/Intel_80286 "Intel 80286") 's [protected mode](https://en.wikipedia.org/wiki/Protected_mode "Protected mode") extends the processor's address space to 2 <sup>24</sup> bytes (16 megabytes), but not by adjusting the shift value used to calculate a segment address from the value in a segment register. Instead, each 16-bit segment register now contains an index into a table of [segment descriptors](https://en.wikipedia.org/wiki/Segment_descriptors "Segment descriptors") containing 24-bit base addresses to which offsets are added. To support old software, the processor starts up in "real mode", a mode in which it uses the segmented addressing model of the 8086. There is a small difference though: the resulting physical address is no longer truncated to 20 bits, so [real mode](https://en.wikipedia.org/wiki/Real_mode "Real mode") pointers (but not 8086 pointers) can now refer to addresses from 100000 <sub>16</sub> through 10FFEF <sub>16</sub>. This nearly 64-kilobyte region of memory was known as the [High Memory Area](https://en.wikipedia.org/wiki/High_Memory_Area "High Memory Area") (HMA), and later versions of [DOS](https://en.wikipedia.org/wiki/DOS "DOS") could use it to increase the available "conventional" memory (i.e. within the first [MB](https://en.wikipedia.org/wiki/Megabyte "Megabyte")), by moving parts of DOS from conventional memory into the HMA. With the addition of the HMA, the total address space is approximately 1.06 MB. Though the 80286 does not truncate real-mode addresses to 20 bits, a system containing an 80286 can do so with hardware external to the processor, by gating off the 21st address line, the [A20 line](https://en.wikipedia.org/wiki/A20_line "A20 line"). The IBM PC AT provided the hardware to do this (for backward compatibility with software for the original [IBM PC](https://en.wikipedia.org/wiki/IBM_PC "IBM PC") and [PC/XT](https://en.wikipedia.org/wiki/IBM_PC/XT "IBM PC/XT") models), and so all subsequent " [AT](https://en.wikipedia.org/wiki/IBM_PC/AT "IBM PC/AT") -class" PC clones did as well.

286 protected mode was seldom used as it would have excluded the large body of users with 8086/88 machines. Moreover, it still necessitated dividing memory into 64k segments like was done in real mode. This limitation can be worked around on 32-bit CPUs which permit the use of memory pointers greater than 64k in size, however as the Segment Limit field is only 24-bit long, the maximum segment size that can be created is 16MB (although paging can be used to allocate more memory, no individual segment may exceed 16MB). This method was commonly used on Windows 3.x applications to produce a flat memory space, although as the OS itself was still 16-bit, API calls could not be made with 32-bit instructions. Thus, it was still necessary to place all code that performs API calls in 64k segments.

Once 286 protected mode is invoked, it could not normally be exited except by performing a hardware reset. Machines following the rising [IBM PC/AT](https://en.wikipedia.org/wiki/IBM_PC/AT "IBM PC/AT") standard could feign a reset to the CPU via the standardised keyboard controller, but this was significantly sluggish. Windows 3.x worked around both of these problems by intentionally triggering a [triple fault](https://en.wikipedia.org/wiki/Triple_fault "Triple fault") in the interrupt-handling mechanisms of the CPU, which would cause the IBM AT-compatible hardware to reset the CPU, nearly instantly, thus causing it to drop back into real mode.[^5]

A logical address consists of a 16-bit segment selector (supplying 13+1 address bits) and a 16-bit offset. The segment selector must be located in one of the segment registers. That selector consists of a 2-bit Requested [Privilege Level](https://en.wikipedia.org/wiki/Privilege_level "Privilege level") (RPL), a 1-bit Table Indicator (TI), and a 13-bit index.

When attempting address translation of a given logical address, the processor reads the 64-bit [segment descriptor](https://en.wikipedia.org/wiki/Segment_descriptor "Segment descriptor") structure from either the [Global Descriptor Table](https://en.wikipedia.org/wiki/Global_Descriptor_Table "Global Descriptor Table") when TI=0 or the [Local Descriptor Table](https://en.wikipedia.org/wiki/Local_Descriptor_Table "Local Descriptor Table") when TI=1. It then performs the privilege check:

max(CPL, RPL) ≤ DPL

where CPL is the current privilege level (found in the lower 2 bits of the CS register), RPL is the requested privilege level from the segment selector, and DPL is the descriptor privilege level of the segment (found in the descriptor). All privilege levels are integers in the range 0–3, where the lowest number corresponds to the highest privilege.

If the inequality is false, the processor generates a [general protection (GP) fault](https://en.wikipedia.org/wiki/General_protection_fault "General protection fault"). Otherwise, address translation continues. The processor then takes the 16-bit offset and compares it against the segment limit specified in the segment descriptor. If it is larger, a GP fault is generated. Otherwise, the processor adds the 24-bit segment base, specified in descriptor, to the offset, creating a linear physical address.

The privilege check is done only when the segment register is loaded, because [segment descriptors](https://en.wikipedia.org/wiki/Segment_descriptor "Segment descriptor") are cached in hidden parts of the segment registers.[^3]

In the [Intel 80386](https://en.wikipedia.org/wiki/Intel_80386 "Intel 80386") and later, protected mode retains the segmentation mechanism of 80286 protected mode, but a [paging](https://en.wikipedia.org/wiki/Paging "Paging") unit has been added as a second layer of address translation between the segmentation unit and the physical bus. Also, importantly, address offsets are 32-bit (instead of 16-bit), and the segment base in each segment descriptor is also 32-bit (instead of 24-bit). The general operation of the segmentation unit is otherwise unchanged. The paging unit may be enabled or disabled; if disabled, operation is the same as on the 80286. If the paging unit is enabled, addresses in a segment are now virtual addresses, rather than physical addresses as they were on the 80286. That is, the segment starting address, the offset, and the final 32-bit address the segmentation unit derived by adding the two are all virtual (or logical) addresses when the paging unit is enabled. When the segmentation unit generates and validates these 32-bit virtual addresses, the enabled paging unit finally translates these virtual addresses into physical addresses. The physical addresses are 32-bit on the [386](https://en.wikipedia.org/wiki/Intel_80386 "Intel 80386"), but can be larger on newer processors which support [Physical Address Extension](https://en.wikipedia.org/wiki/Physical_Address_Extension "Physical Address Extension").

As mentioned above, the 80386 also introduced two new general-purpose data segment registers, FS and GS, to the original set of four segment registers (CS, DS, ES, and SS).

A 386 CPU can be put back into real mode by clearing a bit in the CR0 control register, however this is a privileged operation in order to enforce security and robustness. By way of comparison, a 286 could only be returned to real mode by forcing a processor reset, e.g. by a [triple fault](https://en.wikipedia.org/wiki/Triple_fault "Triple fault") or using external hardware.

## Later developments

The [x86-64](https://en.wikipedia.org/wiki/X86-64 "X86-64") architecture does not use segmentation in long mode (64-bit mode). Four of the segment registers, CS, SS, DS, and ES, are forced to base address 0, and the limit to 2 <sup>64</sup>. The segment registers FS and GS can still have a nonzero base address. This allows operating systems to use these segments for special purposes. Unlike the [global descriptor table](https://en.wikipedia.org/wiki/Global_descriptor_table "Global descriptor table") mechanism used by legacy modes, the base address of these segments is stored in a [model-specific register](https://en.wikipedia.org/wiki/Model-specific_register "Model-specific register"). The x86-64 architecture further provides the special *SWAPGS* instruction, which allows swapping the [kernel mode](https://en.wikipedia.org/wiki/Kernel_mode "Kernel mode") and [user mode](https://en.wikipedia.org/wiki/User_mode "User mode") base addresses.

For instance, [Microsoft Windows](https://en.wikipedia.org/wiki/Microsoft_Windows "Microsoft Windows") on x86-64 uses the GS segment to point to the [Thread Environment Block](https://en.wikipedia.org/wiki/Win32_Thread_Information_Block "Win32 Thread Information Block"), a small data structure for each [thread](https://en.wikipedia.org/wiki/Thread_\(computer_science\) "Thread (computer science)"), which contains information about exception handling, thread-local variables, and other per-thread state. Similarly, the [Linux kernel](https://en.wikipedia.org/wiki/Linux_kernel "Linux kernel") uses the GS segment to store per-CPU data.

GS/FS are also used in [gcc](https://en.wikipedia.org/wiki/GNU_Compiler_Collection "GNU Compiler Collection") 's [thread-local storage](https://en.wikipedia.org/wiki/Thread-local_storage "Thread-local storage") and [canary-based](https://en.wikipedia.org/wiki/Buffer_overflow_protection#GNU_Compiler_Collection_.28GCC.29 "Buffer overflow protection") stack protector.

## Practices

Logical addresses can be explicitly specified in [x86 assembly language](https://en.wikipedia.org/wiki/X86_assembly_language "X86 assembly language"), e.g. (AT&T syntax):

```
movl $42, %fs:(%eax)  ; Equivalent to M[fs:eax]<-42) in RTL
```

or in [Intel syntax](https://en.wikipedia.org/wiki/Intel_syntax "Intel syntax"):

```
mov dword [fs:eax], 42
```

However, segment registers are usually used implicitly.

- All CPU instructions are implicitly fetched from the *[code segment](https://en.wikipedia.org/wiki/Code_segment "Code segment")* specified by the segment selector held in the CS register.
- Most memory references come from the *[data segment](https://en.wikipedia.org/wiki/Data_segment "Data segment")* specified by the segment selector held in the DS register. These may also come from the extra segment specified by the segment selector held in the ES register, if a segment-override prefix precedes the instruction that makes the memory reference. Most, but not all, instructions that use DS by default will accept an ES override prefix.
- Processor [stack](https://en.wikipedia.org/wiki/Run-time_stack "Run-time stack") references, either implicitly (e.g. **push** and **pop** instructions) or explicitly ([memory accesses using the (E)SP or (E)BP registers](https://en.wikipedia.org/wiki/Stack-based_memory_allocation "Stack-based memory allocation")) use the *stack segment* specified by the segment selector held in the SS register. For explicit references, the segment can be overridden.
- [String instructions](https://en.wikipedia.org/w/index.php?title=X86_string_instructions&action=edit&redlink=1 "X86 string instructions (page does not exist)") (e.g. **stos**, **movs**), along with data segment, also use the *extra segment* specified by the segment selector held in the ES register.

Segmentation cannot be turned off on x86-32 processors (this is true for 64-bit mode as well, but beyond the scope of discussion), so many 32-bit operating systems simulate a [flat memory model](https://en.wikipedia.org/wiki/Flat_memory_model "Flat memory model") by setting all segments' bases to 0 in order to make segmentation neutral to programs. For instance, the [Linux kernel](https://en.wikipedia.org/wiki/Linux_kernel "Linux kernel") sets up only 4 general purpose segments:

| Name | Description | Base | Limit | [DPL](https://en.wikipedia.org/wiki/Descriptor_Privilege_Level "Descriptor Privilege Level") |
| --- | --- | --- | --- | --- |
| \_\_KERNEL\_CS | Kernel code segment | 0 | 4 GiB | 0 |
| \_\_KERNEL\_DS | Kernel data segment | 0 | 4 GiB | 0 |
| \_\_USER\_CS | User code segment | 0 | 4 GiB | 3 |
| \_\_USER\_DS | User data segment | 0 | 4 GiB | 3 |

Since the base is set to 0 in all cases and the limit 4 GiB, the segmentation unit does not affect the addresses the program issues before they arrive at the [paging](https://en.wikipedia.org/wiki/Paging "Paging") unit. (This, of course, refers to 80386 and later processors, as the earlier x86 processors do not have a paging unit.)

Current Linux also uses GS to point to [thread-local storage](https://en.wikipedia.org/wiki/Thread-local_storage "Thread-local storage").

Segments can be defined to be either code, data, or system segments. Additional permission bits are present to make segments read only, read/write, execute, etc.

In protected mode, code may always modify all segment registers *except* CS (the [code segment](https://en.wikipedia.org/wiki/Code_segment "Code segment") selector). This is because the current privilege level (CPL) of the processor is stored in the lower 2 bits of the CS register. The only ways to raise the processor privilege level (and reload CS) are through the **lcall** (far call) and [**int** (interrupt)](https://en.wikipedia.org/wiki/INT_\(x86_instruction\) "INT (x86 instruction)") instructions. Similarly, the only ways to lower the privilege level (and reload CS) are through **lret** (far return) and **iret** (interrupt return) instructions. In real mode, code may also modify the CS register by making a far jump (or using an undocumented `POP CS` instruction on the 8086 or 8088).[^6] Of course, in real mode, there are no privilege levels; all programs have absolute unchecked access to all of memory and all CPU instructions.

For more information about segmentation, see the [IA-32](https://en.wikipedia.org/wiki/IA-32 "IA-32") manuals freely available on the [AMD](https://en.wikipedia.org/wiki/AMD "AMD") or [Intel](https://en.wikipedia.org/wiki/Intel "Intel") websites.

## See also

- [x86 memory models](https://en.wikipedia.org/wiki/X86_memory_models "X86 memory models")
- [THE multiprogramming system](https://en.wikipedia.org/wiki/THE_multiprogramming_system "THE multiprogramming system")
- [Split octal](https://en.wikipedia.org/wiki/Split_octal "Split octal")

## External links

- [Home of the IA-32 Intel Architecture Software Developer's Manual](http://www.intel.com/products/processor/manuals/index.htm)
- [The Segment:Offset Addressing Scheme](http://thestarman.pcministry.com/asm/debug/Segments.html)

[^1]: in the [Intel 8008](https://en.wikipedia.org/wiki/Intel_8008 "Intel 8008")

[^2]: from the [Intel 8080](https://en.wikipedia.org/wiki/Intel_8080 "Intel 8080")

[^3]: "Intel 64 and IA-32 Architectures Software Developer's Manual", Volume 3, "System Programming Guide", published in 2011, Page "Vol. 3A 3-11", the book is written: " *Every segment register has a “visible” part and a “hidden” part. (The hidden part is sometimes referred to as a “descriptor cache” or a “shadow register.”) When a segment selector is loaded into the visible part of a segment register, the processor also loads the hidden part of the segment register with the base address, segment limit, and access control information from the segment descriptor pointed to by the segment selector. The information cached in the segment register (visible and hidden) allows the processor to translate addresses without taking extra bus cycles to read the base address and limit from the segment descriptor.*"

[^4]: Intel Corporation (2004). [*IA-32 Intel Architecture Software Developer's Manual Volume 1: Basic Architecture*](http://www.intel.com/content/dam/www/public/us/en/documents/manuals/64-ia-32-architectures-software-developer-vol-1-manual.pdf) (PDF).

[^5]: ["DevBlogs"](http://blogs.msdn.com/b/larryosterman/archive/2005/02/08/369243.aspx).

[^6]: `POP CS` must be used with extreme care and has limited usefulness, because it immediately changes the effective address that will be computed from the instruction pointer to fetch the next instruction. Generally, a far jump is much more useful. The existence of `POP CS` is probably an accident, as it follows a pattern of PUSH and POP instruction opcodes for the four segment registers on the 8086 and 8088.