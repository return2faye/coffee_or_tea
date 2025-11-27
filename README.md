# Coffee Production Analysis Project

Coffee production data analysis and prediction pipeline.

## Project Structure

```
coffee_or_tea/
├── data/
│   ├── psd_coffee.csv           # 原始数据 (Raw data)
│   └── processed_coffee.csv     # 清洗后的数据 (Processed/cleaned data)
├── figures/                     # 所有生成的图片 (300dpi)
│   ├── production_trends.png
│   ├── feature_importance.png
│   ├── shap_summary.png
│   └── predicted_vs_actual.png
├── results/                     # 模型结果 (Model results)
│   └── model_performance_metrics.csv
├── src/                         # 源代码 (Source code)
│   └── coffee_production_pipeline.py
└── README.md
```

## Environment Setup

### 1. 创建虚拟环境 (Create Virtual Environment)

推荐使用虚拟环境来管理依赖：

```bash
# 使用 venv (Python 3.3+)
python -m venv venv

# 或者使用 conda
conda create -n coffee_or_tea python=3.10
conda activate coffee_or_tea
```

### 2. 激活虚拟环境 (Activate Virtual Environment)

```bash
# macOS/Linux
source venv/bin/activate

# Windows
venv\Scripts\activate

# 如果使用 conda
conda activate coffee_or_tea
```

### 3. 安装依赖 (Install Dependencies)

```bash
pip install -r requirements.txt
```

### 4. 配置 Jupyter Notebook

如果你要在 `src/` 目录下使用 Jupyter Notebook：

```bash
# 安装 Jupyter kernel (在虚拟环境中)
python -m ipykernel install --user --name coffee_or_tea --display-name "Python (coffee_or_tea)"

# 启动 Jupyter Notebook
jupyter notebook

# 或者启动 JupyterLab
jupyter lab
```

在 Jupyter 中选择 kernel: `Kernel` -> `Change Kernel` -> `Python (coffee_or_tea)`

## Getting Started

1. Place your raw data in `data/psd_coffee.csv`
2. Run the pipeline: `python src/coffee_production_pipeline.py`
   - 或者打开 `src/` 目录下的 Jupyter Notebook 进行分析
3. Check results in `results/` and visualizations in `figures/`
