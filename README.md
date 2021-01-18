# 快速使用
1. iPhone 上下载 [Scriptable](https://apps.apple.com/cn/app/scriptable/id1405459188) App（确保你的系统已更新为 iOS14+）    
2. 复制下列代码，在Scriptable中新建脚本，并将其粘贴进去，运行即可一键安装你需要的脚本，你只需要修改其中的Scripts数组
```js
const FILE_MGR = FileManager[module.filename.includes('Documents/iCloud~') ? 'iCloud' : 'local']();
// 输入你想安装的脚本，点击运行即可安装
const Scripts = [
  '知乎热榜.js',
  '微博热搜.js',
  'V2EX.js',
  '步行街热帖.js'
]
await Promise.all(Scripts.map(async js => {
  const REQ = new Request(`https://gitee.com/ourongxing/Scriptables/raw/main/${encodeURIComponent(js)}`);
  const RES = await REQ.load();
  FILE_MGR.write(FILE_MGR.joinPath(FILE_MGR.documentsDirectory(), js), RES);
}));
FILE_MGR.remove(module.filename);
```


