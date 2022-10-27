# Cross-compiling openssl

## What is `openssl`  

Openssl is a software library which is used inside many high level languages (e.g. Python, Ruby etc.) and also in linux itself. It is used for security and other cryptography applications.  

## Building openssl for `riscv64` architecture

Following are the steps used to build openssl for riscv64 architecture.  

1. Get the source code of `openssl` and navigate inside the cloned repository using the commands below

    ```shell
    git clone https://github.com/openssl/openssl.git
    cd openssl
    ```

2. Configure openssl for building. In openssl there are some `os/compiler` choices which one can use to build for his architecture. But in our case there is no support for building with riscv64. As it is written in C language, so it can be compiled whether or not the support is given. Use the following command to generate a `Makefile` for `linux-generic64`

    ```shell
    ./Configure linux-generic64 --prefix=$PREFIX # Prefix is the directory where you want binaries to be installed at the end
    ```

3. After the above command is successfully completed, run the following command to build openssl using `riscv64-unknown-linux-gnu-gcc` compiler instead of native gcc compiler.

    ```shell
    make -j$(nproc) CC=riscv64-unknown-linux-gnu-gcc
    ```

4. Install the binaries in the specified `--prefix` using the command below

    ```shell
    make -j$(nproc) install CC=riscv64-unknown-linux-gnu-gcc
    ```

The installed binary can be tested on `qemu-riscv64` using the command below:

```shell
qemu-riscv64 -L $RISCV_SYSROOT ./openssl
```

Here $RISCV_SYSROOT is the `sysroot/` folder located inside the riscv gnu toolchain installed directory.

The above mentioned command will start the openssl console if everything went right.  

**Note:** Do not change the directory of openssl or rename it, as it some files inside it are inferred with absolute paths, changing the directory or renaming it will cause other packages to not configure openssl for them when cross-compiling.
