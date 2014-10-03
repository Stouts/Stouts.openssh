Stouts.openssh
=============

[![Build Status](https://travis-ci.org/Stouts/Stouts.openssh.png)](https://travis-ci.org/Stouts/Stouts.openssh)

Ansible role which installs and setups OpenSSH client and server.


## Variables

The role variables and default values.

```yaml
openssh_enabled: yes          # Enable the role

openssh_client_install: yes   # Install OpenSSH Client
openssh_server_install: yes   # Install OpenSSH Server

openssh_server_vars: {}       # Use this variable for setup server
                              # Ex. openssh_server_vars:
                              #       PasswordAuthentication: no

openssh_client_vars: {}       # Use this variable for setup client
                              # Ex. openssh_client_vars:
                              #       ForwardAgent: yes

openssh_server_defaults:      # Default values. For setup server use 'openssh_server_vars' variable above
  Port: 22
  AllowUsers: []
  AllowGroups: []
  ListenAddress: [ "0.0.0.0", "::"]
  Protocol: 2
  HostKey:
  - /etc/ssh/ssh_host_rsa_key
  - /etc/ssh/ssh_host_dsa_key
  - /etc/ssh/ssh_host_ecdsa_key
  UserPrivilegeSeparation: yes
  KeyRegenerationInterval: 3600
  ServerKeyBits: 768
  SyslogFacility: AUTH
  LogLevel: INFO
  LoginGraceTime: 120
  PermitRootLogin: yes
  StrictModes: yes
  RSAAuthentication: yes
  PubkeyAuthentication: yes
  IgnoreRhost: yes
  RhostsRSAAuthentication: no
  HostbasedAuthentication: no
  IgnoreUserKnownHosts: yes
  PermitEmptyPasswords: no
  ChallengeResponseAuthentication: no
  PasswordAuthentication: yes
  KerberosAuthentication: no
  KerberosGetAFSToken: no
  KerberosOrLocalPasswd: yes
  KerberosTicketCleanup: yes
  GSSAPIAuthentication: no
  GSSAPICleanupCredentials: yes
  X11Forwarding: yes
  X11DisplayOffset: 10
  PrintMotd: no
  PrintLastLog: yes
  TCPKeepAlive: yes
  UseLogin: no
  MaxStartups: "10:30:60"
  Banner: /etc/issue.net
  AcceptEnv: LANG LC_*
  Subsystem: sftp /usr/lib/openssh/sftp-server
  UsePAM: yes
  UseDNS: no

# Client options
openssh_client_defaults:      # Default values. For setup client use 'openssh_client_vars' variable above
  Host: "*"
  ForwardAgent: no
  ForwardX11: no
  ForwardX11Trusted: yes
  RhostsRSAAuthentication: no
  RSAAuthentication: yes
  PasswordAuthentication: yes
  HostbasedAuthentication: no
  GSSAPIAuthentication: no
  GSSAPIDelegateCredentials: no
  GSSAPIKeyExchange: no
  GSSAPITrustDNS: no
  BatchMode: no
  CheckHostIP: yes
  AddressFamily: any
  ConnectTimeout: 0
  StrictHostKeyChecking: ask
  IdentityFile:
  - ~/.ssh/identity
  - ~/.ssh/id_rsa
  - ~/.ssh/id_dsa
  Port: 22
  Protocol: "2,1"
  EscapeChar: ~
  Tunnel: no
  TunnelDevice: "any:any"
  PermitLocalCommand: no
  VisualHostKey: no
  SendEnv:
  - LANG LC_*
  HashKnownHosts: yes
  GSSAPIAuthentication: yes
  GSSAPIDelegateCredentials: no
```
*_

## Usage

Add `Stouts.openssh` to your roles and set variables in your playbook file.

Example:

```yaml

- hosts: all

  roles:
    - Stouts.openssh

  vars:
    openssh_server_vars:
      PasswordAuthentication: no
      PermitRootLogin: no
      X11Forwarding: no

```

## License

Licensed under the MIT License. See the LICENSE file for details.

## Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Stouts/Stouts.openssh/issues)!
