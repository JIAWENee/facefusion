FaceFusion - 人脸处理工具
==========

> Industry leading face manipulation platform.

[![Build Status](https://img.shields.io/github/actions/workflow/status/facefusion/facefusion/ci.yml.svg?branch=master)](https://github.com/facefusion/facefusion/actions?query=workflow:ci)
[![Coverage Status](https://img.shields.io/coveralls/facefusion/facefusion.svg)](https://coveralls.io/r/facefusion/facefusion)
![License](https://img.shields.io/badge/license-OpenRAIL--AS-green)


Preview
-------

![Preview](https://raw.githubusercontent.com/facefusion/facefusion/master/.github/preview.png?sanitize=true)


Installation
------------

Be aware, the [installation](https://docs.facefusion.io/installation) needs technical skills and is not recommended for beginners. In case you are not comfortable using a terminal, our [Windows Installer](http://windows-installer.facefusion.io) and [macOS Installer](http://macos-installer.facefusion.io) get you started.

### Ubuntu 安装步骤

#### 1. 安装工具

- cURL
```bash
apt install curl
```

- FFmpeg
```bash
apt install ffmpeg
```

#### 2. 创建虚拟环境

```bash
conda init --all

conda create --name facefusion python=3.12 pip=25.0

conda activate facefusion
```

#### 3. 安装加速器
##### CUDA

- 官方命令
```bash
conda install nvidia/label/cuda-12.9.1::cuda-runtime nvidia/label/cudnn-9.10.0::cudnn
```

- 选择与系统匹配的版本 （我的版本是 CUDA 12.2）
```bash
conda install nvidia/label/cuda-12.2.2::cuda-runtime nvidia/label/cudnn-9.10.0::cudnn -y
```


#### 4. 安装应用程序

```bash
python install.py --onnxruntime cuda
```

#### 5. 重新加载环境
```bash
conda deactivate

conda activate facefusion
```


#### 6. 完成
最后，运行程序：

```bash
python facefusion.py run --open-browser
```
首次运行会先下载模型。





Usage
-----

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


Documentation
-------------

Read the [documentation](https://docs.facefusion.io) for a deep dive.
