---
title: Enforcing policies for security settings in your enterprise
intro: 'You can enforce policies to manage security settings in your enterprise''s organizations, or allow policies to be set in each organization.'
permissions: Enterprise owners can enforce policies for security settings in an enterprise.
miniTocMaxHeadingLevel: 3
redirect_from:
  - /articles/enforcing-security-settings-for-organizations-in-your-business-account
  - /articles/enforcing-security-settings-for-organizations-in-your-enterprise-account
  - /articles/enforcing-security-settings-in-your-enterprise-account
  - /github/articles/managing-allowed-ip-addresses-for-organizations-in-your-enterprise-account
  - /github/setting-up-and-managing-your-enterprise-account/enforcing-security-settings-in-your-enterprise-account
  - /github/setting-up-and-managing-your-enterprise/enforcing-security-settings-in-your-enterprise-account
  - /github/setting-up-and-managing-your-enterprise/setting-policies-for-organizations-in-your-enterprise-account/enforcing-security-settings-in-your-enterprise-account
versions:
  ghec: '*'
  ghes: '*'
  ghae: '*'
type: how_to
topics:
  - Enterprise
  - Policies
  - Security
shortTitle: Policies for security settings
---

## About policies for security settings in your enterprise

You can enforce policies to control the security settings for organizations owned by your enterprise on {% data variables.product.product_name %}. By default, organization owners can manage security settings. For more information, see "[Keeping your organization secure](/organizations/keeping-your-organization-secure)."

{% ifversion ghec or ghes %}

## Requiring two-factor authentication for organizations in your enterprise

Enterprise owners can require that organization members, billing managers, and outside collaborators in all organizations owned by an enterprise use two-factor authentication to secure their personal accounts.

Before you can require 2FA for all organizations owned by your enterprise, you must enable two-factor authentication for your own account. ????????????[2 ???????????? (2FA) ?????????????????????????????????](/articles/securing-your-account-with-two-factor-authentication-2fa/)?????????????????????????????????

{% warning %}

**??????:**

- When you require two-factor authentication for your enterprise, members, outside collaborators, and billing managers (including bot accounts) in all organizations owned by your enterprise who do not use 2FA will be removed from the organization and lose access to its repositories. Organization ??????????????????????????????????????????????????????????????????????????????????????? Organization ??????????????????????????? 3 ?????????????????????????????????????????????????????????????????????????????? 2 ??????????????????????????????????????????????????????????????????????????????????????????????????????????????? ????????????????????????????????????[Organization ???????????????????????????????????????](/articles/reinstating-a-former-member-of-your-organization)?????????????????????????????????
- Any organization owner, member, billing manager, or outside collaborator in any of the organizations owned by your enterprise who disables 2FA for their personal account after you've enabled required two-factor authentication will automatically be removed from the organization.
- If you're the sole owner of a enterprise that requires two-factor authentication, you won't be able to disable 2FA for your personal account without disabling required two-factor authentication for the enterprise.

{% endwarning %}

2 ????????????????????????????????????????????????Organization ???????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? 2 ?????????????????????????????????????????????????????????????????? Organization ??????????????????????????????????????????????????????????????????????????? 2 ?????????????????????????????????????????????????????? Organization ??? [People] ????????????????????????????????? ????????????[Organization ?????????????????? 2 ???????????????????????????????????????????????????](/articles/viewing-whether-users-in-your-organization-have-2fa-enabled)?????????????????????????????????

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.security-tab %}
4. [Two-factor authentication] ????????????????????????????????????????????????????????? {% data reusables.enterprise-accounts.view-current-policy-config-orgs %}
5. [Two-factor authentication] ??????[**Require two-factor authentication for all organizations in your business**] ???????????????[**Save**] ??????????????????????????? ![2 ??????????????????????????????????????????????????????](/assets/images/help/business-accounts/require-2fa-checkbox.png)
6. If prompted, read the information about members and outside collaborators who will be removed from the organizations owned by your enterprise. To confirm the change, type your enterprise's name, then click **Remove members & require two-factor authentication**. ![2 ????????????????????????????????????](/assets/images/help/business-accounts/confirm-require-2fa.png)
7. Optionally, if any members or outside collaborators are removed from the organizations owned by your enterprise, we recommend sending them an invitation to reinstate their former privileges and access to your organization. ??????????????????????????????????????????????????????????????????????????????????????????????????? 2 ??????????????????????????????????????????????????????

