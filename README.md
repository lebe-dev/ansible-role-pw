# Ansible role for pw

Current implementation support only stateless mode:

```shell
docker run -d --rm --name pw -p PORT:8080 tinyops/pw:1.0.0
```

## Variables

```yaml
pw_installation_type: docker-compose

pw_instances:
  - type: docker-compose
    path: /opt/pw
    image: 'tinyops/pw:1.1.0'
    port_mapping: '8080:8080'
    redis_max_memory: '128mb'

    container_name: pw

    config: |
      port: 8080

      log-level: debug

      message-max-length: 100
      encrypted-message-max-length: 500

      locale-id: 'en'

      redis-url: 'redis://cache:6379'

## Playbook

```yaml
- name: Deploy pw
  hosts: someserver
  roles:
  - ansible-role-pw
```

## Deploy

```yaml
ansible-playbook -b -i your-inventory playbooks/someserver.yml
```
