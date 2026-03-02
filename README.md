[English Version](README_EN.md)


# Automatical Lumerical FDTD Simulation

利用 Vibe Coding 全自动完成 Lumerical FDTD 仿真，设计光学器件。仅需提供 Prompt，模型自动纠错与迭代，全程无需人工干预。

> 最近更新：2026.03.02

---

## Vibe Coding 方法概览

目前主流的 Vibe Coding 方式大致分为以下几种：

- **直接对话网页端大模型**：通过 Ctrl+C / Ctrl+V 与大模型交互，几乎仅调用大模型本身能力，辅以少量工具（如联网搜索）。
- **Agent 编程**：大模型作为"大脑"，同时可调用文件操作、终端指令等多种工具。具体途径包括：
  1. 在集成开发环境（IDE，如 VS Code）中使用 AI 插件
  2. 使用原生集成 AI 能力的 IDE —— Trae（字节跳动）、AntiGravity（Google）、Cursor 等
  3. Linux 命令行工具 —— Claude Code CLI、Codex CLI（对服务器开发友好，CPU 与内存占用低）
- 此外还有更高级的方式，例如策划 Agent 调用 Sub-agents 等，此处仅列举适合初学者的方法。

---

## 示例：使用 Trae 国际版进行全自动 Lumerical FDTD 仿真

理论上该方法同样适用于 FDE、EME、Interconnect 等求解器。但对于网络资料较少的求解器（如 CHARGE），可能需要更强大的 LLM，或等待未来针对性训练的模型。

### 核心要素

- **一个清晰的 Prompt**
- **一个优秀的 AI IDE**（本示例使用 Trae 国际版）
- **一个足够智能的 LLM**（本示例使用 Trae 内置的 Gemini 3 Pro Preview）

> **关于国产模型的测试说明：** 我同样在 Trae 中国版中进行了测试，尝试了 Kimi 2.5、GLM-5、MiniMax 2.5 等多个模型，均未能完成任务，且有时会陷入令人困惑的死循环。不过考虑到该任务并非高难度的 Vibe Coding 任务，随着国产模型持续迭代，未来完成此类任务应当不成问题。期待！

### 演示用 Prompt

```text
你需要完成 Lumerical FDTD 仿真任务，具体细节如下：

1. 我正在使用 2025 R1 版本的 Lumerical，请使用其自带的 Python 解释器，
   路径为 "C:\Program Files\ANSYS Inc\v251\Lumerical\python-3.9.9-embed-amd64\python.exe"。

2. 编写脚本仿真设计一个 1×2 MMI 分束器。分束器包括输入波导、输入 taper、
   矩形 MMI 干涉区、输出 taper、输出波导等结构。你需要搜索学习标准 1×2 MMI 的结构。

3. 仿真波段为 4 μm 中红外光，基模 TE 模式。

4. 基于 1200 nm 刻 600 nm 的 TFLN + 红宝石衬底工艺平台，X 切 Y 传，无包层，波导宽度 2 μm。

验收条件：
- 器件成功实现等功率分束
- 分束功率不均衡度 < 5%
- 传输损耗 < 0.5 dB

请自行运行代码，根据返回结果在终端中 debug，直到代码可以正常运行且器件性能满足验收条件。

最后，在完成所有优化后，将最终结果保存为一个 Lumerical FDTD 文件供我检验。
```

### 使用流程

1. 将上述 Prompt 发送给 Trae
2. 静待 AI 自动完成设计与优化
3. 获取保存好的仿真文件，打开查看结果即可

就是这么简单！如果遇到未一次成功的情况，只需将发现的问题反馈给 Trae，它会继续自动 debug，直到仿真正常运行。

---

