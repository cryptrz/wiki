To install CUDA on Arch Linux, follow these steps:

1. Install NVIDIA driver first (if not already installed) using:
   ```
   sudo pacman -S nvidia
   ```
2. Install the CUDA toolkit package from the official Arch repos:
   ```
   sudo pacman -S cuda
   ```
   This will install CUDA under `/opt/cuda`.

3. Add CUDA binaries to your PATH by appending to your shell config (`~/.bashrc` or `~/.zshrc`):
   ```
   export PATH=/opt/cuda/bin:$PATH
   export LD_LIBRARY_PATH=/opt/cuda/lib64:$LD_LIBRARY_PATH
   ```
   Then reload your shell or source the config file.

4. (Optional) Verify the installation by compiling CUDA samples or checking the CUDA compiler version:
   ```
   nvcc --version
   ```

5. For deep learning frameworks and libraries, it is often recommended to use a Conda or Mamba environment to manage versions:
   ```
   conda install -c nvidia cuda
   ```
   This allows you to handle different CUDA versions alongside packages like PyTorch.

6. If you need cuDNN, download the appropriate version from NVIDIA's site matching your CUDA version, then copy the headers and libraries into `/opt/cuda/include` and `/opt/cuda/lib64`.
