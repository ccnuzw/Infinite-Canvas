# Infinite Canvas

Infinite Canvas 是一个自托管的 AI 图像、视频和文本创作工作台。它以本地 Web 应用的形式运行，把多种模型接口、无限画布、ComfyUI 工作流和素材管理集中在一个界面中。

## 核心功能

- 无限画布与智能画布：管理提示词、图片、视频、音频、LLM 和生成节点。
- 多平台接入：支持 OpenAI 兼容接口、Gemini、ModelScope、RunningHub、火山方舟、即梦 CLI 等。
- ComfyUI 工作流：连接本地或局域网 ComfyUI，导入 API 格式工作流并配置可调参数。
- 图片与视频创作：文生图、图生图、图片编辑、视频生成、增强、裁剪、遮罩和宫格切分。
- 素材管理：管理图片、视频、音频、提示词、工作流和画布资产。
- 工作流导入导出：支持 JSON 工作流，以及包含资源的 ZIP 工作流包。

## 快速开始

### Windows

需要 Python 3.10 或更高版本。项目目录中如果包含便携版 Python，启动脚本会优先使用它。

```bat
安装依赖.bat
run.bat
```

也可以手动启动：

```bat
python main.py
```

### macOS / Linux

```bash
python3 --version
python3 -m pip install -r requirements.txt
python3 main.py
```

macOS 也可以使用项目内的脚本：

```bash
./mac-安装依赖.sh
./mac-启动服务.sh
```

启动后访问：

```text
http://127.0.0.1:3000/
```

服务监听 `0.0.0.0:3000`，需要局域网或 VPS 访问时，可以使用服务器地址和端口访问。生产环境建议通过反向代理、HTTPS 和访问控制保护服务。

## 基本配置

1. 打开首页左侧的「API 设置」。
2. 新增或选择一个平台，填写 Base URL、协议和 API Key。
3. 验证连接并拉取模型列表。
4. 保存后，在画布或其他功能页面选择对应的平台和模型。

使用 ComfyUI 时：

1. 确保 ComfyUI 已启动，默认地址为 `127.0.0.1:8188`。
2. 打开「工作流设置」。
3. 导入 ComfyUI 的 API 格式 JSON 工作流。
4. 配置需要暴露到画布的输入参数。

## 数据与安全

项目运行时会在本地生成配置和用户数据，包括：

- `data/`：API 平台配置、画布、素材索引、提示词库等。
- `API/.env`：部分平台的密钥和环境配置。
- `assets/`、`output/`：上传素材和生成结果。
- `global_config.json`：部分全局配置。

这些目录和文件包含个人数据或 API Key，不要提交到公开仓库，也不要直接把同一个服务实例暴露给不可信用户。当前项目没有内置多用户权限隔离；多人访问同一个实例时，平台配置、文件和部分运行状态可能共享。

## 项目结构

```text
main.py                  FastAPI 服务入口
static/                  Web 前端页面、脚本和样式
workflows/               内置 ComfyUI 工作流
tools/                   辅助工具和浏览器插件
requirements.txt         Python 依赖
新手运行与使用教程.md    使用说明
MAC-使用说明.md          macOS 说明
```

## 许可证

许可证和使用条件请查看项目根目录的 [LICENSE](LICENSE) 文件。
