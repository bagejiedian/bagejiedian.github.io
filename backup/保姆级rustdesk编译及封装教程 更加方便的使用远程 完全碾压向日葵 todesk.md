编译Rustdesk客户端
一、fork Rustdesk的客户端的项目
https://github.com/rustdesk/rustdesk
fork到仓库里
Actions 同意
二、利用Github Actions在线编译
找到完整工作流
Full Flutter Cl
开始工作流 取消工作流

三、填入我们服务器信息及key再次编译
路径：rustdesk/libs/hbb_common/src/config.rs

大概在103行左右
填写ip key
修改好后点保存 

四、修改让源码编译后，自动上传客服端供给我们下载
路径：.github/workflows/flutter-ci.yml
改为true

五、重新开启编译
编译完成，滑到最下面可以看到我们编译好的客户端了

六、Windows客户端封装为一个EXE文件
需要用到winrar老牌的解压软件
https://www.winrar.com.cn/
1.选择所有文件添加到压缩文件
2.勾选“创建自解压格式压缩文件”
3.选择“高级”选项卡，单击“自解压选项按钮”
4.在“设置”选项卡中，“解压后运行”一栏填上解压后运行的文件
5.在“模式”选项卡中，选中“解压到临时文件夹”和“全部隐藏”
6.在“更新”选项卡中，选中“覆盖所有文件”
7.在“文本和图标”选项卡中，在“加载自解压文件图标”处，选择我们自己制作好的ICON图标

