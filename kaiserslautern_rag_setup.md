# Environment Setup Guide: Kaiserslautern RAG

This guide details the steps to recreate the `kaiserslautern_rag` environment, optimized for **LangChain 0.3** and **GPU-accelerated** vector operations using CUDA.

## 1. Environment Creation
Create a clean Python 3.11 environment to ensure compatibility with all AI libraries.

```powershell
conda create -n kaiserslautern_rag python=3.11 -y
conda activate kaiserslautern_rag
```

## 2. Hardware Acceleration (CUDA/PyTorch)
Install PyTorch with CUDA 12.1 support to utilize the local GPU (e.g., GTX 1060).

```powershell
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia -y
```

### Verify the GPU ("The Moment of Truth")
Run this command to ensure Python can see your NVIDIA card:

```powershell
python -c "import torch; print(f'CUDA Available: {torch.cuda.is_available()}'); print(f'Using GPU: {torch.cuda.get_device_name(0)}')"
```

## 3. LangChain & Core Dependencies
Install the stable 0.3 branch of LangChain and the necessary PDF/UI tools.

```powershell
# Install core logic and loaders
pip install "langchain>=0.3.18" "langchain-community>=0.3.17" "langchain-openai" "langchain-chroma" "langchain-text-splitters" pypdf gradio python-dotenv

# Fix dependency conflicts and lock stable versions
pip install "langchain<0.4.0" "langchain-community<0.4.0" "langchain-core<0.4.0" "langchain-openai<0.4.0" "langchain-chroma<0.2.0" "sympy==1.13.1"
```

## 4. Jupyter Lab Integration
Set up the environment as a selectable kernel within Jupyter.

```powershell
pip install jupyterlab ipykernel
python -m ipykernel install --user --name kaiserslautern_rag --display-name "Python (Kaiserslautern RAG)"
```

## 5. Analytics & Visualization
Install tools for t-SNE 2D/3D visualizations and data handling.

```powershell
pip install plotly scikit-learn matplotlib pandas
```

## Summary of Versions
- Python: 3.11
- CUDA: 12.1
- LangChain: 0.3.x (Stable)
- Vector Store: ChromaDB

---

### Pro Tip for Sharing
If you want to make it even easier for others, you can create a `requirements.txt` file by running `pip freeze > requirements.txt` while your environment is active. Then they can just run `pip install -r requirements.txt`.

