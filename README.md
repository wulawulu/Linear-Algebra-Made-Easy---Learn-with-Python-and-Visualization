# 线性代数：Python 与可视化

本项目使用 uv 管理 Python 3.12 环境及 Notebook 依赖。

## 安装依赖

在项目根目录运行：

```bash
uv sync --locked
```

uv 会创建 `.venv`，并按 `uv.lock` 安装依赖。首次使用需要先安装 uv。

## 在 VS Code 中运行 Notebook

1. 用 VS Code 打开整个项目目录（可在项目根目录运行 `code .`）。
2. 安装工作区推荐的 Python、Pylance 和 Jupyter 扩展。
3. 打开任意 `.ipynb` 文件，点击右上角「选择内核 / Select Kernel」，选择「Python 环境 / Python Environments」中的 `.venv`（Python 3.12）。
4. 运行单元格或点击「全部运行 / Run All」。

工作区已将 `.venv` 设为默认 Python 解释器，并将 Notebook 工作目录设为项目根目录，以便读取随项目提供的 `.pkl` 数据文件。Notebook 内核首次仍可能需要手动选择；无需额外注册全局内核。

如果在 WSL 中使用，请通过 VS Code 的 WSL 模式打开此目录，并将上述扩展安装到 WSL 环境。

## 管理依赖

```bash
uv add 包名
uv sync --locked
```

提交 `pyproject.toml`、`uv.lock` 和 `.python-version`，无需提交 `.venv`。

## 验证情况

依赖导入和 Jupyter 内核启动已验证。使用非交互绘图后端顺序执行 88 个 Notebook 的代码时，84 个通过，以下 4 个仍存在代码运行问题：

- `LA_01_08_05.ipynb`：使用了未定义的 `L2_a`。
- `LA_04_04_01.ipynb`：使用了未定义的 `col`。
- `LA_12_03_01.ipynb`、`LA_15_04_01.ipynb`：将复数数组传给图像绘制函数，触发 `TypeError`。

本次环境配置保留原始 Notebook 内容；上述运行问题需要另行修改 Notebook 代码。
