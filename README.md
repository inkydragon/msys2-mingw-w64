# MSYS2 Mingw-w64 Toolchain in Windows docker

## Build docker image

```pwsh
cd msys2-mingw-w64
docker build -t msys2-mingw-w64  .

# Or use mirrors:  https://www.msys2.org/dev/mirrors/
docker build --build-arg MSYS2_DOWNLOAD_URL=https://mirrors.tuna.tsinghua.edu.cn/msys2/distrib/x86_64/msys2-base-x86_64-20220603.sfx.exe  -t msys2-mingw-w64  .
```


## Build julia

```pwsh
#  Run container
docker run -it --cpus="8" --memory=16G  msys2-mingw-w64

#  Clone julia
git clone https://github.com/JuliaLang/julia.git
cd julia

#  Cross-compiling with MINGW64 by default
make O=julia-docker-mingw64  configure
make -C julia-docker-mingw64 -j 8
```


## License

> /* SPDX-License-Identifier: Unlicense OR MIT */

The repo is distributed under the terms of [Unlicense (public domain)](LICENSE) OR [MIT License](LICENSE.MIT).
