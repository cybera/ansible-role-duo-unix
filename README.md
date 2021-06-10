Ansible Role: Duo Unix (pam_duo)
=========

Ansible role to install [Duo Unix (pam_duo)](https://duo.com/docs/duounix) on Linux servers

Requirements
------------

The role does not require anyting to run on RHEL and its derivatives.

Role Variables
--------------

Available variables are listed below, along with default values (see ```defaults/main.yml```):

``` yaml
duo_ikey: "1234567890"
duo_skey: "1234567890"
duo_host: "duo.example.com"
duo_failmode: "safe"
duo_pushinfo: "yes"
duo_autopush: "yes"
duo_prompts: "1"
duo_default_groups: "users,wheel,*admin"
duo_exclude_groups: "!exclude"
ad_domain: "domain.com"
password_authentication: "yes"
```

```duo_ikey:``` **(Required)** Integration key from Duo Console.

```duo_skey``` **(Required)** Secret key from Duo Console.

```duo_host``` **(Required)** Duo API hostname.

```duo_failmode``` **(Optional)** On service or configuration errors that prevent Duo authentication, fail "**safe**" (**allow access**) or "**secure**" (**deny access**). The default is "**safe**".

```duo_pushinfo``` **(Optional)** Include information such as the command to be executed in the Duo Push message. Either "**yes**" or "**no**". The default is "**no**".

```duo_autopush``` **(Optional)** Either "**yes**" or "**no**". Default is "**no**". If "**yes**", Duo Unix will automatically send a push login request to the user's phone, falling back on a phone call if push is unavailable. **Note** that this effectively disables passcode authentication. If "**no**", the user will be prompted to choose an authentication method.

```duo_prompts``` **(Optional)** If a user fails to authenticate with a second factor, Duo Unix will prompt the user to authenticate again. This option sets the maximum number of prompts that Duo Unix will display before denying access. Must be **1**, **2**, or **3**. Default is **3**.

```duo_default_groups``` **(Optional)** Default system groups to include.

```duo_exclude_groups``` **(Optional)** System groups to exclude.

```ad_domain``` **(Optional)** Active Directory group (**Fully-Qualified**) to include.

```password_authentication``` **(Optional)** Password Authentication for SSH Daemon. **Yes** to allow; **No** to disable.

Role variables can be stored with the ```hosts.yaml``` file, or in the main variables file.

Dependencies
------------

None.

Example Playbook
----------------

``` yaml
    - hosts: servers
      roles:
         - role: mikepruett3.duo-unix
           vars:
            duo_ikey: "1234567890"
            duo_skey: "1234567890"
            duo_host: "duo.example.com"
            duo_failmode: "safe"
            duo_pushinfo: "yes"
            duo_autopush: "yes"
            duo_prompts: "1"
            duo_default_groups: "users,wheel,*admin"
            duo_exclude_groups: "!exclude"
            ad_domain: "domain.com"
            password_authentication: "yes"
```

License
-------

MIT

Author Information
------------------

Role created by [mikepruett3](https://github.com/mikepruett3) on [Github.com](https://github.com/mikepruett3/ansible-role-duo-unix)
