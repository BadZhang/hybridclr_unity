# 发布日志

## 3.3.1

发布日志 2023.07.17。

### Runtime

- [version] 支持2021.3.28和2022.3.4版本
- [opt] 删除MachineState::InitEvalStack分配_StackBase后不必要的memset
- [fix] 修复Exception机制的bug
- [fix] 修复CustomAttribute不支持Type[]类型参数的bug
- [fix] 修复不支持new string(xxx)用法的问题
- [refactor] 重构VTableSetup实现
- [fix] 修复未计算子interface中显式实现父interface的函数的bug

### Editor

- [fix] 修复计算桥接函数未考虑到泛型类的成员函数中可能包含的Native2Managed调用
- [change] link.xml及AOTGenericReferences.cs默认输出路径改为HybridCLRGenerate，避免与顶层HybridCLRData混淆
- [fix] 修复Win下生成的Lump文件中include路径以\为目录分隔符导致同步到Mac后找不到路径的bug
- [refactor] 重构Installer


## 3.3.0 

发布日期 2023.07.03。

### Runtime

- [fix] 修复localloc分配的内存未释放的bug
- [change] MachineState改用RegisterRoot的方式注册执行栈，避免GC时扫描整个堆栈
- [opt] 优化Managed2NativeCallByReflectionInvoke性能，提前计算好传参方式
- [refactor] 重构ConvertInvokeArgs

### Editor

- [fix] 修复2020-2021编译libil2cpp.a未包含brotli相关代码文件导致出现编译错误的bug
- [fix] 修复从导出xcode项目包含绝对路径导致传送到其他机器上编译时找不到路径的bug
- [fix] 解决Generate LinkXml、 MethodBridge、AOTGenericReference、ReversePInvokeWrap 生成不稳定的问题
- [fix] 修复使用不兼容版本打开Installer时出现异常的bug
- [change] 禁用hybridclr后打包ios时不再修改导出的xcode工程

## 3.2.1

### Runtime

- [fix] 修复il2cpp TypeNameParser未将类型名中转义字符'\'去掉，导致找不到嵌套子类型的bug

### Editor

- [new] Installer界面新增显示package版本
- [new] CompileDll新增MacOS、Linux、WebGL目标
- [fix] 修复重构文档站后的帮助文档的链接错误
- [change] 为Anaylizer加上using 限定，解决某些情况下与项目的类型同名而产生编译冲突的问题

## 3.2.0

### Runtime

- [fix] 修复未在PlaceHolder中的Assembly加载时，如果由于不在Assembly列表，也没有任何解释器栈，导致Class::resolve_parse_info_internal查找不到类型的bug
- [fix] 修复读取CustomAttribute System.Type类型数据崩溃的bug

### Editor

- [new] 支持直接从源码打包iOS，不再需要单独编译libil2cpp.a
- [opt] 优化版本不兼容时错误提示，不再抛出异常，而是显示"与当前版本不兼容"


## 3.1.1

### Runtime

- [fix] 修复2021及更高版本，InterpreterModule::Managed2NativeCallByReflectionInvoke调用值类型成员函数时，对this指针多余this=this-1操作。
- [fix] 修复解析CustomAttribute中Enum[]类型字段的bug
- [fix] 修复2021及更高版本反射调用值类型 close Delegate的Invoke函数时未修复target指针的bug
- [new] 新增对增量式GC宏的检查，避免build.gradle中意外开启增量式GC引发的极其隐蔽的问题

### Editor

- [fix] 修复 Win32、Android32、WebGL平台的编译错误
- [fix] 修复计算桥接函数时未考虑到补充元数据泛型实例化会导致访问到一些非公开的函数的情况，导致少生成一些必要的桥接函数
- [opt] 生成AOTGenericReferences时，补充元数据assembly列表由注释改成List<string>列表，方便在代码中直接使用。
- [change] CheckSettings中不再自动设置Api Compatible Level

## 3.1.0

### Runtime

- [rollback] 还原对Unity 2020.3.x支持
- [fix] 修复 WebGL平台ABI的bug

### Editor

- [rollback] 还原对Unity 2020.3.x支持

## 3.0.3

### Runtime

- [fix] 修复Enum::GetValues返回值不正确的bug

## 3.0.2

### Runtime

- [fix] 修复Memory Profiler中创建内存快照时崩溃的bug

### Editor

- [remove] 移除 `HybridCLR/CreateAOTDllSnapshot`菜单


## 3.0.1

### Runtime

- [new] 支持2022.3.0

## 3.0.0

### Runtime

- [fix] 修复不支持访问CustomData字段及值的bug
- [remove] 移除对2019及2020版本支持

### Editor

- 包名更改为com.code-philosophy.hybridclr
- 移除UnityFS插件
- 移除Zip插件
- HybridCLR菜单位置调整

## 2.4.2

### Runtime

- [version] 支持 2020.3.48，最后一个2020LTS版本
- [version] 支持 2021.3.25

## 2.4.1

### Runtime

### Editor

- [fix] 修复遗漏 RELEASELOG.md.meta 文件的问题

## 2.4.0

### Runtime

### Editor

- [new] CheckSettings中检查ScriptingBackend及ApiCompatibleLevel，切换为正确的值
- [new] 新增 MsvcStdextWorkaround.cs 解决2020 vs下stdext编译错误的问题
- [fix] 修复当struct只包含一个float或double字段时，在arm64上计算桥接函数签名错误的bug

## 2.3.1

### Runtime

### Editor

- [fix] 修复本地复制libil2cpp却仍然从仓库下载安装的bug

## 2.3.0

### Runtime

### Editor

- [new] Installer支持从本地目录复制改造后的libil2cpp
- [fix] 修复2019版本MonoBleedingEdge的子目录中包含了过长路径的文件导致Installer复制文件出错的问题


