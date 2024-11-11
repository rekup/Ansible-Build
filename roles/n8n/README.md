# N8N role

Deploy N8N container.

## Usage

Configure the role.

```yml
# https://hub.docker.com/r/n8nio/n8n/tags
n8n_image: n8nio/n8n:1.67.1
n8n_build_image: true # default: false
n8n_hostname: n8n01
n8n_config_map:
  - name: prod
    webhook_url: https://n8n.example.com/
  - name: int
    webhook_url: https://n8n-int.example.com/
n8n_description: Workflow Automation # default: N8N
n8n_state: stopped # default: started
n8n_data_dir: /usr/share/n8n # default: "/usr/share/{{ n8n_hostname }}"
n8n_timezone: Europe/Paris # default: Europe/Zurich
n8n_db_type: # default: postgresdb
n8n_postgresdb_host: postgres01
n8n_postgresdb_port: # default: "5432"
n8n_postgresdb_database: workflow # default: n8n
n8n_postgresdb_schema: n8n # default: public
n8n_postgresdb_user: workflow # default: n8n
n8n_postgresdb_password: # default: "{{ vault_n8n_postgresdb_password }}"
n8n_secure_cookie: "false" # default: "true"
```

And include it in your playbook.

```yml
- hosts: n8n
  roles:
  - role: n8n
```