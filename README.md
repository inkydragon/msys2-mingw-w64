# MSYS2 Mingw-w64 Toolchain in Windows docker

## Build

```pwsh
cd msys2-mingw-w64
docker build -t msys2-mingw-w64  .

# Or use mirrors:  https://www.msys2.org/dev/mirrors/
docker build --build-arg MSYS2_DOWNLOAD_URL=https://mirrors.tuna.tsinghua.edu.cn/msys2/distrib/x86_64/msys2-base-x86_64-20220603.sfx.exe  -t msys2-mingw-w64  .
```


## License

> /* SPDX-License-Identifier: Unlicense OR MIT */

The repo is distributed under the terms of [Unlicense (public domain)](LICENSE) OR [MIT License](LICENSE.MIT).
