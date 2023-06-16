## Minimal Ansible Execution Environment

This is meant to offer a consistently available image on Github Container Registry
with the minimal requirements for an EE.

```
docker pull ghcr.io/alancoding/zen-ee:latest
```

Go pull it an check.

```
docker run --rm --tty --interactive ghcr.io/alancoding/zen-ee /bin/bash
```

And check `ansible --version` and `ansible-runner --version`.

You can also see it in the web interface here:

https://github.com/alancoding/bad-execution-environments/pkgs/container/zen-ee

The intent is to use the smallest possible configuration from ansible-builder v3.
That task, by itself, is fairly trivial, but to use an image in AWX
you usually need to publish it publicly, which adds notably to your problems
if you're busy trying to hack stuff.

### History

For Ansible Automation Platform, there is an ee-minimal which is supported.
There used to be an upstream analog, which was the runner image itself.

https://quay.io/repository/ansible/ansible-runner

This image, along with many others in the pipeline, are no longer up-to-date,
because of structural changes in how ansible-builder works.

In addition to ansible-runner, there has always been the awx-ee image,
which is still maintained and used by default by AWX today.

https://quay.io/repository/ansible/awx-ee

So to recap, there used to be 2 public images that you could start using in AWX.
We still have awx-ee, but we lost rolling builds of a _minimal_ image.
That is what this attempts to provide.

### Image Refreshes

See the github actions - this should be configured to push a new build every Friday.
If it fails, it should file an issue which will fire a github notification.
The aim is to avoid any scenario where this falls _months_ out of date.

File an issue and `@` me if you want to get those notifications and help maintain.
