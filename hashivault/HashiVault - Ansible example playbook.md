---
- name: Get krabby patty secret formula from hashivault
  hosts: 127.0.0.1
  vars:
    vault_url: http://IPhere:8200
    vault_token: password

  tasks:
  - name: Read latest version of kv2 secret from vault via remote host with userpass auth
    community.hashi_vault.vault_kv2_get:
      url: http://192.168.2.130:8200
      engine_mount_point: secret
      path: krabby-patty
      auth_method: userpass
      username: crabs
      password: password
    register: response
    
    
  - name: Display results  
    ansible.builtin.debug:
      msg:
        - "Secret: {{ response.secret }}"
        - "Data: {{ response.data }} (contains secret data & metadata in kv2)"
        - "Metadata: {{ response.metadata }}"
        - "Full response: {{ response.raw }}"
        - "Value of key 'formula' in the secret: {{ response.secret.formula }}"
