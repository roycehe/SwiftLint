



用于规范Swift书写，安装之后对于项目中一些规则方面的错误会提出警告，可以使得我们书写swift的时候更加规范。

官方文档
https://github.com/realm/SwiftLint/blob/master/README_CN.md
1.在终端复制粘贴一下代码【逐行】
cd ~/Downloads (存放在任何地方都可以)
git clone https://github.com/realm/SwiftLint.git
cd SwiftLint
git submodule update --init --recursive; make install
2.打开项目->TARGETS->Bulid Phases
3.点击左上加号按钮，点击New Run Script Phase
4.在Run Script项目中添加以下内容
5.最后运行：⌘+B
if which swiftlint >/dev/null; then

swiftlint

else

echo "warning: SwiftLint not installed, download from https://github.com/realm/SwiftLint"

fi
配置
可以通过在你需要执行 SwiftLint 的目录下添加一个 .swiftlint.yml 文件的方式来配置 SwiftLint。可以被配置的参数有：

* disabled_rules: 关闭某些默认开启的规则.
* opt_in_rules: 一些规则是可选的.
* whitelist_rules: 不可以和 disabled_rules 或者 opt_in_rules 并列。类似一个白名单，只有在这个列表中的规则才是开启的。
包含的规则:

disabled_rules: # 执行时排除掉的规则
  - colon
  - comma
  - control_statement
opt_in_rules: # 一些规则仅仅是可选的
  - empty_count
  - missing_docs
  # 可以通过执行如下指令来查找所有可用的规则:
  # swiftlint rules
included: # 执行 linting 时包含的路径。如果出现这个 `--path` 会被忽略。
  - Source
excluded: # 执行 linting 时忽略的路径。 优先级比 `included` 更高。
  - Carthage
  - Pods
  - Source/ExcludedFolder
  - Source/ExcludedFile.swift

# 可配置的规则可以通过这个配置文件来自定义
# 二进制规则可以设置他们的严格程度
force_cast: warning # 隐式
force_try:
  severity: warning # 显式
# 同时有警告和错误等级的规则，可以只设置它的警告等级
# 隐式
line_length: 110
# 可以通过一个数组同时进行隐式设置
type_body_length:
  - 300 # warning
  - 400 # error
# 或者也可以同时进行显式设置
file_length:
  warning: 500
  error: 1200
# 命名规则可以设置最小长度和最大程度的警告/错误
# 此外它们也可以设置排除在外的名字
type_name:
  min_length: 4 # 只是警告
  max_length: # 警告和错误
    warning: 40
    error: 50
  excluded: iPhone # 排除某个名字
variable_name:
  min_length: # 只有最小长度
    error: 4 # 只有错误
  excluded: # 排除某些名字
    - id
    - URL
    - GlobalAPIKey
reporter: "xcode" # 报告类型 (xcode, json, csv, checkstyle)

