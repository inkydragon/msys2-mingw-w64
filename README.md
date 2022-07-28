# MSYS2 Mingw-w64 Toolchain in Windows docker

> The main usage of this image is to build [julia](https://github.com/JuliaLang/julia) on windows.

## Build julia using a pre-built image

Use `cmd /C ver` to check your windows version and make sure it is `>= 20H2 (10.0.19042.1826)`.
Or you need to build an image that matches your windows version.

```pwsh
#  Pull && Run container
docker pull woclass/msys2-mingw-w64
docker run -it --cpus="8" --memory=16G  woclass/msys2-mingw-w64

#  Clone julia
git clone https://github.com/JuliaLang/julia.git
cd julia

#  Cross-compiling with MINGW64 by default
make O=julia-docker-mingw64  configure
make -C julia-docker-mingw64 -j 8
```


## Build docker image

```pwsh
cd msys2-mingw-w64
docker build -t msys2-mingw-w64  .

#  Or choose an another windows version:  https://hub.docker.com/_/microsoft-windows-servercore
docker build --build-arg WIN_VERSION=ltsc2022 -t msys2-mingw-w64  .

#  Or use mirrors:  https://www.msys2.org/dev/mirrors/
docker build --build-arg MSYS2_DOWNLOAD_URL=https://mirrors.tuna.tsinghua.edu.cn/msys2/distrib/x86_64/msys2-base-x86_64-20220603.sfx.exe  -t msys2-mingw-w64  .
```


## Pre-installed pkg

```sh
cmake diffutils git m4 make patch tar p7zip curl python3

#  mingw64 toolchain
mingw-w64-x86_64-gcc mingw-w64-x86_64-gcc-fortran 
```


## License

> /* SPDX-License-Identifier: Unlicense OR MIT */

The repo is distributed under the terms of [Unlicense (public domain)](LICENSE) OR [MIT License](LICENSE.MIT).
