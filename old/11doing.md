## shell gitlab runner

* 安装 runner
* 注册 runner
* 执行一个前端cicd流水线
* 与docker的不同点

shell 执行器的特点
* 使用系统服务，更快速
* 无法使用docker镜像
* 工作目录区别

```bash
# Replace ${arch} with any of the supported architectures, e.g. amd64, arm, arm64
# A full list of architectures can be found here https://gitlab-runner-downloads.s3.amazonaws.com/latest/index.html
curl -LJO "https://gitlab-runner-downloads.s3.amazonaws.com/latest/deb/gitlab-runner_${arch}.deb"


# Replace ${arch} with any of the supported architectures, e.g. amd64, arm, arm64
# A full list of architectures can be found here https://gitlab-runner-downloads.s3.amazonaws.com/latest/index.html
curl -LJO "https://gitlab-runner-downloads.s3.amazonaws.com/latest/rpm/gitlab-runner_amd64.rpm"


dpkg -i gitlab-runner_<arch>.deb

rpm -i gitlab-runner_<arch>.rpm

sudo gitlab-runner register \
  --non-interactive \
  --url "http://gitlab.mczaiyun.top/" \
  --registration-token "_2mLzy3dYL3csrrLv_zU" \
  --executor "shell" \
  --docker-image alpine:latest \
  --description "shell-runner" \
  --tag-list "shell,0704" \
  --run-untagged="true" \
  --locked="false" \
  --access-level="not_protected"

```

```md
/etc/gitlab-runner/ on *nix systems when GitLab Runner is executed as root (this is also the path for service configuration)
~/.gitlab-runner/ on *nix systems when GitLab Runner is executed as non-root
```

https://docs.gitlab.com/runner/executors/shell.html

<working-directory>/builds/<short-token>/<concurrent-id>/<namespace>/<project-name>


| Executor                                          | SSH  | Shell   | VirtualBox | Parallels | Docker | Kubernetes | Custom         |
|:--------------------------------------------------|:----:|:-------:|:----------:|:---------:|:------:|:----------:|---------------:|
| Clean build environment for every build           | ✗    | ✗       | ✓          | ✓         | ✓      | ✓          |conditional (4) |
| Reuse previous clone if it exists                 | ✓    | ✓       | ✗          | ✗         | ✓      | ✗          |conditional (4) |
| Runner file system access protected (5)           | ✓    | ✗       | ✓          | ✓         | ✓      | ✓           |conditional    |
| Migrate runner machine                            | ✗    | ✗       | partial    | partial   | ✓      | ✓          |✓               |
| Zero-configuration support for concurrent builds  | ✗    | ✗ (1)   | ✓          | ✓         | ✓      | ✓          |conditional (4) |
| Complicated build environments                    | ✗    | ✗ (2)   | ✓ (3)      | ✓ (3)     | ✓      | ✓          |✓               |
| Debugging build problems                          | easy | easy    | hard       | hard      | medium | medium     |medium          |



| Executor                                     | SSH  | Shell   |VirtualBox  | Parallels | Docker | Kubernetes | Custom |
|:---------------------------------------------|:----:|:-------:|:----------:|:---------:|:------:|:----------:|:------:|
| Secure Variables                             | ✓    | ✓       | ✓          | ✓         | ✓      | ✓          | ✓      |
| GitLab Runner Exec command                   | ✗    | ✓       | ✗          | ✗         | ✓      | ✓          | ✓      |
| `gitlab-ci.yml`: image                       | ✗    | ✗       | ✗          | ✗         | ✓      | ✓          | ✓ (via [`$CUSTOM_ENV_CI_JOB_IMAGE`](custom.md#stages)      |
| `gitlab-ci.yml`: services                    | ✗    | ✗       | ✗          | ✗         | ✓      | ✓          | ✓      |
| `gitlab-ci.yml`: cache                       | ✓    | ✓       | ✓          | ✓         | ✓      | ✓          | ✓      |
| `gitlab-ci.yml`: artifacts                   | ✓    | ✓       | ✓          | ✓         | ✓      | ✓          | ✓      |
| Passing artifacts between stages             | ✓    | ✓       | ✓          | ✓         | ✓      | ✓          | ✓      |
| Use GitLab Container Registry private images | n/a  | n/a     | n/a        | n/a       | ✓      | ✓          | n/a    |
| Interactive Web terminal                     | ✗    | ✓ (UNIX)| ✗          | ✗         | ✓      | ✓ (1)      | ✗      |

