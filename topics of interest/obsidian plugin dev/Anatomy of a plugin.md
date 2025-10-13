The Plugin class defines the lifecycle of a plugin and exposes the operations available to all plugins:

```ts
import { Plugin } from 'obsidian';

export default class ExamplePlugin extends Plugin {
  async onload() {
    // Configure resources needed by the plugin.
  }
  async onunload() {
    // Release any resources configured by the plugin.
  }
}
```

Plugin lifecycle 
onload() runs whenever the user starts using the plugin in Obsidian. This is where you'll configure most of the plugin's capabilities.

onunload() runs when the plugin is disabled. Any resources that your plugin is using must be released here to avoid affecting the performance of Obsidian after your plugin has been disabled.

To better understand when these methods are called, you can print a message to the console whenever the plugin loads and unloads. The console is a valuable tool that lets developers monitor the status of their code.

To view the console:

Toggle the Developer Tools by pressing Ctrl+Shift+I in Windows and Linux, or Cmd-Option-I on macOS.
Click on the Console tab in the Developer Tools window.

```ts
import { Plugin } from 'obsidian';

export default class ExamplePlugin extends Plugin {
  async onload() {
    console.log('loading plugin')
  }
  async onunload() {
    console.log('unloading plugin')
  }
}
```

## Use Svelte in your plugin

Svelte is built around a compiler that preprocesses your code and outputs optimized vanilla JavaScript. This means that it doesn't need a virtual DOM to track state changes, which allows your plugin to run with minimal additional overhead.

Configure your plugin 

To build a plugin with Svelte, you need to install the dependencies and configure your plugin to compile code written using Svelte. If you only want to use TypeScript's _type-only_ features, you don't need `svelte-preprocess`.

Add Svelte to your plugin dependencies:

```
npm install --save-dev svelte svelte-preprocess esbuild-svelte svelte-check
```

Svelte requires at least TypeScript 5.0. To update to Typescript 5.0 run the following in your terminal.

```
npm install typescript@~5.0.0
```

Extend the `tsconfig.json` to enable additional type checking for common Svelte issues. `verbatimModuleSyntax` is needed for `svelte-preprocess` and `skipLibCheck` is needed for `svelte-check` to work correctly.

```json
{
  "compilerOptions": {
    "verbatimModuleSyntax": true,
    "skipLibCheck": true,
    // ...
  },
  "include": [
    "**/*.ts",
    "**/*.svelte"
  ]
}
```

In `esbuild.config.mjs`, add the following imports to the top of the file:

```js
import esbuildSvelte from 'esbuild-svelte';
import { sveltePreprocess } from 'svelte-preprocess';
```

Add Svelte to the list of plugins.

```js
const context = await esbuild.context({
  plugins: [
    esbuildSvelte({
      compilerOptions: { css: 'injected' },
      preprocess: sveltePreprocess(),
    }),
  ],
  // ...
});
```

Add a script to run `svelte-check` to your `package.json`.

```js
{
  // ...
  "scripts": {
    // ...
    "svelte-check": "svelte-check --tsconfig tsconfig.json"
  }
}
```

## Create a Svelte component

In the root directory of the plugin, create a new file called Counter.svelte:

```ts
<script lang="ts">
  interface Props {
    startCount: number;
  }

  let {
    startCount
  }: Props = $props();

  let count = $state(startCount);

  export function increment() {
    count += 1;
  }
</script>

<div class="number">
  <span>My number is {count}!</span>
</div>

<style>
  .number {
    color: red;
  }
</style>
```

## Mount the Svelte component 

To use the Svelte component, it needs to be mounted on an existing [HTML element](https://docs.obsidian.md/Plugins/User+interface/HTML+elements). For example, if you are mounting on a custom [ItemView](https://docs.obsidian.md/Reference/TypeScript+API/ItemView) in Obsidian:

```ts
import { ItemView, WorkspaceLeaf } from 'obsidian';

// Import the Counter Svelte component and the `mount` and `unmount` methods.
import Counter from './Counter.svelte';
import { mount, unmount } from 'svelte';

export const VIEW_TYPE_EXAMPLE = 'example-view';

export class ExampleView extends ItemView {
  // A variable to hold on to the Counter instance mounted in this ItemView.
  counter: ReturnType<typeof Counter> | undefined;

  constructor(leaf: WorkspaceLeaf) {
    super(leaf);
  }

  getViewType() {
    return VIEW_TYPE_EXAMPLE;
  }

  getDisplayText() {
    return 'Example view';
  }

  async onOpen() {
    // Attach the Svelte component to the ItemViews content element and provide the needed props.
    this.counter = mount(Counter, {
      target: this.contentEl,
      props: {
        startCount: 5,
      }
    });

    // Since the component instance is typed, the exported `increment` method is known to TypeScript.
    this.counter.increment();
  }

  async onClose() {
    if (this.counter) {
      // Remove the Counter from the ItemView.
      unmount(this.counter);
    }
  }
}
```


