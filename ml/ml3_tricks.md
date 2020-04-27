# 机器学习技巧

### 数据增强

#### 图像数据增强

- 调增亮度

对归一化后的图像像素，统一增加delta值(0到1之间)

```.python
tf.adjust_brightness();
```

- 调整对比度

对每个像素值x，调整后为(x-mean)*factor+mean

```.python
tf.adjust_contrast();
```

- 调整色相

调整色相，先转到HSV空间，增加对应色相值，再返回RGB空间

```.python
tf.adjust_hue();
```

- 调整饱和度

调整饱和度，先转到HSV空间，乘以对应饱和度系数，再返回RGB空间

```.python
tf.adjust_saturation();
```
