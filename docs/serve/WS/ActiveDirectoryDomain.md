为什么要使用域？假设你是公司的系统管理员，你们公司有一千台电脑。如果你要为每台电脑设置登录帐户，设置权限(比如是否允许登录帐户安装软件)，那你要分别坐在这一千台电脑前工作。如果你要做一些改变，你也要分别在这一千台电脑上修改。相信没有哪个管理员想要用这种不吃不喝不睡觉的方式来工作，所以就应运而生了域的概念。
下面列出了域的几个主要概念：
# Active Directory 域配置
这里我使用windows server 2012 r2 搭建域服务器。
第一步：添加角色功能=>安装’Active Directory域服务’，接着一路下一步，安装完即可。
 注：（1）最好使用Administrator来安装，要不可能会因为没有目录权限而安装失败。
    （2） 加入域不能使用Home版的Windows操作系统（顾名思义它是给你在家用的，而你家里是不用搭建域的）。
    （3） 域控制器不能使用web edition server，因为它没有安装活动目录。
第二步：配置服务器的ip地址
第三步：开始配置域服务
第四步：创建域用户及在域下可以创建用户，组织单位，联系人等。
第五步：加入到域中
右键我的电脑=>属性=>高级系统设置=>计算机名页签=>计算机名或域更改，进入这个页面后，你的电脑应该属于一个工作组，这里隶属于我们选择域，并输入test.cn,完事点确定，不出意外肯定会报这个错误。
## Active Directory 域（Domain）
**AD的全称是Active Directory**：活动目录
**域（Domain）**:
1)域是Windows网络中独立运行的单位，域之间相互访问则需要建立信任关系(即Trust Relation)。信任关系是连接在域与域之间的桥梁。当一个域与其他域建立了信任关系后
2)两个域之间不但可以按需要相互进行管理，还可以跨网分配文件和打印机等设备资源，使不同的域之间实现网络资源的共享与管理，以及相互通信和数据传输
## Active Directory 域控制器（DC）
域控制器就是一台服务器，负责每一台联入网络的电脑和用户的验证工作。
## Active Directory 组（group）
组主要用于权限设置，组可以包含用户、计算机、本地服务器上的共享资源、单个域、域目录树或目录林。
组在AD中可以理解为权限目录，它指定了用户在AD中所具有的一些属性，也可以理解为权限的集合。
 组织单元是域中包含的一类目录对象如用户、计算机和组、文件与打印机等资源。是一个容器。组织单元还具有分层结构可用来建立域的分层结构模型，进而可使用户把网络所需的域的数量减至最小（这点应该很好理解了吧，组织单元的分层肯定要比森林方便管理吧^_^）。组织单元具有继承性，子单元能够继承父单元的acl。同时域管理员可授予用户对域中所有组织单位或单个组织单位的管理权限。就像一个公司的各个部门的主管，权力平均化能更有效的管理
## Active Directory 组织单元（OU）
组织单元是域中包含的一类目录对象如用户、计算机和组、文件与打印机等资源，是一个容器，可以在OU上部署组策略
## Active Directory 用户名服务器名（CN）
Active Directory用户账户bai用于验证用户身份，指派用户的访问权限。用户必须使用用户账户登录到特定的计算机和域。登录到网络的每个用户应有自己的惟一账户和密码。用户账户也可用作某些应用程序的服务账户。
在域控制器上建立的是域用户账户，账户数据存储在AD中，用来登录域、访问域内的资源。非域控制器的计算机上还有本地账户。本地账户数据存储在本机中，不会发布到AD中，只能用来登录账户所在计算机，访问该计算机上的资源。本地账户主要用于工作组环境，对于加入域的计算机来说，一般不再建立和管理本地账户，除非要以本地账户登录。