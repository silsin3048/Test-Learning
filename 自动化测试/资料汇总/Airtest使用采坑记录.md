1、Airtest IDE连接安卓模拟器adb连接失败（使用夜神）
由于夜神模拟器的adb版本和Airtest IDE版本中的adb版本不一致，连接不上，需要将Airtest IDE中的adb.exe（相对路径：\airtest\core\android\static\adb\windows）替换掉夜神模拟器 安装目录bin下面的nox_adb.exe，重新启动夜神模拟器，尝试连接
2、Airtest IDE连接安卓模拟器黑屏
官方文档：模拟器可以像真机一样连接到AirtestIDE中，如果画面显示为黑屏，请在连接模拟器之前，勾选connect按钮下拉菜单里的 Use javacap 选项，然后再点击connect按钮进行连接。