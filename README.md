# pnnx

![download](https://img.shields.io/github/downloads/pnnx/pnnx/total.svg)

PyTorch Neural Network eXchange

Note: The current WIP implementation is in https://github.com/Tencent/ncnn/pull/3262


## [Download](https://github.com/pnnx/pnnx/releases)

Download PNNX Windows/Linux/MacOS Executable

**https://github.com/pnnx/pnnx/releases**

This package includes all the binaries required. It is portable, so no CUDA or PyTorch runtime environment is needed :)

## Usages

### Example Command

```shell
pnnx.exe mobilenet_v2.pt inputshape=[1,3,224,224]
```

### Full Usages

```console
Usage: pnnx [model.pt] [(key=value)...]
  pnnxparam=model.pnnx.param
  pnnxbin=model.pnnx.bin
  pnnxpy=model_pnnx.py
  ncnnparam=model.ncnn.param
  ncnnbin=model.ncnn.bin
  ncnnpy=model_ncnn.py
  optlevel=2
  device=cpu/gpu
  inputshape=[1,3,224,224],...
  inputshape2=[1,3,320,320],...
  customop=/home/nihui/.cache/torch_extensions/fused/fused.so,...
  moduleop=models.common.Focus,models.yolo.Detect,...
Sample usage: pnnx mobilenet_v2.pt inputshape=[1,3,224,224]
              pnnx yolov5s.pt inputshape=[1,3,640,640] inputshape2=[1,3,320,320] device=gpu moduleop=models.common.Focus,models.yolo.Detect
```

## Build from Source

1. Download and setup the libtorch from https://pytorch.org/

2. Clone pnnx (inside nihui/ncnn pnnx branch atm)

```shell
git clone https://github.com/nihui/ncnn.git
cd ncnn
git checkout pnnx
```

3. Build with CMake

```shell
mkdir tools/pnnx/build
cd tools/pnnx/build
cmake -DCMAKE_INSTALL_PREFIX=install -DTorch_INSTALL_DIR=<your libtorch dir> ..
cmake --build . --config Release -j 2
cmake --build . --config Release --target install
```
