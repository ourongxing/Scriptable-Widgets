## 快速使用
> 热榜组件由于其阅读属性所以仅适配大尺寸
1. iPhone 上下载 [Scriptable](https://apps.apple.com/cn/app/scriptable/id1405459188) App（确保你的系统已更新为 iOS14+）    
2. 复制下列代码，在 Scriptable 中新建脚本，并将其粘贴进去，运行即可一键安装你需要的脚本，你只需要修改其中的 Scripts 数组
```js
const FILE_MGR = FileManager[module.filename.includes('Documents/iCloud~') ? 'iCloud' : 'local']();
// 输入你想安装的脚本，点击运行即可安装
const Scripts = [
  '知乎热榜.js',
  '微博热搜.js',
  'B站排行榜.js',
  'V2EX.js',
  '步行街热帖.js'
]
await Promise.all(Scripts.map(async js => {
  const REQ = new Request(`https://cdn.jsdelivr.net/gh/ourongxing/Scriptable-Widgets/${encodeURIComponent(js)}`);
  const RES = await REQ.load();
  FILE_MGR.write(FILE_MGR.joinPath(FILE_MGR.documentsDirectory(), js), RES);
}));
FILE_MGR.remove(module.filename);
```
### 1. 微博热搜
> 去除 zzzq 和广告，可以设置点击链接后打开的客户端，支持微博和国际版微博。
<div><img src="./img/weibo.jpg" width="50%"></img></div>

### 2. V2EX
> 可以设置节点，目前有最新，最热，分享创造，分享发现，程序员，问与答，酷工作，二手交易等结点
<div><img src="./img/v2ex.jpg" width="50%"></img></div>

### 3. B 站排行榜
> 可以设置分区，包括数码区，知识区，舞蹈区，鬼畜区，生活区，点击后打开哔哩哔哩 APP
<div><img src="./img/bilibili.jpg" width="50%"></img></div>

### 4. 知乎热榜
<div><img src="./img/zhihu.jpg" width="50%"></img></div>

### 5. 虎扑步行街
<div><img src="./img/hupu.jpg" width="50%"></img></div>

### 6. 重邮教务在线
> 仅限重邮学生使用
<div><img src="./img/jwzx.jpg" width="50%"></img></div>

## 感谢
本仓库脚本均使用下面两个框架进行编写
- [im3x/Scriptables](https://github.com/im3x/Scriptables)
- [2214962083/ios-scriptable-tsx](https://github.com/2214962083/ios-scriptable-tsx)
