chromedirver 去特征标识版本

windows - 以后有时间去编译，也可以查看github某位大佬的产物[https://github.com/xjoker/ChromeDriver]   ps：但多开chrome下会造成线程混乱。。。


linux - 版本不全，有时间补齐




chromeium编译指南 google官方：https://chromium.googlesource.com/chromium

chromedriver tag大全：https://chromium.googlesource.com/chromium/src/+refs

切换版本tips：
 进入src目录执行： 
   //如果改过文件请执行git放弃
   git reset --hard
   //同步版本标识 可忽略
   gclient sync --with_branch_heads --with_tags
   //版本  可忽略  直接从上面的链接拿到版本tag
   git fetch --tags
   //同步版本
   git checkout -b ChromeDriver tags/84.0.4147.85
   //同步源码
   gclient sync --with_branch_heads --with_tags

//设置gn
gn gen out/Release --args="is_debug=false"
//编译
ninja -C out/Release chromedriver -j16


//driver检测特征cdc在src\chrome\test\chromedriver\js\call_function.js