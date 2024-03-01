If you use `Linux` or `BSD` terminal for coding (like me), probably you use `Emacs`, so here you find the steps for configuring `Emacs` for developing `RUST` applications.

### 1. Install `RUST`
```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
After installation, run the below command:
```sh
source "$HOME/.cargo/env"
```
And then check the `RUST` version by below command:
```sh
rustc --version
```  
For more information about the above command, please see the [RUST website](https://www.rust-lang.org/tools/install).

### 2. Emacs Configuration
- Install build-essential:
  ```sh
  sudo apt install build-essential git -y
  ```
  
- Install `RUST` source code:
  ```sh
  rustup component add rust-src
  ```
  
- Install `rust-analyzer server`:
  ```sh
  git clone https://github.com/rust-analyzer/rust-analyzer.git -b release
  cd rust-analyzer
  cargo xtask install --server
  ```
  
- update `~/.emacs`:
  Add the below configuration to your `.emacs`:
  ```emacs
  (setq package-archives
      '(("gnu" . "https://elpa.gnu.org/packages/")
        ("melpa" . "https://melpa.org/packages/")))
  ```
  
- Install Emacs packages: `use-package`

  `M-x`: As you know, On Debian, first press `Esc` and then press `x`.
  
  `↩`: Is the Enter Key.
  
  ```emacs
  M-x package-refresh-contents ↩
  M-x package-install ↩ use-package ↩
  ```
  
- Update `~/.emacs`:
  
  copy [this file](https://github.com/mohsenmoqadam/rust_on_emacs/blob/main/.emacs) to your `~/.emacs`

### 3. Create an example and check your emacs:
```sh
cargo new hello_world
cd hello_world/
emacs -nw src/main.rs
```
For the first time, wait a while for Emacs to be ready to use (depending on your internet speed).

and the final result😋:
![Screenshot](https://github.com/mohsenmoqadam/rust_on_emacs/blob/main/emacs.jpg)
