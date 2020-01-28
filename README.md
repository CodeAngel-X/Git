# Git #
Git操作

1. 原理 
![原理图](https://app.yinxiang.com/FileSharing.action?hash=1/fdc20d9adc5b4db7b84f1d8bf5cda400-124524)
2. git下载
[ https://git-scm.com   ]( https://git-scm.com    "git下载")
3. git注册登录

## 从git克隆仓库到本地：git→本地 ##
 
- github创建仓库（repositories）：设置时默认创建read.md ，可预设格式（如java）
-  github创建ssh密钥：
1. 在本地创建工作区（文件夹），然后右键-git bash here ；
2. 在弹出的窗口输入 $ ssh-keygen -t rsa -b 4096 -C "your_ emai L@example. com"，连续回车
3. 继续输入 ssh/id rsa. pub，没有报错即成功 
4. 终端中有公共密钥和私有密钥的路径， 路径里找到 .ssh 目录，里面有 id_rsa 和 id_rsa.pub 两个文件，这两个就是SSH Key 的秘钥对，id_rsa 是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。用记事本打开 id_rsa.pub（C:\Users\Administrator\.ssh），复制ssh key 公钥。
![](https://app.yinxiang.com/FileSharing.action?hash=1/24b6d915a59dfee89019d303e78c5419-669636)
5.回到github，点击头像找到![](https://app.yinxiang.com/FileSharing.action?hash=1/9dac63bc74e47157ca16687ca5e99c13-1708)并点击，再点击左边的![](https://app.yinxiang.com/FileSharing.action?hash=1/919e991fa966fb22cc24474d7add34b7-2908)，点击右边的![](https://app.yinxiang.com/FileSharing.action?hash=1/889a54dc56993a9c02b1019845823d35-2570)
![](https://app.yinxiang.com/FileSharing.action?hash=1/6c9c0896c97abe12338cad63fcefdf7e-111355)


- 写好title，黏贴刚刚得到的密钥，生成SSH密钥
![](https://app.yinxiang.com/FileSharing.action?hash=1/b2c69f96a4a11a4501c94d381e255d23-142743)

###克隆仓库###
- 回到刚刚新建的仓库，点击clone，点击use ssh，复制链接
![](https://app.yinxiang.com/FileSharing.action?hash=1/5aff055aef1a059451c7904967c0b36b-130705)
- 在刚刚打开的gitbash窗口，输入 $  git clone +  刚刚复制的链接，回车，克隆成功！

##本地上传文件到github：本地→github##

1. *在本地工作区中右键-git bash here ；*
2. 输入 $ git status  查看状态，其中untracked files 下的内容是未提交到git的文件
![](https://app.yinxiang.com/FileSharing.action?hash=1/0e9351aea39e901789609cedb9c6f0ed-652455)
3. **上传跟踪项目文件夹中的所有文件和文件夹  ：**
        输入  $ git add . 
           上传文件： 
          输入  $ git add xxx.txt
4. **绑定github账号：**
          输入 $ git config --global user . email "you@example. com 和
                  $ git config-g lobal user. name Your Name" 


5. **commit :**
          输入  $ git commit -m ' XXXX文件描述' 
6. **push ：**
          输入  $git push，成功上传

##解决冲突##
*git push时若提醒非最新版本，如下图：*
![](https://app.yinxiang.com/FileSharing.action?hash=1/c22ad78f2c500bf8969f6316bc788ec3-449038)
*则需要解决冲突，输入git pull ，会提示哪个冲突文件已经合并*
![](https://app.yinxiang.com/FileSharing.action?hash=1/60ad616c74a135e518e5a3670e7ebed4-303478)
*git status会提示你可以做两个操作，一个是解决冲突conflg后commit提交，一个是合并git merge*
![](https://app.yinxiang.com/FileSharing.action?hash=1/75baefef360463d84319022fd5618b71-48662)
*打开冲突文件，可以看到多了冲突内容，只要删除红框内容保存文件即为解决冲突，按正常流程add →commit→ push即可*
![](https://app.yinxiang.com/FileSharing.action?hash=1/04c3ebd87b3f7d212730d5f2d1157326-58836)
*如果是合并，输入git merge +目标分支，即把目标分支合并到当前分支上
git merge 以后先git pull 拉取一下最新数据 ，最后git push，
如git merge 的分支没有在本地上(如下图提示)，可以输入git merge origin/被拉取的非本地分支名称*
![](https://app.yinxiang.com/FileSharing.action?hash=1/b393cc2dc8c673f42b1c933486876ef4-12927)
##工作流##
 
1. 创建分支 ：输入git branch 分支名称
2. 更改分支到当前分支上：输入gir checkout  分支名称 
3. 以上步骤可以合并到一个命令：输入git checkout -b 分支名称
4. add →commit→ push 后，push提示需要在远程生成branch，输入 git push -- set-upstream origin 分支名称，即可同时提交和创建远端新分支
![](https://app.yinxiang.com/FileSharing.action?hash=1/356425cb506d3f66c212543954c7c24a-30314)
**用ｉｄｅ解决冲突**
![](https://app.yinxiang.com/FileSharing.action?hash=1/066bc341a4468e7edbf7daeb7242711f-1244210)
*ｉｄｅ的terminal　对比修改分支内容，并且保存，较传统方式更为直观*
##其他操作##
1. .日志查询：
           输入 $ git log  
2.可以看到某commit id做了什么：
           输入 $ git show + 日志中的commit id 
3. 重置commit 操作：
           输入 $ git reset  + 日志中的commit id
4. 查看本地和git仓库的状态：
           输入 $ git status