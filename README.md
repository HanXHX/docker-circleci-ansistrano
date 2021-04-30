Ansistrano Docker image for CircleCI
====================================

![Docker Image Version (latest by date)](https://img.shields.io/docker/v/hanxhx/circleci-ansistrano)


Exemple CircleCI config:

```yaml
version: 2.1
workflows:
  version: 2
  deploy_only:
    jobs:
      - deploy_ansistrano

jobs:
  deploy_ansistrano:
    docker:
      - image: hanxhx/circleci-ansistrano
        auth:
          username: $DOCKER_HUB_LOGIN
          password: $DOCKER_HUB_PASS
        environment:
          ANSIBLE_HOST_KEY_CHECKING: no
          ANSIBLE_FORCE_COLOR: true
    steps:
      - checkout
      - add_ssh_keys:
          fingerprints:
            - "00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00"
      - run: ansible-playbook -i deploy/inventory deploy/deploy.yml
```
