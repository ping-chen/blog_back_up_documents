Unity3d 5.0 正式上线了。
最近项目一直在弄资源管理这块。
刚好赶在这个点，我就去下载看看new asset bundle system。

介绍视频在这里：
https://www.youtube.com/watch?v=gVUgF2ZHveo&index=18&list=PLX2vGYjWbI0RP5YmvwgqgJQrHGul-Tnr_
考虑到没有fq能力的同学，我上传到360的网盘上：
http://yunpan.cn/cJ9IYTq9GMdyW
访问密码 9adb

文字介绍在这里：
http://forum.unity3d.com/threads/new-assetbundle-build-system-in-unity-5-0.293975/

里面有详细的介绍，还有一个demo

所以这篇文章，不是来介绍asset bundle system，而且记录一些我遇到的注意事项。

一、
打包成图集的图片，都放在同一个asset bundle里。要不然会导致打包成多个图集，dc就变大了。

二、
new asset bundle system帮我们做好了依赖关系，所以我们加载也要把依赖加载好，代码可参考文字介绍里的demo


后续发现问题，会在这里持续更新。谢谢！