# peer-stream-vue
vue与ue的像素流交互

peer-stream作者 [peer-stream](https://github.com/inveta/peer-stream)

## 操作步骤

```bash
# px_test目录下运行虚幻引擎5.2.1版本
1. 编辑->插件->安装插件Pixel Steaming
2. 编辑->编辑器偏好设置->播放->额外启动参数->-AudioMixer -PixelStreamingIP=localhost -PixelStreamingPort=88
3. 打包ue程序
4. 将打包程序放在peer-stream-main的package文件夹下

# peer-stream-main目录下
npm install
node signal.js

# demo目录下
npm install
npm run serve
```

* vue
  * 发送消息：sendMessage
  * 接收消息：receiveMessage

* ue（源码在ue程序里的NewBlueprint蓝图类）
  * 发送消息：send pixel streaming response
  * 接收消息：add pixel streaming input
