To find out if your Linux system has a GPU (graphics processing unit) and get details about it, you can use the following commands:

## lspci command

The `lspci` command lists all PCI devices, including graphics cards. Run:

```
lspci | grep -i --color 'vga\|3d\|2d'
```

This will show you any VGA, 3D or 2D graphics controllers detected.[1]

## lshw command 

The `lshw` (list hardware) command shows detailed information about your hardware configuration, including graphics cards. Run:

```
sudo lshw -C display
```

This will display verbose information about any display/graphics adapters found.[2]

## glxinfo command

If you have the OpenGL utilities installed, `glxinfo` will show information about your OpenGL renderer, which is typically your GPU:

```
glxinfo | grep "OpenGL renderer"
```

## nvidia-smi (for NVIDIA GPUs)

If you have the NVIDIA drivers installed, you can use the `nvidia-smi` tool to get detailed information about any NVIDIA GPUs:

```
nvidia-smi
```

This will list details like GPU model, driver version, memory usage, etc.[5]

So in summary, running `lspci`, `lshw`, `glxinfo` and/or `nvidia-smi` should allow you to detect if a GPU is present and get key details about it. The specific output will depend on your graphics hardware and drivers installed.[1][2][3][4]

Citations:
[1] https://itsfoss.com/check-graphics-card-linux/
[2] https://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/
[3] https://askubuntu.com/questions/5417/how-to-get-the-gpu-info
[4] https://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/
[5] https://stackoverflow.com/questions/67504079/how-to-check-if-an-nvidia-gpu-is-available-on-my-system


[[Ollama - Docker]]