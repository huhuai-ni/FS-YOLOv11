# FS-YOLOv11 · 火焰烟雾检测系统

基于 **YOLOv11** 的火焰与烟雾实时检测系统，配套 **PySide6** 桌面界面，用于摄像头 / 视频流中的早期火灾预警。

> 仓库当前为项目说明页，源码与训练权重整理中。

## 功能

- 实时检测画面中的 **火焰（fire）** 与 **烟雾（smoke）**
- 桌面端界面：登录页 + 检测页，摄像头实时预览与结果框选
- 检测到目标时触发报警提示（可扩展微信 / 声音通知）
- 支持图片、视频、摄像头三种输入源

## 技术栈

| 层 | 选型 |
|---|---|
| 检测模型 | YOLOv11（Ultralytics） |
| 界面 | PySide6 / Qt |
| 推理 | PyTorch + OpenCV |
| 训练数据 | Roboflow 公开火焰烟雾数据集 + 自标注 |
| 环境 | Anaconda（Python 3.9+）、CUDA |

## 目录结构（计划）

```
FS-YOLOv11/
├── main.py              # 程序入口
├── login_window.py      # 登录界面
├── detection_window.py  # 检测界面
├── models/              # 权重文件（.pt）
├── dataset/             # 数据集配置
├── requirements.txt
└── README.md
```

## 快速开始

```bash
# 1. 建环境
conda create -n yolo11 python=3.9 -y
conda activate yolo11

# 2. 装依赖
pip install ultralytics pyside6 opencv-python

# 3. 训练
yolo detect train data=dataset/data.yaml model=yolo11n.pt epochs=100 imgsz=640

# 4. 运行界面
python main.py
```

## 数据集

- 类别：`fire`、`smoke`
- 来源：Roboflow Universe 公开数据集 + 自采视频抽帧标注
- 划分：train / val / test = 8 : 1 : 1

## 进度

- [x] 数据集准备与标注
- [x] 模型训练与验证
- [x] PySide6 界面（登录 + 检测）
- [ ] 报警联动（微信 / 声音）
- [ ] 模型量化与边缘部署
- [ ] 源码与权重上传

## 说明

本项目为本科毕业设计，代码整理后开源。模型权重较大，后续通过 Release 发布。

---

作者：[@huhuai-ni](https://github.com/huhuai-ni)
