# wiliwili for Sunniwell Z96A (Rockchip RK3568)

This repository provides an automated AArch64 Bookworm build of [wiliwili](https://github.com/xfangfang/wiliwili) with Rockchip MPP hardware decoding support, specifically optimized for the Sunniwell Z96A (RK3568).

## Architecture

- **Hardware Decoding Backend**: Relies on [`jinyayayaya/z96a-mpv-rkmpp`](https://github.com/jinyayayaya/z96a-mpv-rkmpp) which provides an isolated prefix with Rockchip MPP, DRM PRIME, and FFmpeg 6.1 (with OpenSSL).
- **GUI & Video Rendering**: wiliwili links to `libmpv.so` and uses OpenGL ES 3.1 with DRM PRIME direct texture import (`drm_prime[nv12]`), ensuring 1080P@60fps zero-copy playback with under 15% CPU usage.

## Installation on Z96A

### 1. Ensure `z96a-mpv-rkmpp` runtime is installed
```sh
# Download and install runtime to /opt
curl -sSL "https://github.com/jinyayayaya/z96a-mpv-rkmpp/releases/download/v1.0.0/z96a-mpv-rkmpp.tar.gz" | sudo tar -C /opt -xzf -
```

### 2. Install wiliwili
```sh
# Download and extract wiliwili
curl -sSL "https://github.com/jinyayayaya/z96a-wiliwili/releases/download/v1.0.0/z96a-wiliwili.tar.gz" | sudo tar -C / -xzf -

# Symlink launcher
sudo ln -sf /opt/wiliwili/bin/wiliwili.sh /usr/local/bin/wiliwili
```

### 3. Launch
```sh
wiliwili
```
