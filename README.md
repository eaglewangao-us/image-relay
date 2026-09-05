# image-relay

把 Docker Hub 的公开镜像搬运到本账号的 GHCR 命名空间。

国内机器直连 Docker Hub 或社区代理都很慢（实测 0.3～1 MB/s，且极不稳定），
而 ghcr.io 从国内拉能到 11～24 MB/s。GitHub Actions 的 runner 在境外，
拉 Docker Hub 满速，`skopeo copy` 逐层流式转发，不解压、不落完整副本。

用法：Actions → `relay-image` → Run workflow，填源镜像和目标 tag。
