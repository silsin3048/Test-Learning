### 1、设置全局断点，修改HTTP请求：
①设置全局断点：单击菜单栏中的Rules=》Automatic Breakpoint =》Before Requests（或使用快捷键F11）；
②取消全局断点：单击菜单栏中的Rules=》Automatic Breakpoint =》Disabled（或使用快捷键Shift+F11）。
### 2、设置单个断点，修改HTTP请求：
①设置单个断点：在Fiddler左下角的QuickExec命令行中输入命令“bpu www.baidu.com”，这种方法只会拦截www.baidu.com；
②取消单个断点：在命令行中输入“bpu”。
### 3、设置全局断点，修改HTTP响应：
①设置全局断点：单击菜单栏中的Rules=》Automatic Breakpoint =》After Response（或使用快捷键Alt+F11）；
②取消全局断点：单击菜单栏中的Rules=》Automatic Breakpoint =》Disabled（或使用快捷键Shift+F11）。
### 4、设置单个断点，修改HTTP响应：
①设置单个断点：在Fiddler左下角的QuickExec命令行中输入命令“bpafter www.baidu.com”，这种方法只会拦截www.baidu.com；
②取消单个断点：在命令行中输入“bpafter”。