pcopfer.postfix
=========

A role to manage Postfix.

Role Variables
--------------

- ``postfix_hostname: "{{ ansible_hostname }}"``
- ``postfix_domain: "{{ ansible_domain }}"`` 
- ``postfix_fqdn: "{{ ansible_fqdn }}"``
- ``postfix_myhostname: "{{ postfix_fqdn }}"``
- ``postfix_smtp: true`` Enable SMTP, recive Mail on TCP 25
- ``ufw_smtp_public: "{{ postfix_smtp }}"`` Open TCP 25 in Firewall
- ``postfix_submission: false`` Disable submission, recive Mails from Clients, TCP 587
- ``ufw_submission_public: "{{ postfix_submission }}"`` Open TCP 587 in Firewall
- ``postfix_smtps: false`` Disable smtps, recive Mail on TCP 465 (deprecated) 
- ``ufw_smtps: "{{ postfix_smtps }}"`` Open TCP 465 in Firewall
- ``postfix_smtpd_banner: "$myhostname ESMTP $mail_name"`` Set Banner on Connect on smtp
- ``postfix_delay_warning_time: "4h"``
- ``postfix_alias_maps: "hash:/etc/aliases"`` Alias Map for postfix_domain
- ``postfix_relayhost : ""`` Add Postfix relayhost, different Server which sends the Mails to the internet
- ``postfix_ssl: true`` Postfix use TLS
- ``postfix_ssl_high: true`` Enable strong cipher
- ``postfix_cert_path: "/etc/ssl/letsencrypt/certs/{{ postfix_fqdn }}"`` Path to the certs
- ``postfix_rmilter: false`` Add Rmilter config for rspamd
- ``postfix_virtual_mailbox_domains: "{{ ansible_domain }}"`` Virtual Domains
- ``postfix_mynetworks: "127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128"`` my_networks IP Ranges for send Mail without authentication
- ``postfix_debconf_selections: ...`` For Debian etc. only
- ``postfix_srs: false`` Disable Postfix Sender rewrite scheme (postsrsd)
- ``postsrsd_domains: "{{ postfix_domain }}"`` 
- ``postsrsd_exclude_domains: ".{{ postfix_domain }}"``
- ``dovecot_lmtp: false`` Disable dovecot_lmtp Dovecot Local Mail transport

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: pcopfer.postfix

License
-------

BSD

Author Information
------------------

pcopfer <christian-platz at pcopfer.de>
