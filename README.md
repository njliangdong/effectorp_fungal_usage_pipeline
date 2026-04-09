根据您的要求，已将这段 Shell 流水线注释转换为适用于 GitHub 仓库的 Markdown 格式。内容包含安装、变量配置及运行命令示例，可直接用于 `README.md`。

```markdown
# EffectorP Fungal Usage Pipeline

This pipeline demonstrates how to run **EffectorP 3.0** for fungal effector prediction using a Conda/Mamba environment.

## 🧪 Installation

Create and activate a dedicated environment, then install EffectorP 3.0 via the `predector` channel:

```bash
mamba create -n effector -y
mamba activate effector
mamba install predector::effectorp3 -y
```

## ⚙️ Configuration

Set the path to your Conda environment's `bin` directory and define your input file base name:

```bash
# Path to the bin directory of your active conda environment
opt_path="${CONDA_PREFIX}/bin"
# Base name of your input FASTA file (without extension)
name='C_siamense_JDA_12'
```

> **Note**: The variable `opt_path` points to the location of `EffectorP3.py`. Using `${CONDA_PREFIX}/bin` ensures it automatically references the currently active environment.

## 🚀 Run EffectorP 3.0

Execute the following command to predict effectors. The script assumes your input protein FASTA file is named `${name}.fa`.

```bash
python3 ${opt_path}/EffectorP3.py \
    -f \
    -i ${name}.fa \
    -o ${name}.Effectors.out.txt \
    -E ${name}.Effectors.out.fasta
```

### Parameter Explanation

| Flag | Description |
|------|-------------|
| `-f` | **Fungal mode** – required for analyzing fungal proteomes. |
| `-i` | Input FASTA file containing protein sequences. |
| `-o` | Output tab‑delimited file with prediction scores and classes. |
| `-E` | Output FASTA file containing only the sequences predicted as effectors. |

## 📁 Expected Output

After successful execution, you will obtain:

- `${name}.Effectors.out.txt` – Full prediction table with probabilities and final classification.
- `${name}.Effectors.out.fasta` – FASTA file containing only effector candidates (useful for downstream analyses).

## 🔧 Troubleshooting

- **Command not found**: Ensure your Conda environment is activated and that `EffectorP3.py` exists in the `bin` directory.
- **Permission errors**: Make the script executable if necessary: `chmod +x ${opt_path}/EffectorP3.py`.
- **Multi‑threading**: Add `-t <N>` to use multiple CPU cores (e.g., `-t 8`).
```

这份 README 片段可以直接粘贴到您的 GitHub 仓库文档中。如果您的实际 `EffectorP3.py` 版本不支持 `-f` 和 `-E` 选项（某些版本可能使用 `-p` 等不同参数），请根据 `python3 ${opt_path}/EffectorP3.py -h` 的输出调整相应标志。
