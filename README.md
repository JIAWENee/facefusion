FaceFusion
==========

> Industry leading face manipulation platform.

[![Build Status](https://img.shields.io/github/actions/workflow/status/facefusion/facefusion/ci.yml.svg?branch=master)](https://github.com/facefusion/facefusion/actions?query=workflow:ci)
[![Coverage Status](https://img.shields.io/coveralls/facefusion/facefusion.svg)](https://coveralls.io/r/facefusion/facefusion)
![License](https://img.shields.io/badge/license-OpenRAIL--AS-green)


## 安装

- 终端安装：参见[官方文档](https://docs.facefusion.io/installation)
- 一键安装：
  - [Windows Installer](http://windows-installer.facefusion.io/)
  - [macOS Installer](http://macos-installer.facefusion.io/)

### Ubuntu 终端安装示例
#### 1. 安装工具

- Git
```bash
apt install git-all
```

- cURL
```bash
apt install curl
```

- Conda
```bash
curl -LO https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

```bash
bash Miniconda3-latest-Linux-x86_64.sh
```

- FFmpeg
```bash
apt install ffmpeg
```

#### 2. 创建虚拟环境

- 为终端初始化 conda：
```bash
conda init --all
```

- 创建环境：
```bash
conda create --name facefusion python=3.12 pip=25.0
```

- 激活环境：
```bash
conda activate facefusion
```

#### 3. 安装加速库（可选：CUDA）

- 官方命令
```bash
conda install nvidia/label/cuda-12.9.1::cuda-runtime nvidia/label/cudnn-9.10.0::cudnn
```

- 选择与系统匹配的版本（通过 nvidia-smi 查看）
```bash
# Driver Version: 565.57.01      CUDA Version: 12.7
conda install -c "nvidia/label/cuda-12.7.1" cuda-runtime cudnn=9.1
```

#### 4. 克隆存储库
```bash
git clone https://github.com/facefusion/facefusion

cd facefusion
```

#### 5. 安装应用程序
```bash
python install.py --onnxruntime cuda
```

#### 6. 重新加载环境
```bash
conda deactivate

conda activate facefusion
```

#### 7. 完成
首次运行会自动下载所需模型：
```bash
python facefusion.py run --open-browser
```


## 快速开始
> 可通过修改 `facefusion.ini` 调整默认配置。

### Gradio 图形界面 (run)
```bash
# 绑定到所有 IP，允许外部访问
python facefusion.py run --open-browser --ui-server-host 0.0.0.0 --ui-server-port 7860 --keep-temp
```
如果未指定 `output_path`，输出文件默认保存在临时目录 `/tmp` 。

文件名格式为：8位哈希值 + 原文件扩展名（例如：a1b2c3d4.mp4）


### CLI 无界面模式 (headless-run)
```bash
python facefusion.py headless-run \
  --processors face_swapper face_enhancer \
  --source 源人脸图片.jpg \
  --target 目标视频.mp4 \
  --output-path 输出视频.mp4
```

示例：
```bash
python facefusion.py headless-run \
  --processors face_swapper face_enhancer \
  --source assets/dilireba.jpg \
  --target assets/demo_video.mp4 \
  --output-path assets/demo_output.mp4 \
  --log-level debug \
  --keep-temp
```

## 文档
阅读[官方文档](https://docs.facefusion.io/)以深入了解。

## Gradio 预览

![Preview](https://raw.githubusercontent.com/facefusion/facefusion/master/.github/preview.png?sanitize=true)


## 用法

Run the command:

```
python facefusion.py [commands] [options]

options:
  -h, --help                                      show this help message and exit
  -v, --version                                   show program's version number and exit

commands:
    run                                           run the program
    headless-run                                  run the program in headless mode
    batch-run                                     run the program in batch mode
    force-download                                force automate downloads and exit
    benchmark                                     benchmark the program
    job-list                                      list jobs by status
    job-create                                    create a drafted job
    job-submit                                    submit a drafted job to become a queued job
    job-submit-all                                submit all drafted jobs to become a queued jobs
    job-delete                                    delete a drafted, queued, failed or completed job
    job-delete-all                                delete all drafted, queued, failed and completed jobs
    job-add-step                                  add a step to a drafted job
    job-remix-step                                remix a previous step from a drafted job
    job-insert-step                               insert a step to a drafted job
    job-remove-step                               remove a step from a drafted job
    job-run                                       run a queued job
    job-run-all                                   run all queued jobs
    job-retry                                     retry a failed job
    job-retry-all                                 retry all failed jobs
```