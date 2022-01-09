# Ansible Banner Role
This Ansible role manages common Linux banner files. Currently, the following banners are supported:

| Banner                                           | Description                                                                                                                                                                                                                                    |
|--------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `motd` - message of the day                        | The motd banner is displayed after a successful login but just before it executes the login shell.                                                                                                                                             |
| `issue` - prelogin message and identification file | The issue banner is a text file which contains a message or system  identification to be printed before the login prompt. It may contain various `@char`  and  `\char`  sequences,  if supported by the getty-type program employed on the system. |

# Role Variables
The content of the banners is controlled by variables. The variables have no content by default and must be overwritten
by the user. The following variables are available:
```yaml
---
# default variables
banner_issue:
banner_motd:
```

Example Playbook
----------------
```yaml
---
- hosts: all
  tasks:
    - name: Update banners
      ansible.builtin.include_role:
        name: wallernetwork.banner
      vars:
        banner_issue: |
          \e{bold}
          __          __   _ _                      _                      _
          \\ \\        / /  | | |                    | |                    | |
           \\ \\  /\\  / /_ _| | | ___ _ __ _ __   ___| |___      _____  _ __| | __
            \\ \\/  \\/ / _` | | |/ _ \\ '__| '_ \\ / _ \\ __\\ \\ /\\ / / _ \\| '__| |/ /
             \\  /\\  / (_| | | |  __/ |  | | | |  __/ |_ \\ V  V / (_) | |  |   <
              \\/  \\/ \\__,_|_|_|\\___|_|  |_| |_|\\___|\\__(_)_/\\_/ \\___/|_|  |_|\\_\\
          \e{reset}
            OS:            \e{bold}\S{PRETTY_NAME}, \r\e{reset}
            Date:          \e{bold}\d, \t\e{reset}

            Hostname:      \e{bold}\n\e{reset}
            IPv4:          \e{bold}\4\e{reset}
            IPv6:          \e{bold}\6\e{reset}

        banner_motd: |

          __          __   _ _                      _                      _
          \ \        / /  | | |                    | |                    | |
           \ \  /\  / /_ _| | | ___ _ __ _ __   ___| |___      _____  _ __| | __
            \ \/  \/ / _` | | |/ _ \ '__| '_ \ / _ \ __\ \ /\ / / _ \| '__| |/ /
             \  /\  / (_| | | |  __/ |  | | | |  __/ |_ \ V  V / (_) | |  |   <
              \/  \/ \__,_|_|_|\___|_|  |_| |_|\___|\__(_)_/\_/ \___/|_|  |_|\_\

```
