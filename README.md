# Ansible role for pw

Current implementation support only stateless mode:

```shell
docker run -d --rm --name pw -p PORT:8080 tinyops/pw:1.0.0
```

## Variables

```yaml
pw_installation_type: docker

pw_container_name: pw
pw_image: 'tinyops/pw:1.0.0'
pw_port_mapping: '8080:8080'
```

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

## Roadmap

1. Installation with docker-compose.yml