{% endif %}

{% ifversion ghec or ghae %}

## Managing allowed IP addresses for organizations in your enterprise

{% ifversion ghae %}

You can restrict network traffic to your enterprise on {% data variables.product.product_name %}. ????????????????????????????????????[Enterprise ?????????????????????????????????????????????????????????](/admin/configuration/configuring-your-enterprise/restricting-network-traffic-to-your-enterprise)?????????????????????????????????

{% elsif ghec %}

Enterprise owners can restrict access to private assets owned by organizations in an enterprise by configuring an allow list for specific IP addresses. {% data reusables.identity-and-permissions.ip-allow-lists-example-and-restrictions %}

{% data reusables.identity-and-permissions.ip-allow-lists-cidr-notation %}

{% data reusables.identity-and-permissions.ip-allow-lists-enable %} {% data reusables.identity-and-permissions.ip-allow-lists-enterprise %}

?????? IP ??????????????????Organization ????????????????????????????????????????????? ????????????[ Organization ?????????????????? IP ???????????????????????????](/organizations/keeping-your-organization-secure/managing-allowed-ip-addresses-for-your-organization)?????????????????????????????????

### ?????? IP ???????????????????????????

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.security-tab %}
{% data reusables.identity-and-permissions.ip-allow-lists-add-ip %}
{% data reusables.identity-and-permissions.ip-allow-lists-add-description %}
{% data reusables.identity-and-permissions.ip-allow-lists-add-entry %}

### {% data variables.product.prodname_github_apps %}??????????????????????????????

{% data reusables.identity-and-permissions.ip-allow-lists-githubapps-enterprise %}

### ?????? IP ??????????????????????????????

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.security-tab %}
3. [IP allow list] ?????????**Enable IP allow list**???????????????????????? ![IP ???????????????????????????????????????????????????](/assets/images/help/security/enable-ip-allowlist-enterprise-checkbox.png)
4. [**Save**] ???????????????????????????

### ?????? IP ???????????????????????????

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.security-tab %}
{% data reusables.identity-and-permissions.ip-allow-lists-edit-entry %}
{% data reusables.identity-and-permissions.ip-allow-lists-edit-ip %}
{% data reusables.identity-and-permissions.ip-allow-lists-edit-description %}
8. [**Update**] ???????????????????????????

### ?????? IP ???????????????????????????

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.security-tab %}
{% data reusables.identity-and-permissions.ip-allow-lists-delete-entry %}
{% data reusables.identity-and-permissions.ip-allow-lists-confirm-deletion %}

### IP?????????????????? {% data variables.product.prodname_actions %} ???????????????

{% data reusables.actions.ip-allow-list-self-hosted-runners %}

{% endif %}

{% endif %}

## Managing SSH certificate authorities for your enterprise

You can use a SSH certificate authorities (CA) to allow members of any organization owned by your enterprise to access that organization's repositories using SSH certificates you provide. {% data reusables.organizations.can-require-ssh-cert %}????????????????????????????????????[SSS ?????????????????????](/organizations/managing-git-access-to-your-organizations-repositories/about-ssh-certificate-authorities)?????????????????????????????????

{% data reusables.organizations.add-extension-to-cert %}

### SSH ????????????????????????

If you require SSH certificates for your enterprise, enterprise members should use a special URL for Git operations over SSH. ????????????????????????????????????[SSH ?????????????????????](/organizations/managing-git-access-to-your-organizations-repositories/about-ssh-certificate-authorities#about-ssh-urls-with-ssh-certificates)?????????????????????????????????

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.security-tab %}
{% data reusables.organizations.new-ssh-ca %}
{% data reusables.organizations.require-ssh-cert %}

### SSH????????????????????????

CA???????????????????????????????????????????????????????????? ??????CA????????????????????????????????????????????????CA?????????????????????????????????????????????????????????

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.security-tab %}
{% data reusables.organizations.delete-ssh-ca %}

{% ifversion ghec or ghae %}
## ???????????????

- "[About identity and access management for your enterprise](/admin/authentication/managing-identity-and-access-for-your-enterprise/about-identity-and-access-management-for-your-enterprise)"{% ifversion ghec %}
- "[Accessing compliance reports for your enterprise](/admin/overview/accessing-compliance-reports-for-your-enterprise)"{% endif %}
{% endif %}
