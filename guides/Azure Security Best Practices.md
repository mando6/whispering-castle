**Set Up Your Users with Phish Resistant Multifactor Authentication (MFA)**

**Ensure that the MFA method used is phishing-resistant**

You can do so by using:

- [**Password Authentication**(opens in a new tab)](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-authentication-passwordless-deployment)
- [**Number matching**(opens in a new tab)](https://learn.microsoft.com/en-us/azure/active-directory/authentication/how-to-mfa-number-match)

If a customer refuses to use MFA, don't provide them administrator role access to Azure AD or write permissions to Azure Subscriptions. Recall that you are financially responsible if your customer is compromised.

https://learn.microsoft.com/en-us/partner-center/security/partner-security-requirements-mandating-mfa

https://learn.microsoft.com/en-us/partner-center/security/mfa-for-users

- My Partner Center/Customer's tenant has Microsoft Entra ID P1
    - Use [Conditional Access](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-policy-common) to enforce MFA.
- My Partner Center/Customer's tenant has Microsoft Entra ID P2
    - Use [Conditional Access](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-policy-common) to enforce MFA.
    - [Implement risk-based policies](https://learn.microsoft.com/en-us/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) using Microsoft Entra ID Protection.
    - For your Partner Center tenant, you might qualify for Microsoft 365 E3 or E5, depending on your Internal Use Rights (IUR) benefits. These SKUs include Microsoft Entra ID P1 or 2, respectively.
    - For your customer's tenant, we recommend enabling [security defaults](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).
        - If your customer is using apps that require legacy authentication, those apps won't function after you enable security defaults. If the app can't be replaced, removed, or updated to use modern authentication, you can enforce MFA through [per-user MFA](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-userstates).
- - Adopt the Secure Application Model framework. All partners integrating with Partner Center APIs must adopt the [Secure Application Model framework](https://learn.microsoft.com/en-us/partner-center/develop/enable-secure-app-model) for any app and user auth model applications.
- Disable [user consent](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/user-consent) in Partner Center Microsoft Entra tenants or use the [admin consent workflow](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/configure-admin-consent-workflow).

### Least privilege / No standing access
- Users who have Microsoft Entra privileged built-in roles shouldn't regularly use those accounts for email and collaboration. Create a separate user account with no Microsoft Entra administrative roles for collaboration tasks.
- Review the Admin agent group and remove people who don't need access.
- Regularly review administrative role access in Microsoft Entra ID, and limit access to as few accounts as possible. For more information, see [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/azure/active-directory/roles/permissions-reference).
- Users who leave the company or change roles within the company should be removed from Partner Center access.
- If you have Microsoft Entra ID P2, use [Privileged Identity Management (PIM)](https://learn.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-configure) to enforce just-in-time (JIT) access. Use dual custody to review and approve access for Microsoft Entra administrator roles and Partner Center roles.
- For securing privileged roles, see [Securing privileged access overview](https://learn.microsoft.com/en-us/security/privileged-access-workstations/overview).
- Regularly review access to customer environments.
    - [Remove inactive Delegated Administration Privileges (DAP)](https://learn.microsoft.com/en-us/partner-center/security/dap-monitor-self-serve-removal).
    - [GDAP frequently asked questions](https://learn.microsoft.com/en-us/partner-center/customers/gdap-faq).
    - Ensure that GDAP relationships are utilizing roles with the [least privileges needed](https://learn.microsoft.com/en-us/partner-center/customers/gdap-least-privileged-roles-by-task).

### Identity isolation

- Avoid hosting your Partner Center instance in the same Microsoft Entra tenant that hosts your internal IT services, such as email and collaboration tools.
- Use separate, dedicated user accounts for Partner Center privileged users who have customer access.
- Avoid creating user accounts in customer Microsoft Entra tenants intended to be used by partners to administer the customer tenant and related apps and services.

## Devices best practices

- Only allow Partner Center and customer tenant access from registered, healthy workstations that have managed security baselines and are monitored for security risks.
- For Partner Center users with privileged access to customer environments, consider requiring dedicated workstations (virtual or physical) for those users to access customer environments. For more information, see [Securing privileged access](https://learn.microsoft.com/en-us/security/privileged-access-workstations/overview).

**Remove Delegated Administrative Privileges (DAP)**  
Migrate active delegated administrative privileges to granular delegated administrative privileges when not in use.

# Essential steps to confirm, contain, and secure a compromise

![[essential-steps-secure-compromise.png]]