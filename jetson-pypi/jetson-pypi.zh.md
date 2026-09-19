本镜像收录了面向 NVIDIA Jetson 平台的 Python wheel 包（如 torch、torchvision、bitsandbytes、flash-attn 等针对 Jetson 预编译的版本），按 JetPack/CUDA 版本划分通道。

### pip

#### 临时使用

```{ztmpl lang="bash" input="channel"}
pip install --index-url {{endpoint}}/{{channel}}/+simple some-package
```

注意，`+simple` 不能少。

#### 设为默认

```{ztmpl lang="bash" input="channel"}
pip config set global.index-url {{endpoint}}/{{channel}}/+simple
```

镜像中未收录的普通 PyPI 包会跳转到本站 PyPI 镜像，因此单独使用本镜像即可安装全部依赖。

如果您的站点没有提供该跳转，建议把 PyPI 镜像配为补充源：

```{ztmpl lang="bash" input="channel"}
pip config set global.index-url {{endpoint}}/{{channel}}/+simple
pip config set global.extra-index-url https://pypi.org/simple
```

### Astral uv

```{ztmpl lang="bash" input="channel"}
uv pip install --index-url {{endpoint}}/{{channel}}/+simple some-package
```
