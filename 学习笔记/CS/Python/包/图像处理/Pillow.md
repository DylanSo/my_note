# Pillow
导入图像并获取图像某像素点的RGB值

```python
# XCTF 新手组 007
from PIL import Image

st = ""

for i in range(0, 103, 1):
    img = Image.open(f"gif/{i}.jpg")
    im = img.convert("RGB")# 切换模式为RGB
    a = im.getpixel((10, 10))# 获取坐标为(10,10)的像素点的RGB值
    if a[0] != 255:
        st += "1"
    else:
        st += "0"


for i in range(0, len(st), 8):
    byte = st[i:i+8]
    print(chr(int(byte, 2)), end="")
```
