用于规范Swift书写，安装之后对于项目中一些规则方面的错误会提出警告，可以使得我们书写swift的时候更加规范

官方文档
https://github.com/realm/SwiftLint/blob/master/README_CN.md
1.在终端复制粘贴一下代码【逐行】
cd ~/Downloads (存放在任何地方都可以) git clone https://github.com/realm/SwiftLint.git cd SwiftLint git submodule update --init --recursive; make install
2.打开项目->TARGETS->Bulid Phases
3.点击左上加号按钮，点击New Run Script Phase
4.在Run Script项目中添加以下内容
5.最后运行：⌘+B
if which swiftlint >/dev/null; then
swiftlint
else
echo "warning: SwiftLint not installed, download from https://github.com/realm/SwiftLint"
fi
![](https://github.com/roycehe/SwiftLint/blob/master/QQ20161128.png)


