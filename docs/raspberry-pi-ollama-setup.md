# Raspberry Pi 5 (16 GB) — Ollama install and automatic startup

Hardware: Raspberry Pi 5, 16 GB RAM, Kingston NV3 2 TB NVMe SSD, X1015 NVMe HAT.

Ollama is a standalone application. **Python is not required** to install, run, or automatically start Ollama. Python is optional later for agent frameworks or scripts.

If a command says Ollama is not in `/usr/bin` or a user `bin` directory, that alone doesn't prove installation failed. The executable is commonly installed at `/usr/local/bin/ollama`. Check its actual location and service.

## Step 1 — Check the installation

Run this full block in your Pi's terminal:

```bash
uname -m
command -v ollama
ls -l /usr/local/bin/ollama /usr/bin/ollama 2>/dev/null
ollama --version
systemctl status ollama --no-pager
```

- `uname -m` should ideally print `aarch64` (64-bit ARM).
- `command -v ollama` displays the installed executable path if the command is on your PATH.
- An `ollama: command not found` result suggests it is missing or not on PATH.
- `Unit ollama.service could not be found` means its systemd service is not registered.

## Step 2 — Install or reinstall if needed

Use Ollama's official Linux installer:

```bash
sudo apt update
sudo apt install -y curl zstd
curl -fsSL https://ollama.com/install.sh | sh
```

Official instructions: https://ollama.com/download/linux

## Step 3 — Enable Ollama to start automatically

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now ollama
sudo systemctl status ollama --no-pager
```

You want to see `Active: active (running)`. The `enable --now` option both enables the service on boot and starts it immediately.

If it says `Unit ollama.service not found`, go back to Step 2 and inspect the installer's output.

For useful error details:

```bash
journalctl -u ollama -n 50 --no-pager
```

## Step 4 — Test a small local AI model

```bash
ollama run qwen3:0.6b
```

This downloads the model the first time and starts a chat. This small model is a good installation test.

## Realistic Pi 5 / 16 GB expectations

| Model size | What to expect |
| --- | --- |
| 0.5B–1B | Good starting point for install testing and lightweight jobs |
| 1.5B–3B | Usable small local models |
| 4B–8B | Possible with suitable quantization; CPU inference can be slow |
| 14B+ | RAM and speed become significant constraints |
| 27B | Typically impractical in 16 GB at ordinary 4-bit quantization |

Your 2 TB NVMe SSD is helpful for model storage and loading, but does not substitute for RAM during inference.

For more ambitious agentic workflows, keep Ollama as the inference server and add Python / an agent framework separately after the basic server works.

**If anything fails:** Copy the terminal output from Step 1 (and the `journalctl` output if relevant) so the precise error can be diagnosed, rather than repeating installation commands blindly.
