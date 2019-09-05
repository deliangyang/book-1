# 安装 Nu

目前启动和运行Nu最佳的方法是从[crates.io](https://crates.io)安装，从[release page](https://github.com/nushell/nushell/releases)下载预编译的二进制文件, 或者编译源码。

## 预编译的二进制文件

你可以从[release page](https://github.com/nushell/nushell/releases)下载Nu预编译文件。 另外，如果你在macOS上使用 [Homebrew](https://brew.sh/)，你可以执行`brew install nushell`安装二进制程序。

## 准备工作

在安装Nu执行，我们需要确认我们系统有必须的要求
我们需要在安装Nu之前确认我们的已经拥有系统所需的要求。目前，这意味着我们需要确保Rust toolchain和本地的依赖都已经安装好。

### 安装Rust

如果我们的系统没有安装Rust，最好的方法就是通过它来安装[rustup](https://rustup.rs/)。Rustup是一个管理Rust安装的方法，同时包含管理使用不同版本的Rust。

Nu现在要求Rust的版本是**nightly**。当我们第一打开“rustup”是，它会问我们要安装Rust的哪个版本：

```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

选择#2自定义安装，

```
Default host triple?
```

按下Enter，选择默认安装。

```
Default toolchain? (stable/beta/nightly/none)
```

确定版本是“nightly"，并且按下Enter键，我们将设置一下这个设置：

```
Modify PATH variable? (y/n)
```

你可以选择更新路径，这通常是一个不错的主意可以是你后续的步骤更加的容易。


```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: nightly
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

你可以看到我们默认的toolchain已经变成了nightly toolchain。如果这个听起来有点儿风险，请不要担心。Rust编译器是通过一整套测试运行的。nightly版本的编译器通常是最接近稳定版本的。

一旦我们准备好了，我们按下1，然后按下Enter键。在这之后，我们可以按照“rustup”给我们的说明，在我们的系统上有一个可以工作的Rust编译器。

如果你不想通过“rustup”安装Rust，你也可以使用其他的方法安装它（例如：安装来自Linux发行版的软件包），请务必安装最新的nightly版本的toolchain。

## 依赖

### Debian/Ubuntu

你需要安装“pkg-config”和“libssl-dev”：

```
apt install pkg-config libssl-dev
```

Linux用户希望使用`rawkey`和`clipboard`功能选项将需要安装软件包“libx11-dev”和“libxcb-composite0-dev”

```
apt install libxcb-composite0-dev libx11-dev
```

### macOS

使用[Homebrew](https://brew.sh/)，你需要安装“openssl”和“cmake”：

```
brew install openssl cmake
```

## 从[crates.io](https://crates.io)安装

一旦我们有Nu的依赖，我们可以使用Rust编译器附带的`cargo`命令安装它。

```
> cargo install nu
```

是的！工具cargo可以下载Nu并且在源码的依赖，编译之后会把Nu安装到cargo的bin目录下以便我们可以运行它。

安装之后，我们可以使用`Nu`命令执行Nu：

```
$ nu
/home/jonathan/Source> 
```

## 源码编译

我们也可以直接从github上下载源码，编译我们自己Nu。这可以使我们可以立即接触到Nu最新的功能和漏洞修复。

```
> git clone https://github.com/nushell/nushell.git
```

Git将克隆主要的nushell仓库。从那里你可以构建和运行Nu：
Git will clone the main nushell repo for us. From there, we can build and run Nu:

```
> cd nushell
nushell> cargo build && cargo run
```

你还可以在发布模式下构建和运行Nu

```
nushell> cargo build --release && cargo run --release
```

熟悉Rust的人可能知道执行“run”默认会执行构建，因此您可能想知道为什么这里要运行“build”和“run”。这是为了避免Cargo中新的`default-run`选项的缺点，并且确保所有的插件都已构建，尽管可能将来不需要它们。

