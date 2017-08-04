# Idea

## 安装

TBD

## 优化

默认安装的 idea，配置不够合理，需要修稿。

打开 idea 安装目录下的 `bin/idea.vmoptions` 文件，原来的默认内容如下：

```bash
-server
-Xms128m
-Xmx512m
-XX:ReservedCodeCacheSize=240m
-XX:+UseConcMarkSweepGC
-XX:SoftRefLRUPolicyMSPerMB=50
-ea
-Dsun.io.useCanonCaches=false
-Djava.net.preferIPv4Stack=true
-XX:+HeapDumpOnOutOfMemoryError
-XX:-OmitStackTraceInFastThrow
-Dawt.useSystemAAFontSettings=lcd
-Dsun.java2d.renderer=sun.java2d.marlin.MarlinRenderingEngine
```

修改配置如下：

```bash
-server
-Xms512m
-Xmn512m
-Xmx4g
-XX:ReservedCodeCacheSize=240m
-XX:+UseG1GC
-XX:+UseNUMA
-XX:MaxMetaspaceSize=512m
-XX:SoftRefLRUPolicyMSPerMB=50
-ea
-Dsun.io.useCanonCaches=false
-Djava.net.preferIPv4Stack=true
-XX:+HeapDumpOnOutOfMemoryError
-XX:-OmitStackTraceInFastThrow
-Dawt.useSystemAAFontSettings=lcd
-Dsun.java2d.renderer=sun.java2d.marlin.MarlinRenderingEngine
```

重新启动 idea。


