
5. SSH(secure shell):一种让你的电脑通过网络“安全地登录/连接另一台电脑或服务器”的协议。
    (1)原因:可以配置密钥；电脑->SSH密钥->git服务器


4. 网址转换成git:git@服务器:用户名/仓库名.git
    例子:        https://git.nju.edu.cn/nju-se-oslab/oslab2026autumn
        ssh地址:     git@git.nju.edu.cn:nju-se-oslab/oslab2026autumn.git   
        所以:git remote add upstream git@git.nju.edu.cn:nju-se-oslab/oslab2026autumn.git

3. 如果我fork一个项目，然后原项目更新了，但我已经有了很多branch该怎么办？
    (1)方法  1.git remote -v;先确定main有没有upstram;如果没有，则添加git remote add upstream git@github.com:A/project.git
            2.git fetch upstream；获取原项目最新提交，这样main就更新了，
            3.git push；获取完commit后push 到origin远程分支上
            3.git switch week2;切换其他branch
            4.git merge upstream/main ；让其他分支也merge
            5.git push;把week2推送



2. 在本地建立一个仓库week2后，进行git push,然后报错;
    (1)原因：还没有建立远方仓库
    (2)方法:git push --set-upstram origin week2；用于追踪gitlab中的仓库，以后也能pull

1. 为什么电脑显示：引用的账户已被锁定，输入正确密码也没用
    方法一：等30min，重新输入密码即可
