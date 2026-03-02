# Automatical Lumerical FDTD Simulation

Fully automated Lumerical FDTD simulation and optical device design powered by Vibe Coding. Just provide a prompt — the model handles error correction and iterative optimization entirely on its own.

> Last updated: 2026.03.02

---

## Vibe Coding Methods Overview

There are several mainstream approaches to Vibe Coding:

- **Direct conversation with web-based LLMs**: Interact via copy-paste (Ctrl+C / Ctrl+V), relying almost entirely on the LLM itself with minimal tool support (e.g., web search).
- **Agent-based programming**: The LLM acts as the "brain" and can invoke various tools such as file operations and terminal commands. Specific approaches include:
  1. AI plugins within IDEs (e.g., VS Code)
  2. IDEs with native AI integration — Trae (ByteDance), AntiGravity (Google), Cursor, etc.
  3. Linux CLI tools — Claude Code CLI, Codex CLI (server-friendly with low CPU/memory overhead)
- More advanced approaches also exist, such as orchestrating Agents that call Sub-agents, but only beginner-friendly methods are listed here.

---

## Example: Fully Automated Lumerical FDTD Simulation with Trae (International)

In theory, this method also applies to other solvers such as FDE, EME, and Interconnect. However, for solvers with limited online resources (e.g., CHARGE), a more capable LLM — or a future domain-specific fine-tuned model — may be required.

### Core Requirements

- **A clear and well-structured prompt**
- **A capable AI IDE** (Trae International Edition in this example)
- **A sufficiently intelligent LLM** (Gemini 3 Pro Preview, built into Trae, in this example)

> **Note on domestic Chinese models:** I also tested with Trae China Edition using Kimi 2.5, GLM-5, MiniMax 2.5, and several other models. None were able to complete the task, and some fell into confusing infinite loops. That said, this is not a particularly difficult Vibe Coding task, so with continued iteration, domestic models should be able to handle it in the near future. Looking forward to it!

### Demo Prompt

```text
You need to complete a Lumerical FDTD simulation task. Details are as follows:

1. I am using Lumerical 2025 R1. Please use its built-in Python interpreter at:
   "C:\Program Files\ANSYS Inc\v251\Lumerical\python-3.9.9-embed-amd64\python.exe"

2. Write a script to simulate and design a 1×2 MMI beam splitter. The splitter should
   include an input waveguide, input taper, rectangular MMI interference region, output
   tapers, and output waveguides. Please search and learn the standard 1×2 MMI structure.

3. The simulation wavelength is 4 μm (mid-infrared), fundamental TE mode.

4. The fabrication platform is based on 1200 nm etched to 600 nm TFLN on sapphire
   substrate, X-cut Y-propagation, no cladding, waveguide width 2 μm.

Acceptance criteria:
- The device achieves equal-power splitting
- Splitting power imbalance < 5%
- Insertion loss < 0.5 dB

Please run the code yourself, debug based on the terminal output, and iterate until
the code runs successfully and the device performance meets the acceptance criteria.

Finally, after all optimizations are complete, save the final result as a Lumerical
FDTD file for my review.
```

### Workflow

1. Send the prompt above to Trae
2. Wait for the AI to automatically complete the design and optimization
3. Open the saved simulation file and review the results

It's that simple! If it doesn't succeed on the first try, just describe the issue you found to Trae — it will continue debugging automatically until the simulation runs correctly.

---

## Contact

Feel free to reach out for discussion! WeChat: tuzengji
