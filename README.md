# DF_Inference
YOLOv8 / YOLO26 推理可视化工具

百度网盘下载：
> 链接：https://pan.baidu.com/s/1V60GWaNll5WXTqPQHW8zrg
> 提取码：pw3e

## YAML 配置文件说明
### 参数列表
| 参数 | 说明 |
| ---- | ---- |
| `modelType` | 任务类型，可选：`detect`、`segment`、`pose`、`rotated`、`class`、`semanticSegment` |
| `isEnd2End` | 区分模型版本<br/>• `True`：NMS-Free YOLO26<br/>• `False`：YOLOv8 |
| `resizeType` | 图像预处理缩放模式<br/>• `0`：直接拉伸缩放到目标宽高<br/>• `1`：等比例缩放，左上对齐，剩余区域填充<br/>• `2`：等比例缩放，居中放置，两侧填充 |
| `size` | 模型输入尺寸，格式 `[width, height]` |
| `means` | 归一化均值，一般无需修改 |
| `scales` | 归一化缩放系数，一般无需修改<br/>计算公式：`x_normal = (x - means) * scales` |
| `nmsTh` | NMS的IoU阈值 |
| `confTh` | 置信度阈值，过滤低置信度预测框 |
| `keypoint_count` | 关键点任务使用，设置关键点数量 |
| `label_list` | 类别名称列表，顺序必须和模型类别索引保持一致 |

## 使用示例
YOLO26模型推理，需要准备 `model.onnx` 权重文件 + `model.yaml` 配置文件。

```yaml
modelType: detect
isEnd2End: True
resizeType: 1
size: [640, 640]
means: [0, 0, 0]
scales: [0.003906, 0.003906, 0.003906]
nmsTh: 0.4
confTh: 0.5
label_list: ["person","boy"]
