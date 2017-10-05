# Build

## Docker 

### Git repository

Clone `iroha` repository on your directory.

> Cloning Iroha

``` shell
git clone -b develop --depth=1 \
https://github.com/hyperledger/iroha /path/to/iroha
```

### How to run development environment

``` shell
/path/to/iroha/scripts/run-iroha-dev.sh
```

You will be attached to interactive environment for development and testing with `iroha` folder mounted from host machine.

Docker environment will be removed when you logout from the container.

### Build `iroha` and run tests

Build:
``` shell
cmake -H. -Bbuild; 
cmake --build build -- -j$(nproc)
```

`irohad` and `iroha-cli` binaries will be in `./build/bin` directory.

> How to run tests method #1

``` shell
cmake --build build --target test
```

> How to run tests method #2

``` shell
ctest . # in build folder 
```

### Execute `iroha-cli` with `irohad` running

Execute `run-iroha-dev.sh` again to attach to existing container.

## Linux or macOS

> Linux

``` shell
apt-get -y --no-install-recommends install \
        build-essential python-software-properties \
        automake libtool \
        libssl-dev zlib1g-dev libboost-all-dev \
        libc6-dbg golang \
        git ssh tar gzip ca-certificates \
        python3 python3-pip python3-setuptools \
        lcov \
        wget curl cmake file unzip gdb \
        iputils-ping vim ccache \
        gcovr vera++ cppcheck doxygen \
        graphviz graphviz-dev; \
    apt-get -y clean
git clone https://github.com/hyperledger/iroha -b develop
cd iroha
cmake -H. -Bbuild
cmake --build build -- -j4
```

> macOS

``` shell
xcode-select --install
# if you dont't have brew installed
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/homebrew/install/master/install)"
brew install cmake boost postgres grpc autoconf automake libtool golang
git clone https://github.com/hyperledger/iroha -b develop
cd iroha
cmake -H. -Bbuild
cmake --build build -- -j4
```
> macOS brew

``` shell
brew tap soramitsu/iroha
brew install iroha
```

