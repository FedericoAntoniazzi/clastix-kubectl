
<p align="center">
  <img src="assets/logo/kubexarm.png" />
</p>

<p align="left">
  <img alt="GitHub tag (latest SemVer)" src="https://img.shields.io/github/v/tag/clastix/kubectl?sort=semver">
  <img src="https://img.shields.io/github/license/clastix/kubectl"/>
</p>

---

# Kubectl

Your [k8s](https://kubernetes.io) cluster swiss army knife, running in a container.

## Why should you use this?

Because this kubectl image is :

- lightweight
- secure
- multi-arch

New stable versions will be built and pushed automatically by *GitHub action* [workflow](https://github.com/clastix/kubectl/blob/master/.github/workflows/docker-ci.yml).

### Supported tags

| kubectl | amd64 | arm64 | armv7 |
| :---: | :---: | :---: | :---: |
|v1.32.0| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.31.0| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.30.1| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.29.1| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.28.2| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.27.2| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.26.4| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.25.4| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.24.1| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.23.1| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.22.2| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.21.5| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.20.11| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.19.15| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.18.20| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.17.17| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|v1.16.15| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

Keep watching our [docker.io](https://hub.docker.com/r/clastix/kubectl) and [quay.io](https://quay.io/repository/clastix/kubectl) repositories for the latest updates!

---

## Quickstart

### Prerequisites

Make sure you have a containerization software (e.g. _[Docker](https://www.docker.com/)_ ) installed on your device :

```bash
$ docker version

Client: Docker Engine - Community
 Cloud integration: 1.0.14
 Version:           20.10.6
 API version:       1.41
 Go version:        go1.13.15
 Git commit:        370c289
 Built:             Fri Apr  9 22:46:45 2021
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true
[...]
```

### Take our image

Just pull the desired version from [docker.io](https://hub.docker.com/r/clastix/kubectl) or [quay.io](https://quay.io/repository/clastix/kubectl) :

```bash
$ docker pull clastix/kubectl:<desired_version>
```

OR

### Build your image

running :

```bash
$ docker build . -t foo.io/bar/kubectl:<desired_version> --build-arg KUBECTL_VERSION=<desired_version> --build-arg TARGETARCH=<target_architecture>
```

or using **make** utility :
```bash
$ make docker-build
```
**N.B.** if you like, you can choose desired kubectl version and target architecture as follow :

```bash
$ export KUBECTL_VERSION=<desired_version>
$ export TARGETARCH=<target_architecture>
```
otherwise, Makefile will automatically retrieve its default values.

### Launch a container

```bash
$ docker run --name kubectl clastix/kubectl:v1.22.2 version --client

Client Version: version.Info{Major:"1", Minor:"22", GitVersion:"v1.22.2", GitCommit:"8b5a19147530eaac9476b0ab82980b4088bbc1b2", GitTreeState:"clean", BuildDate:"2021-09-15T21:38:50Z", GoVersion:"go1.16.8", Compiler:"gc", Platform:"linux/amd64"}
```

you can also use your own _kubeconfig_

```bash
$ docker run --name kubectl -v ~/.kube/config:/home/nonroot/.kube/config clastix/kubectl:<desired_version> get nodes

NAME              STATUS   ROLES                  AGE   VERSION
controlplane-00   Ready    control-plane,master   13d   v1.21.5
controlplane-01   Ready    control-plane,master   13d   v1.21.5
controlplane-02   Ready    control-plane,master   13d   v1.21.5
worker-00         Ready    <none>                 13d   v1.21.5
worker-01         Ready    <none>                 13d   v1.21.5
worker-02         Ready    <none>                 13d   v1.21.5
```

### Removal
To clean up, just :

1. Remove your kubectl container :

    ```bash
    $ docker rm kubectl
    ```

3. Remove your kubectl image :

    ```bash
    $ docker rmi -f clastix/kubectl:<desired_version>
    ```

## FAQ
- Q. Does it work on my architecture?

  A. We successfully tested it on amd and arm architectures; have a look at "[Supported tags'](https://github.com/clastix/kubectl#supported-tags)" section for more information.

- Q. Can I contribute?

  A. Absolutely!

## License

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at :

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
