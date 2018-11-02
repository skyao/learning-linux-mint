# 字体设置

## 使用微软雅黑字体

备注：非视网膜屏幕推荐。

1. 从win10系统中提取出字体文件  msyh.ttf 和 msyhbd.ttf

2. 在linux mint 系统字体文件夹中建立对应的字体文件夹

   ```bash
   sudo mkdir /usr/share/fonts/msyh
   sudo cp msyh.ttf msyhbd.ttf   /usr/share/fonts/msyh
   sudo fc-cache  -fv
   ```

3. `菜单-->首选项-->字体` 设置字体

## 移除不需要的字体

在软件管理器中，找到"Fonts-arphic-ukai"和"Fonts-arphic-uming"，移除这两个字体。

注：没有验证删除后有什么变化。

## 修改字体为文泉微米等宽黑

打开菜单-->首选项-->字体，一律修改成文泉微米等宽黑。

备注：但是文泉微米等宽黑也不是很完美


