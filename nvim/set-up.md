## download binary
https://github.com/neovim/neovim/releases/

## from source code
```bash
git clone --depth 1 https://github.com/neovim/neovim.git
conda install gxx_linux-64
make CMAKE_EXTRA_FLAGS="-DCMAKE_INSTALL_PREFIX=$(pwd)/bin/" # will fail due to network, try again in that case
make install
```