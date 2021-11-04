# 嵌入式笔记
记录嵌入式开发过程中的笔记
## CAN总线协议
[CAN详解](https://blog.csdn.net/XiaoXiaoPengBo/article/details/116206252?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522163409383916780274162903%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=163409383916780274162903&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-3-116206252.pc_search_result_control_group&utm_term=can&spm=1018.2226.3001.4187)
## 解决github图片不显示的问题
解决方法，打开路径C:\Windows\System32\drivers\etc下的hosts文件，在最后加上下一段代码

    # GitHub Start 
    151.101.184.133    assets-cdn.github.com
    151.101.184.133    raw.githubusercontent.com
    151.101.184.133    gist.githubusercontent.com
    151.101.184.133    cloud.githubusercontent.com
    151.101.184.133    camo.githubusercontent.com
    151.101.184.133    avatars0.githubusercontent.com
    151.101.184.133    avatars1.githubusercontent.com
    151.101.184.133    avatars2.githubusercontent.com
    151.101.184.133    avatars3.githubusercontent.com
    151.101.184.133    avatars4.githubusercontent.com
    151.101.184.133    avatars5.githubusercontent.com
    151.101.184.133    avatars6.githubusercontent.com
    151.101.184.133    avatars7.githubusercontent.com
    151.101.184.133    avatars8.githubusercontent.com
    # GitHub End
加完后，再删除，也会生效，原因不明。
