# Ansible role gitlab runner

An ansible role for installing and registering a gitlab continious integration runner

## Requirements

A gitlab server to connect to, it's URL and the `ci runner token`

## Role Variables

The following variables must be passed to the role:

Variable | Description | Example
--- | --- | ---
`gitlab_runner_registration_token`| [The gitlab instance CI registration token][1]  | `gjgfiijvcxv`
`gitlab_runner_url`| The url of the gitlab instance to connect to | `https://gitlab.my.tld`
`gitlab_runner_name`| Short name for the runner | `docker runner #1`
`gitlab_runner_executor`| [Executor to use for the runner][2], `docker`, `shell` etc | `docker`

Also note that when registering docker builders, a default image of `node:6.9` is used, but this can be changed via the variable `gitlab_runner_docker_image`

## Example Playbook

```yml
- hosts: servers
  roles:
    - { role: nover.gitlab-runner, gitlab_runner_url: 'https://gitlab.my.tld' ,gitlab_runner_name: 'My runner', gitlab_runner_registration_token: 'asdfwerqe', gitlab_runner_executor: 'docker' }
```

If you wish to register multiple runners, simply include the role multiple times and use different names and decriptions.

## License

The unlicense



[1]: https://docs.gitlab.com/ce/ci/runners/README.html
[2]: https://gitlab.com/gitlab-org/gitlab-ci-multi-runner/blob/master/docs/executors/README.md
