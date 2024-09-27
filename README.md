# Open WebUI (原 Ollama WebUI) 👋

![GitHub stars](https://img.shields.io/github/stars/open-webui/open-webui?style=social)
![GitHub forks](https://img.shields.io/github/forks/open-webui/open-webui?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/open-webui/open-webui?style=social)
![GitHub repo size](https://img.shields.io/github/repo-size/open-webui/open-webui)
![GitHub language count](https://img.shields.io/github/languages/count/open-webui/open-webui)
![GitHub top language](https://img.shields.io/github/languages/top/open-webui/open-webui)
![GitHub last commit](https://img.shields.io/github/last-commit/open-webui/open-webui?color=red)
![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Follama-webui%2Follama-wbui&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)
[![Discord](https://img.shields.io/badge/Discord-Open_WebUI-blue?logo=discord&logoColor=white)](https://discord.gg/5rJgQTnV4s)
[![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/tjbck)

Open WebUI 是一个[可扩展](https://github.com/open-webui/pipelines)、功能丰富且用户友好的自托管 WebUI，设计用于完全离线运行。它支持多种 LLM 运行器，包括 Ollama 和兼容 OpenAI 的 API。有关更多信息，请查看我们的 [Open WebUI 文档](https://docs.openwebui.com/)。

![Open WebUI 演示](./demo.gif)

## Open WebUI 主要功能 ⭐

- 🚀 **无缝安装**：通过 Docker 或 Kubernetes（kubectl、kustomize 或 helm）轻松安装，支持 `:ollama` 和 `:cuda` 标记的镜像。

- 🤝 **Ollama/OpenAI API 集成**：轻松集成兼容 OpenAI 的 API，支持与 Ollama 模型一起使用的多样化对话。可自定义 OpenAI API URL，以连接 **LMStudio、GroqCloud、Mistral、OpenRouter 等**。

- 🧩 **流水线，Open WebUI 插件支持**：通过 [Pipelines 插件框架](https://github.com/open-webui/pipelines)，将自定义逻辑和 Python 库无缝集成到 Open WebUI 中。启动 Pipelines 实例，将 OpenAI URL 设置为 Pipelines URL，探索无限可能。包括 **函数调用**、用户 **访问控制**、与 Langfuse 结合的**使用监控**、**LibreTranslate 的实时翻译**以支持多语言、**有害消息过滤**等功能的[示例](https://github.com/open-webui/pipelines/tree/main/examples)。

- 📱 **响应式设计**：在台式电脑、笔记本电脑和移动设备上享受无缝体验。

- 📱 **移动端渐进式 Web 应用 (PWA)**：在移动设备上提供类似原生应用的体验，支持离线访问并提供流畅的用户界面。

- ✒️🔢 **支持完整 Markdown 和 LaTeX**：使用全面的 Markdown 和 LaTeX 功能提升 LLM 互动体验。

- 🎤📹 **免提语音/视频通话**：体验集成语音和视频通话的无缝通信，提供更具互动性的聊天环境。

- 🛠️ **模型构建器**：通过 Web UI 轻松创建 Ollama 模型。通过 [Open WebUI 社区](https://openwebui.com/) 集成，轻松创建并添加自定义角色/代理、定制聊天元素及导入模型。

- 🐍 **原生 Python 函数调用工具**：在工具工作区中为 LLM 提供内置代码编辑器支持。通过添加纯 Python 函数，实现与 LLM 的无缝集成。

- 📚 **本地 RAG 集成**：借助开创性的检索增强生成 (RAG) 支持，深入探索聊天互动的未来。该功能将文档互动无缝集成到聊天体验中。您可以将文档直接加载到聊天中，或将文件添加到文档库中，使用 `#` 命令在查询前轻松访问它们。

- 🔍 **用于 RAG 的网页搜索**：使用 `SearXNG`、`Google PSE`、`Brave Search`、`serpstack`、`serper`、`Serply`、`DuckDuckGo`、`TavilySearch` 和 `SearchApi` 等提供商进行网页搜索，并将结果直接注入到您的聊天体验中。

- 🌐 **网页浏览功能**：使用 `#` 命令后接 URL，将网页内容无缝集成到聊天体验中，增强互动的丰富性和深度。

- 🎨 **图片生成集成**：通过 AUTOMATIC1111 API 或 ComfyUI（本地），以及 OpenAI 的 DALL-E（外部）轻松集成图片生成功能，使聊天体验更加生动。

- ⚙️ **多模型对话**：轻松同时与多个模型互动，利用它们各自的优势获得最佳响应。通过并行使用多样化模型，提升体验。

- 🔐 **基于角色的访问控制 (RBAC)**：确保访问安全；只有授权人员才能访问您的 Ollama，且管理员保留创建/拉取模型的专有权利。

- 🌐🌍 **多语言支持**：通过国际化 (i18n) 支持，以您偏好的语言体验 Open WebUI。我们正在积极寻找贡献者，帮助扩展我们支持的语言！

- 🌟 **持续更新**：我们致力于通过定期更新、修复和新功能不断改进 Open WebUI。

想了解更多关于 Open WebUI 的功能？请查看我们的 [Open WebUI 文档](https://docs.openwebui.com/features) 获取全面概述！

## 🔗 也别忘了查看 Open WebUI 社区！

不要忘记探索我们的姐妹项目 [Open WebUI 社区](https://openwebui.com/)，您可以在这里发现、下载和探索定制的模型文件。Open WebUI 社区为增强您与 Open WebUI 的聊天互动提供了广泛的可能性！🚀

## 如何安装 🚀

### 通过 Python pip 安装 🐍

Open WebUI 可以通过 pip（Python 包管理器）安装。安装前请确保您使用的是 **Python 3.11** 以避免兼容性问题。

1. **安装 Open WebUI**：  
   打开终端并运行以下命令安装 Open WebUI：

   ```bash
   pip install open-webui
   ```

2. **运行 Open WebUI**：  
   安装后，您可以通过执行以下命令启动 Open WebUI：

   ```bash
   open-webui serve
   ```

这将启动 Open WebUI 服务器，您可以通过 [http://localhost:8080](http://localhost:8080) 访问。

### 使用 Docker 快速启动 🐳

> [!注意]  
> 请注意，某些 Docker 环境可能需要额外的配置。如果遇到连接问题，我们的 [Open WebUI 文档](https://docs.openwebui.com/) 中提供了详细的指南。

> [!警告]  
> 使用 Docker 安装 Open WebUI 时，请确保在命令中包含 `-v open-webui:/app/backend/data`。此步骤至关重要，它可确保正确挂载数据库并防止数据丢失。

> [!提示]  
> 如果您希望使用带有 Ollama 或 CUDA 加速的 Open WebUI，我们建议使用标有 `:cuda` 或 `:ollama` 标签的官方镜像。要启用 CUDA，您必须在 Linux/WSL 系统上安装 [Nvidia CUDA 容器工具包](https://docs.nvidia.com/dgx/nvidia-container-runtime-upgrade/)。

### 默认配置安装

- **如果 Ollama 在您的计算机上**，请使用以下命令：

  ```bash
  docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
  ```   

- **如果 Ollama 在不同的服务器上**，请使用以下命令：

要连接到另一台服务器上的 Ollama，请将 `OLLAMA_BASE_URL` 更改为服务器的 URL：

```bash
docker run -d -p 3000:8080 -e OLLAMA_BASE_URL=https://example.com -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

- **使用 Nvidia GPU 支持运行 Open WebUI**，请使用以下命令：

```bash
docker run -d -p 3000:8080 --gpus all --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:cuda
```

### 仅用于 OpenAI API 的安装

- **如果您只使用 OpenAI API**，请使用以下命令：

```bash
docker run -d -p 3000:8080 -e OPENAI_API_KEY=your_secret_key -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

### 安装包含 Ollama 支持的 Open WebUI

此安装方法使用一个打包了 Open WebUI 和 Ollama 的单一容器镜像，允许通过单一命令进行简化安装。根据您的硬件设置选择合适的命令：

- **支持 GPU**：
  通过运行以下命令利用 GPU 资源：

```bash
docker run -d -p 3000:8080 --gpus=all -v ollama:/root/.ollama -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:ollama
```

- **仅使用 CPU**：
  如果不使用 GPU，请使用以下命令：

```bash
docker run -d -p 3000:8080 -v ollama:/root/.ollama -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:ollama
```

两种命令都可以方便内建安装 Open WebUI 和 Ollama，确保您快速完成安装并运行。

安装完成后，您可以访问 [http://localhost:3000](http://localhost:3000) 的 Open WebUI。享受吧！😄

### 其他安装方法

我们提供多种安装替代方案，包括非 Docker 的原生安装方法、Docker Compose、Kustomize 和 Helm。访问我们的 [Open WebUI 文档](https://docs.openwebui.com/getting-started/) 或加入我们的 [Discord 社区](https://discord.gg/5rJgQTnV4s) 获取完整指南。

### 疑难解答

遇到连接问题？我们的 [Open WebUI 文档](https://docs.openwebui.com/troubleshooting/) 可以帮助您解决问题。有关进一步的帮助并加入我们的活跃社区，请访问 [Open WebUI Discord](https://discord.gg/5rJgQTnV4s)。

#### Open WebUI：服务器连接错误

如果您遇到连接问题，通常是由于 WebUI docker 容器无法在容器内到达 127.0.0.1:11434（host.docker.internal:11434）的 Ollama 服务器所致。在您的 docker 命令中使用 `--network=host` 标志来解决此问题。请注意，端口从 3000 变为 8080，链接为：`http://localhost:8080`。

**示例 Docker 命令**：

```bash
docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

### 保持 Docker 安装最新

如果您希望将本地 Docker 安装更新到最新版本，可以使用 [Watchtower](https://containrrr.dev/watchtower/) 进行：

```bash
docker run --rm --volume /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower --run-once open-webui
```

在命令的最后部分，如果容器名称不同，请将 `open-webui` 替换为您的容器名称。

请查看我们在 [Open WebUI 文档](https://docs.openwebui.com/migration/) 中的迁移指南。

### 使用开发分支 🌙

> [!WARNING]
> `:dev` 分支包含最新的不稳定功能和变更。使用时需自行承担风险，因为可能存在错误或不完整功能。

如果你想尝试最新的尖端功能并能接受偶尔的不稳定，可以使用 `:dev` 标签，如下：

```bash
docker run -d -p 3000:8080 -v open-webui:/app/backend/data --name open-webui --add-host=host.docker.internal:host-gateway --restart always ghcr.io/open-webui/open-webui:dev
```

## 下一步是什么？🌟

在 [Open WebUI 文档](https://docs.openwebui.com/roadmap/) 中发现即将推出的功能。

## 支持者 ✨

向我们的杰出支持者致敬，他们帮助这个项目成为现实！🙏

### 白金赞助商 🤍

- 我们正在寻找赞助商！

### 鸣谢

特别感谢 [Lawrence Kim 教授](https://www.lhkim.com/) 和 [Nick Vincent 教授](https://www.nickmvincent.com/) 对该项目成为研究工作的支持和指导。感激您在整个过程中的指导！🙌

## 许可 📜

本项目使用 [MIT 许可](LICENSE) - 详细信息请参阅 [LICENSE](LICENSE) 文件。📄

## 支持 💬

如果您有任何问题、建议或需要帮助，请打开一个问题，或加入我们的 [Open WebUI Discord 社区](https://discord.gg/5rJgQTnV4s) 以与我们联系！🤝

## 星标历史

<a href="https://star-history.com/#open-webui/open-webui&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=open-webui/open-webui&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=open-webui/open-webui&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=open-webui/open-webui&type=Date" />
  </picture>
</a>

---

由 [Timothy J. Baek](https://github.com/tjbck) 创建 - 让我们一起让 Open WebUI 更加出色！💪
