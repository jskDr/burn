# Regression

The example shows you how to:

- Define a custom dataset for regression problems. We implement the  [Diabetes Toy Dataset](https://huggingface.co/datasets/Jayabalambika/toy-diabetes) 
from HuggingFace hub. The dataset is also available as part of toy regression datasets in sklearn[datasets](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_diabetes.html).
- Create a data pipeline from a raw dataset to a batched fast DataLoader with min-max feature scaling.
- Define a Simple NN model for regression using Burn Modules.

The example can be run like so:

```bash
git clone https://github.com/tracel-ai/burn.git
cd burn
# Use the --release flag to really speed up training.
echo "Using ndarray backend"
cargo run --example regression --release --features ndarray                # CPU NdArray Backend - f32 - single thread
cargo run --example regression --release --features ndarray-blas-openblas  # CPU NdArray Backend - f32 - blas with openblas
cargo run --example regression --release --features ndarray-blas-netlib    # CPU NdArray Backend - f32 - blas with netlib
echo "Using tch backend"
export TORCH_CUDA_VERSION=cu113                                       # Set the cuda version
cargo run --example regression --release --features tch-gpu                # GPU Tch Backend - f32
cargo run --example regression --release --features tch-cpu                # CPU Tch Backend - f32
echo "Using wgpu backend"
cargo run --example regression --release --features wgpu
```
