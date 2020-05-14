
**管理员快速上手**

SmartCMP主要有两种服务场景，其一是云资源蓝图服务场景；其二是工单服务场景。
+	云资源蓝图服务场景
云资源蓝图服务基于蓝图建模来定义标准的服务框架与组件，提供丰富的开箱即用的软件组件，以可视化的形式编排蓝图，实现自动化部署。
例如：配置一项vSphere单节点虚拟机服务是云资源蓝图服务的典型场景。
管理员经过蓝图建模之后，通过服务配置指定用户可以申请使用的资源、参数，形成基于蓝图的标准服务，发布后用户可以自助申请，自动化交付。

+	工单服务场景
工单服务分为两种类型：
1.	申请非标准化资源的服务（例如：为了卸除某项服务部署，申请云资源蓝图服务，申请此项云资源服务的操作是工单服务的典型服务场景）
2. 需要IT人工介入的服务（例如：申请重新设置密码的手工工单服务，申请此项手工工单服务也是工单服务的典型服务场景）
支持管理员定义标准工单服务、通过服务配置指定服务流程和服务团队再发布服务、通过服务目录进行服务申请，服务团队接收服务工单，进行工单处理操作。

>「Note」配置更多云资源蓝图服务请您参考[快速配置云资源蓝图服务](#快速配置云资源蓝图服务)，工单服务详细介绍，请您参考[手工工单服务管理](https://cloudchef.github.io/doc/AdminDoc/08工单服务管理/)


管理员初次使用系统发布服务，需要做如下操作以配置系统：

1.  配置云平台入口：如vSphere、OpenStack的管理员登录信息

2.  添加IP池：定义可用的IP地址范围

3.  定义资源池：配置可使用的物理资源，并设置配额，例如CPU、内存、存储、网络等

4.  定义业务组，关联人员、资源池，配置审批流程、部署规范等

5.  定义虚拟机模板：选择云平台和对应的模板或镜像

6.  定义蓝图：定义服务的架构及自动化安装逻辑

7.  配置并发布服务：关联蓝图到业务组及资源池，并配置部署参数，例如选择虚拟机模板等

8.  申请服务：服务目录里申请服务，也可以在「组织架构」-「业务组」中启用业务组的向导式申请功能，直接开始向导式部署

9.  自助运维：在「我的部署」菜单栏中查看服务部署、云主机或云资源的详细信息，并进行自助运维操作

接下来的章节将介绍如何建立自己第一个云资源，发布并申请服务。您可以根据[快速配置云资源蓝图服务](#快速配置云资源蓝图服务)，配置多种类型的云资源蓝图服务。

# 登录系统


+ 浏览器输入SmartCMP的IP，例如：http://cmp.smartcmp.online:1688/#/login
+ 输入用户名和密码。

# 配置云平台入口


云平台入口定义了SmartCMP纳管的公有云、私有云、容器或物理机的云基础设施资源。不同云基础设施账号的形式及获取方式各有不同，管理员可以通过填写对应的基础设施的访问信息完成云平台基础设施的注册。

>「Note」请使用租户管理员或基础设施管理员登录SmartCMP平台。公有云的访问信息获取方式，请您参考[添加阿里云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加阿里云平台)

## 添加vSphere云平台

1.  进入「基础设施」-「云平台管理」，选择「vSphere」，点击「添加」

2.  输入所需参数(请根据自己的真实环境输入相关参数，示例只给出参考)

|参数名称 |描述 |示例|
|:------:|:------:|:-----:|
|云名称|vSphere云平台名称|数据中心A--vCenter|
|用户名|vSphere用户名|administrator\@vsphere.local|
|密码| vSphere密码 |确认密码 |                        
|地址|vSphere API URL |192.168.xx.xx|
|端口|API端口|443|
|数据中心|数据中心所在地|上海|
|关联VMware NSX云平台|NSX云平台（需先添加VMware平台）|选择对应的NSX云平台名称|


3.  点击「验证」，验证连接vSphere虚拟化平台；若输入参数错误，则提示配置错误；若配置正确，则提示验证连接成功

4.  验证成功后，点击「提交」，vSphere虚拟化平台连接成功

## 添加OpenStack云平台

1.  进入「基础设施」-「云平台管理」，选择「OpenStack」，点击「添加」

2.  输入所需参数(请根据自己的真实环境输入相关参数)


|参数名称|   描述|                        示例|
|:------:|:------:|:-----:|
|云名称 |    OpenStack云平台名称|         OpenStack|
|认证URL|    OpenStack keystone认证URL|   http://xxx.xxx.xxx.x:500/v2|
|API版本 |   选择API版本：版本2 版本3|    版本2|
|租户名称 |  租户名称 | admin|
|用户名|     用户名|   admin|
|密码|       密码 | 确认密码|     
|区域|     区域名称 |   RegionOne|
|数据中心|   数据中心所在地| 上海|

3.  点击「验证」，验证连接OpenStack虚拟化平台；若输入参数错误，则提示配置错误；若配置正确，则提示验证连接成功

4.  验证连接成功后，点击「提交」, OpenStack云平台入口已保存

## 添加阿里云平台

您可以根据下面的步骤来添加一个阿里云平台：

1.  在左边导航选择「基础设施」-「云平台管理」，在左边选择「阿里云」类型

2.  点击「添加」按钮，填入下列信息：

|参数名称|描述  |示例|
| :------:|:------:|:-----:|
|云名称|       阿里云云平台名称|   Aliyun|
|访问密钥ID|   阿里云访问密钥ID|   获取方式请参考接入云平台|
|访问密钥|     阿里云访问密钥  |   获取方式请参考接入云平台|

3.  点击「验证」，验证连接成功后，点击「提交」, 阿里云平台入口已保存

# 添加IP池


管理员可在SmartCMP中配置IP池，管理IP地址段，并可在IP池中查看IP地址使用情况，可占用以及释放被占用的IP地址。

1.  用户可以根据需要对IP池进行添加，选择「基础设施」-「IP地址管理」，点击「添加」，选择IP池（还支持F5
    BIG-IP、ACI IP池），进入创建IP池页面

2.  在「概况」页面：输入名称、描述（选填）、CIDR、网关等

3.  点击「IP范围」菜单，IP范围下点击「添加」：在创建IP范围页面输入名称，起始IP和结束IP，点击「提交」，IP范围创建成功。在列表下方可看到IP范围内的IP地址的状态（可用、已占用、预留、冷却中），可进行释放和占用操作。

4.  点击「保存」，IP池创建成功

>「Note」IP池的起始ID应大于等于CIDR，IP池的结束IP应大于起始IP

# 定义资源池


SmartCMP可通过定义资源池来将一个云平台中的资源映射到多个逻辑单元中，并配置到不同的组织架构，从而指定不同的组织和用户使用该云平台中的基础设施资源，包括计算、存储和网络资源等。一个云平台可以定义一个资源池，也可以定义多个资源池。

定义该资源池和业务组的关联关系,资源的共享情况分为三种：

1.  资源池仅分配给唯一的业务组，操作方法：不选择「允许共享给多个业务组」，点击「业务组」选择该业务组

2.  资源池分配给所有的业务组，并且新增的业务组自动关联该资源池，操作方法：选择「允许共享给多个业务组」，点击「业务组」选择全部业务组

3.  资源池共享给多个业务组，操作方法：选择「允许共享给多个业务组」，单价「业务组」选择相应的多个业务组

创建资源池的步骤如下：

>「Note」请使用租户管理员或基础设施管理员角色登录SmartCMP平台。

## 添加vSphere资源池

1.  进入「基础设施」-「资源池管理」，点击「添加」，选择vSphere，填写下列信息：

2.  「基本信息」页面：

 + 基本信息：名称，资源标签（选填），优先级（数值越小，优先级越高），

  + 云平台资源信息：选择云平台入口（选择刚创建的vSphere云平台），资源入口，文件夹（选填）

3.  「基本信息」页面加载成功后点击「计算资源」：

  + 资源入口信息：仅查看

  + 物理主机信息：仅查看

  + 计算资源：vCPU数量（上限），内存（上限），虚机数量（上限），每台虚拟机允许快照数量（上限）

  + 存储：选择存储及其预留空间

4.  「网络资源」页面：

  + 网络资源：选择某一网络，IP分配方式选择IP池，并在「IP地址管理」栏下选择新建的IP池

  + 分布式虚拟交换机：默认

5.  点击「保存」，保存后在资源池列表出现刚添加成功的vSphere资源池

## 添加OpenStack资源池

1.  进入「基础设施」-「资源池管理」，点击「添加」，选择OpenStack，填写下列信息：

2.  「基本信息」页面：

  + 基本信息：名称，业务组、是否共享给多个业务组、资源标签（选填），优先级

  + 云平台资源信息：选择云平台入口（选择刚创建的OpenStack云平台）、可用区（选择云平台后出现）、DNS域（选填）

>「Note」域名由根域名、顶级域、二级、三级等多级域名构成，每级域名由字母、数字和连字符(-)构成(第一个字符不能是连字符)，不区分大小写，长度不超过63个字符。一个完整域名总长度不超过255个字符，必须以点结尾。配置资源池DNS域前请先配置租户中的DNS域。

业务组关联情况请参考

3.  「基本信息」加载成功后点击「计算资源」：

  + 资源信息：仅查看

  + 计算资源：vCPU数量（上限），内存（上限），存储（上限），虚机数量（上限），浮动IP数量（上限）

4.  「网络资源」

  + 「网络资源」：选择网络及对应的子网、IP分配方式选择IP池，并在「IP池」栏下选择刚创建的IP池

  + 「安全策略组」：选择一个或多个安全策略组

  + 「防火墙」：选择一个或多个防火墙

5.  「路由」：可选

6.  点击「保存」，保存后在资源池列表出现刚添加成功的OpenStack资源池

## 添加阿里云资源池

您可以根据下面的步骤来添加阿里云资源池:

1.  进入「基础设施」-「资源池管理」，点击「添加」，选择阿里云，填写下列信息：

2.  「基本信息」页面：

  + 基本信息：名称，是否共享给多个业务组、资源标签（选填），优先级（数值越小，优先级越高）

  + 云平台资源信息：选择云平台入口（阿里云云平台）、区域以及可用区（选择区域后出现对应的可用区，可多选）、网络类型（经典网络/专有网络）

3.  「基本信息」加载成功后点击「计算资源」：vCPU数量（上限），内存（上限），虚机数量（上限）

4.  「付费方式」：选择预付费或后付费

预付费：预付费是指您需要先付费才能使用资源。根据计费周期不同，预付费可以分为：

  + 按周付费：计费周期为一周

  + 包年包月：计费周期为月或年

选择预付费后，请选择购买时长，小至一周，大至5年。可勾选自动续费，按周购买自动续费时长为一周，按月购买自动续费时长为1个月，按年购买自动续费时长为1年

后付费：后付费是指您先使用资源后付费的方式。使用这种方式，您可以按需取用资源，随时开启和释放资源，无需提前购买大量资源。

「网络资源」

「安全策略组」：选择一个或多个安全策略组

「虚拟交换机」：若选择专有网络，可选择虚拟交换机

 点击「保存」，阿里云资源池创建成功

# 定义业务组


业务组是租户内的逻辑组织结构，支持创建多级业务组，用于在SmartCMP系统内对应企业的组织架构。业务组内关联该业务组所属的用户以及该业务组可使用的资源池。

业务组是一个逻辑概念，有需要把用户、服务目录和资源配额联系在一起的实体都可以用业务组来对应，比如子公司，不同层级的部门等。

系统默认创建Default业务组以及租户管理员、业务组管理员和业务组普通用户等。可通过以下步骤分配资源池：

>「Note」如需修改该业务组的设置，或创建新的业务组，请参考 [组织架构](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/)中的详细步骤。

1.  点击左侧导航栏「组织架构」-「业务组」，点击业务组名称（Default）进入编辑页面

2.  「概况」页面，保持默认值

3.  「用户」页面，保持默认值。系统默认设置两个用户，分别为业务组管理员和业务组普通用户

4.  「资源池」页面，点击「添加资源池」，选择上节创建的vSphere资源池和OpenStack资源池，点击「确定」

5.  点击「保存」，业务组与资源池关联成功

6.  为业务组申请资源和服务关联审批流程

7.  为业务组成员配置云资源操作许可和服务部署操作许可

# 定义虚拟机模板


平台支持创建虚拟机模板，一个操作系统可对应多个虚拟机模板，一个虚拟机模板可在多个云平台中使用。虚拟机模板与vSphere平台中的模板或OpenStack平台中的镜像相关联。

在虚拟机模板中可配置SmartCMP两种代理的安装方式和账号信息，这两种代理是监控代理和自动化代理。SmartCMP平台中的一些自动化功能依赖自动化代理，

例如：蓝图带应用部署或添加磁盘，服务配置初始化并挂载磁盘、创建新用户，以及部分虚机运维操作（包括重置密码，执行脚本，应用启动停止，添加、扩展Linux逻辑卷或Windows磁盘等）。

创建虚拟机模板之后，可在服务配置中直接指定。SmartCMP可根据蓝图对象所在的云平台自动识别虚拟机模板。

这里定义两个虚拟机模板：CentOS 7和Windows 2012 R2：

>「Note」请使用租户管理员或基础设施管理员角色登录SmartCMP平台。租户管理员可为某用户指定基础设施管理员角色。系统默认创建了3个虚拟机模板：Windows2012 R2、Redhat 7、CentOS7，还需添加相应的云平台信息才可使用。创建虚拟机模板详见下文 

添加虚拟机模板

## 添加Linux虚拟机模板

1.  选择「基础设施」-「虚拟机模板」，进入虚拟机模板列表界面。该页面默认有2个Linux虚拟机模板，分别为Redhat
    7和CentOS 7

2.  点击「CentOS
    7」，进入虚拟机模板「基本信息」页面，该页面显示操作系统名称、描述、以及系统类型（Linux
    或Windows）

3.  点击「虚拟机模板」标签页，进入虚拟机模板列表界面

## 添加一个vSphere虚拟机模板 {#添加一个vsphere虚拟机模板 .afff6}

1.  点击「添加」，输入模板名称：Linux CentOS 7 on
    vSphere，选择2.2.1节配置的vSphere云平台并做如下配置：

+ 克隆模式：选择「完全克隆」或「链接克隆」

>「Note」完全克隆是和原始虚拟机完全独立的一个拷贝，它不和原始虚拟机共享任何资源，可以脱离原始虚拟机独立使用；链接克隆需要和原始虚拟机共享同一虚拟磁盘文件，不能脱离原始虚拟机独立运行。但采用共享磁盘文件却大大缩短了创建克隆虚拟机的时间，同时还节省了宝贵的物理磁盘空间。

 + 完全克隆
模板，选择一个Linux CentOS 7模板

 + 链接克隆

虚拟机：选择一个Linux CentOS 7的模板；快照模式：默认"指定一个快照"，可选择"申请时候选择"或"总是使用最新"这两种快照模式,
选择"申请时候选择"将在服务申请的时候选择虚拟机快照； 快照：若快照模式选择"指定一个快照"，将选择一个快照；使用规范：选择「内建」（按需求选择无、内建或自定义规范，规范有助于防止在部署相同设置的虚机时而产生冲突）；模板中已启用SSH：勾选该选项，表示模板中已经启用和配置SSH，可以选择通过SSH的方式安装监控代理和自动化代理；默认SSH端口为22，如果模板中修改了SSH的端口，可输入模板中修改的SSH端口号；用户名、密码：若选择启用SSH，填写具有SSH权限的用户及其密码

+ 监控方式：



  + 无监控：若不安装监控代理，则平台的监控功能不可用

  + SSH安装监控代理：选择SSH安装的话，会通过SSH的方式访问虚拟机并安装监控代理；设置监控端口，默认是9100

  + 预安装监控代理：预安装是指模板中已经安装了监控代理

  + 云平台监控：从vCenter上直接读取虚机的监控数据，不需要安装监控代理

+ 安装自动化代理：



  + 不安装：若不安装自动化代理，则平台的一些自动化功能将无法使用，例如蓝图带应用部署或添加磁盘，某些虚拟机的操作如重置密码，执行脚本等

  + SSH安装：选择SSH安装，会通过SSH的方式访问虚拟机并安装自动化代理

  + 预安装：预安装是指模板中已经安装了自动化代理


+ 管理员用户：输入模板中配置的管理员用户名

+ 管理员密码：输入模板中配置的管理员密码

2.  点击「提交」，提示虚拟机模板已创建。点击「保存」，提示虚拟机模板已更新

## 添加一个OpenStack虚拟机模板 {#添加一个openstack虚拟机模板 .afff6}

 点击「添加」，输入虚拟机模板名称Linux CentOS 7 on OpenStack，选择2.2.2节配置的OpenStack云平台并做如下配置：

  + 启动源类型：选择从镜像启动、从快照启动、从云硬盘启动、从云硬盘快照启动
  + 从镜像启动：选择镜像名称和快照模式；快照模式默认为"不使用快照"，可选择"申请时候选择"和"总是使用最新的"。若选择"申请时候选择"将在服务申请时指定虚拟机快照
  + 从快照启动：选择快照名称
  + 从云硬盘启动：选择镜像名称和快照模式；快照模式默认为"不使用快照"，可选择"申请时候选择"和"总是使用最新的"。若选择"申请时候选择"将在服务申请时指定虚拟机快照；若勾选"终止后删除"，将在终止主机后删除硬盘。选择"从云硬盘启动"模式需要在服务配置时选择卷类型和配置卷大小
  + 从云硬盘快照启动：选择云硬盘快照名称，若勾选"终止后删除"，将在终止主机后删除硬盘。选择"从云硬盘快照启动"模式需要在服务配置时选择卷类型和配置卷大小
  + 监控方式和自动化代理的方式：与vSphere的Linux模板相同，可配置SSH端口，此外SSH用户支持密钥方式（可在「基础设施」-「密钥对」中新建密钥或导入密钥）
  + 管理员用户名和密码：输入需要设置的操作系统管理员用户名和密码

点击「提交」，提示虚拟机模板已创建。点击「保存」，提示虚拟机模板已更新此时CentOS7的Linux操作系统，关联了2个虚拟机模板。在[配置服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html)的时候，平台会自动选择与该服务相对应的虚拟机模板，无需重复设置。

## 添加Windows虚拟机模板

1.  选择「基础设施」-「虚拟机模板」，进入虚拟机模板列表界面。该页面默认有1个Windows虚拟机模板，Windows
    2012 R2

2.  点击「Windows 2012 R2」，进入虚拟机模板「基本信息」页面

3.  该页面显示操作系统名称、描述、以及系统类型

4.  点击「虚拟机模板」标签页，进入虚拟机模板列表界面

## 添加一个vSphere虚拟机模板 {#添加一个vsphere虚拟机模板-1 .afff6}

1.  点击「添加」，输入虚拟机模板名称：Windows 2012 R2 onvSphere，选择vSphere云平台并做如下配置：

+ 克隆模式：选择「完全克隆」（按需求选择完全克隆或链接克隆）

>「Note」完全克隆是和原始虚拟机完全独立的一个拷贝，它不和原始虚拟机共享任何资源，可以脱离原始虚拟机独立使用；链接克隆需要和原始虚拟机共享同一虚拟磁盘文件，不能脱离原始虚拟机独立运行。但采用共享磁盘文件却大大缩短了创建克隆虚拟机的时间，同时还节省了宝贵的物理磁盘空间。

  + 完全克隆：模板：选择Windows 2012模板



  + 链接克隆 
  虚拟机：选择一个Windows 2012的模板； 使用规范：选择「内建」（按需求选择无、内建或自定义规范，规范有助于防止在部署相同设置的虚机时而产生冲突）；模板中已启用WinRM：勾选该选项，表示模板中已经启用和配置WinRM，可以选择通过WinRM的方式安装监控代理和自动化代理

+ 监控方式：


  + 无监控：不安装监控代理，则平台的监控功能不可用

  + WinRM安装监控代理：会通过WinRM的方式访问虚拟机并安装监控代理；设置监控端口，默认是9182

  + 预安装监控代理：指模板中已经安装了监控代理

  + 云平台监控：从vCenter上直接读取虚机的监控数据，不需要安装监控代理



+ 安装自动化代理：


  + 不安装：若不安装自动化代理，则平台的一些自动化功能将无法使用，例如蓝图带应用部署或添加磁盘，某些虚拟机的操作如重置密码，执行脚本等

  + WinRM安装：选择WinRM安装，会通过WinRM的方式访问虚拟机并安装自动化代理

  + 预安装：是指模板中已经安装了自动化代理



+ Windows用户名：输入需要设置的Windows管理员用户名

+ Windows密码：输入需要设置的Windows管理员密码

2.  点击「提交」，提示虚拟机模板已创建。点击「保存」，提示虚拟机模板已更新

## 添加一个OpenStack虚拟机模板 {#添加一个openstack虚拟机模板-1 .afff6}

1.  点击「添加」，输入虚拟机模板名称：Windows 2012 R2 on OpenStack，选择2.3.2节配置的OpenStack云平台并做如下配置：

  + 启动源类型：选择从镜像启动、从快照启动、从云硬盘启动或从云硬盘快照启动


  1. 从镜像启动：选择镜像名称（选择Windows
    2012的镜像）和快照模式（不使用快照、申请时候选择、总是使用最新）

  2. 从快照启动：选择快照名称（选择Windows 2012的快照）

  3.  从云硬盘启动：选择镜像名称（选择Windows
    2012的镜像）和快照模式（不使用快照、申请时候选择、总是使用最新）

  4. 从云硬盘快照启动：选择云硬盘快照名称（选择Windows 2012的快照）


  + 安装监控和自动化代理的方式与vSphere的Windows模板相同

  + Windows用户名: 输入需要设置的Windows管理员用户名

  + 验证类型：密钥对、密码两种类型，选择密码

 + Windows密码：设置用户名对应的密码

2.  点击「提交」，提示虚拟机模板已创建。点击「保存」，提示虚拟机模板已更新



# 定义蓝图


软件架构师可以通过蓝图管理界面以可视化的方式设计虚拟机或应用蓝图。蓝图是对应用的抽象，包含应用的拓扑，工作流以及策略三部分。

通过拖拽式可视化的蓝图建模，软件架构师可以非常高效对复杂多节点应用建模。

普通用户可以在其基础上，通过服务目录申请服务，完成一键申请，快速多次部署。

系统默认内置了蓝图，包括vSphere Linux，vSphere
Windows等，可直接使用，进入下一节进行服务配置和发布。

>「Note」如需创建新的蓝图，请参考[服务建模](https://cloudchef.github.io/doc/AdminDoc/05服务建模)中的详细步骤。

# 配置并发布服务


在SmartCMP云管理平台的服务配置界面里可以创建、配置和发布服务。这里将系统默认配置的**vSphere
Linux**蓝图（1个Server+1个Network）与底层资源池相关联，配置模板等部署所需的必要参数。

>「Note」请使用业务组管理员或基础设施管理员角色登录SmartCMP平台。

## 添加vSphere Linux单节点服务

1.  在左边导航栏选择「服务建模」-「服务配置」，点击「添加」：输入服务名称及服务描述（选填），选择系统默认的vSphere
    Linux蓝图，选择系统默认的Default业务组或全部业务组，点击「提交」

2.  服务配置项创建成功后进入编辑页面，「概况」页面全都选择默认值（可根据需求修改配置）

>「Note」配置服务时，很多选项可以勾选「允许修改」和「仅审批时可修改」。这里存在两种情况：如果勾选一项「允许修改」，则用户在请求服务时，可修改参数，在服务审批阶段也可修改参数；如果勾选两项「允许修改」和「仅审批时可修改」，用户在服务请求中，不可修改参数，只在服务审批阶段允许修改参数；

 进入「组件配置」页面，选择「Server」，进入server节点详细设置页面

「基本信息」：保留默认值（可根据需求修改云主机数量）


 + 计算资源

 OS主机名（Hostname）：继承业务组命名规则
 （不勾选「允许改变」和「仅审批时可修改」）

 云主机名称：继承业务组命名规则
 （不勾选「允许改变」和「仅审批时可修改」）

 注释：选填（不勾选「允许改变」和「仅审批时可修改」）

 + 资源池配置

 资源池选择策略：默认自动选择

 + 模板设置

选择上节配置的vSphere虚拟机模板（Centos 7 --- Linux CentOS 7 on
 vSphere）

 + 计算规格配置

 计算规格模式：自定义

 vCPU数量：2（不勾选「允许改变」和「仅审批时可修改」）

 内存（GB）：8（不勾选「允许改变」和「仅审批时可修改」）

 + 系统盘配置

 置备模式：虚拟机模板中完全克隆时可选

 文件夹：选择一个文件夹，虚机会部署在选中的vCenter文件夹里（资源池中配置）

 虚拟机存储策略：默认数据存储默认值，（不勾选「允许改变」和「仅审批时可修改」）
存储：虚机会部署在选中的存储里。若不选，则部署在资源池定义的存储里

允许用户添加新磁盘时选择置备模式和存储：不勾选

 + 「网络」

 配置IP分配方式。点击配置网络下的「IP分配方式」，选择「IP池」（根据资源池中的「网络资源」配置提供可选范围，若资源池中仅配置IP池的分配方式，则服务配置默认且仅有IP池的分配方式）

  「用户」：保持默认

  「磁盘」：保持默认

  「关系」：保持默认

 「操作许可」：保持默认

  点击「保存」，返回组件配置页面。选择「Network」进行编辑

  进入Network「属性」页面，选择所需网络标签（根据资源池中「网络资源」配置的网络标签可选项进行选择），勾选「管理网络」，点击「保存」，返回组件配置页面

  点击「保存并发布」，新的服务变成已发布状态

>「Note」发布成功后，使用业务组成员角色登录SmartCMP平台，在「服务目录」中申请虚拟机。

## 添加OpenStack Linux 单节点服务

1.  在左边导航栏选择「服务建模」-「服务配置」，点击「添加」：输入服务名称及服务描述（选填），选择系统默认的**OpenStack
    Linux蓝图**，选择系统默认的Default业务组或全部业务组，点击「提交」

2.  服务配置项创建成功后进入编辑页面，「概况」页面全都选择默认值（可根据需求修改配置）

>「Note」配置服务时，很多选项可以勾选「允许修改」和「仅审批时可修改」。这里存在两种情况：如果勾选一项「允许修改」，则用户在请求服务时，可以进行修改参数，在服务审批阶段也可以进行修改参数；如果勾选两项项「允许修改」和「仅审批时可修改」，则用户在请求服务时，不可以进行修改参数，只在服务审批阶段允许进行修改参数；

  进入「组件配置」页面，选择「Server」，配置云服务器，进入节点详细设置页面

 + 「概况」

保留默认值（可根据需求修改云主机数量）

 + 「云资源属性」



 + 基本信息

 OS主机名（Hostname）：继承业务组命名规则
 （不勾选「允许改变」和「仅审批时可修改」）

云主机名称：继承业务组命名规则
（不勾选「允许改变」和「仅审批时可修改」）

 主机集合：不选择

 + 资源池配置

 资源池选择策略：默认自动选择

 + 虚拟机模板

 选择上节配置的虚拟机模板Linux CentOS 7 on OpenStack

 + 「网络资源」

 默认不配置DNS

 「磁盘」：保持默认

 「安全策略组」：保持默认

 「关系」：保持默认

 「操作许可」：保持默认

  点击「保存」，返回组件配置页面。选择「Network」进行编辑

  进入Network「属性」页面，选择所需网络和子网，不勾选「允许改变」和「仅审批时可修改」，IP分配方式根据所选网络和子网在资源池中的配置决定。不勾选「管理网络」，点击「保存」，返回组件配置页面

  点击「保存并发布」，新的服务变成已发布状态

# 申请服务


服务发布成功后，可在服务目录界面查看并申请已发布的服务。

1.  点击左侧导航栏的一级菜单「服务目录」，选择上节配置的vSphere单节点服务或OpenStack单节点服务，点击进入服务申请界面

2.  在该页面查看该服务的详情信息，如：组织信息，部署信息，申请参数等

3.  填写/修改相关信息，若无直接进入下一步

4.  点击申请，根据该业务组的流程控制（审批模板）获得批准后申请成功。Default业务组无审批流程，申请后直接进入部署

# 自助运维


服务申请后，可在「我的部署」-「服务部署」查看该部署的进行状态。

 + 若有审批流程，可在「服务请求」-「待审批」进入待审批页面，可查看当前审批流程走向

 + 若无审批流程，可点击服务部署名称进入部署详情页面，可查看该部署的基本信息，服务部署拓扑，以及操作历史



 + 可在操作历史中查看当前部署进程。在「我的部署」-「服务部署」-「操作历史」标签页中，选中操作，可在下方查看当前部署进程。

 + 在基本信息页面：查看服务名称、蓝图、部署时间、到期时间、保留时间、业务组、项目、所有者等信息

 + 在页面上方可进行服务部署的运维操作。

## 查看服务部署详情和自助运维

服务成功部署后，可在「服务部署」页面查看该服务部署的详细信息以及云主机、应用组件的监控信息。一个服务部署包含一台或多台云主机。

1.  在左侧菜单选择「我的部署」-「服务部署」后，您将会看到服务部署列表，可在「高级搜索」中根据业务组、阶段（运行、操作进行中、关闭、操作失败、已取消、部署审批中
    ）、状态（正常、异常）、所有者、项目进行筛选，也可直接进行搜索操作

2.  在服务部署列表中，您可以选中一个或者多个服务部署快速进行一些运维操作，包括「停止服务部署」「安装软件」「复制服务部署」「延长过期时间」「卸除服务部署」「删除管理信息」「更改所有者」「更改项目」「更改业务组」和「伸缩」（示例为vSphere服务部署，不同云平台的运维操作有差异）

 >「Note」只有在业务组设置或服务配置时配置虚拟机的操作许可，虚拟机在部署生成后才能看到允许的操作列表。Default 业务组默认全部操作启用给业务组管理员，且无审批流程。

  点击服务部署名称，可查看该服务部署的详细信息。服务部署详情信息界面包括「基本信息」「服务部署拓扑」「操作历史」和「监控」（对云主机和应用组件的监控）

  + 「基本信息」：包括服务部署的名称、业务组、项目、蓝图、资源池、云平台，以及费用、状态、时间等相关信息。还包括该服务部署的输入参数列表以及输出结果信息。服务部署失败后，某些场景可线下修复，修复成功后支持更改服务部署状态，将"操作失败"更改为"运行"

  +「服务部署拓扑」：包括服务部署的蓝图、详情和流程信息。鼠标悬停至服务拓扑图中，将显示该节点的关键信息，如Server节点将显示云主机名称、客户操作系统、IP地址、内存、磁盘总空间、vCPU数量、CPU使用率、内存使用率等

  +「操作历史」：显示该服务部署的操作历史记录

  +「监控」：显示对该部署中的云主机和组件应用的监控信息

## 查看云主机详情和自助运维

同时，可在「云主机」中查看云主机状态和详情来对其进行管理和操作，操作的启用和是否需要审批需要在业务组级别或者服务配置级别进行设置。

1.  在左侧菜单选择「我的部署」-「云主机」，您将会看到云主机的列表，在列表右上角「高级搜索」中可以根据业务组、状态（已启动、遗失、已停止）、所有者、项目、标签进行筛选。点击「展示列」，可以勾选或者不选某些列进行展示

2.  在云主机列表中，您可以选中一个或者多个云主机快速进行一些操作，包括「启动」「重新启动」「挂起」「停止」「执行脚本」「设置标签」「启用/切换监控」「更新监控代理」「更新自动化代理」等

3.  您也可以单击某一个云主机进入其详情界面进行管理和操作，包括「基本信息」「操作历史」「快照信息」「监控」「应用列表」标签页和顶部的运维操作列表

>「Note」只有当该云主机安装监控和带应用时，部署成功后，在云主机详情页才能看见监控和应用标签页

「基本信息」包括：

 + 虚拟机及其相关主机的基本信息，如：名称、操作系统、已装软件、vCPU、内存、状态、SSH端口、自动化代理、监控方式、监控端口、租用/保留到期时间等

 + 关系：服务器信息、资源池、数据存储、虚拟机存储策略以及网络标签等

 + 物理主机信息

 + 用户和组

 + 组织信息：服务部署名称、服务名称、业务组、租户、项目等

 + 运行状态

 + IP地址

 + 键值标签

>「Note」更多主机相关信息，将根据不同云平台、不同服务配置项决定

 「操作历史」包括了该虚拟机进行过的操作历史记录

 「快照信息」显示当前的快照信息（快照名称、创建时间等），可对快照进行「刷新」「添加」「恢复」和「删除」操作

 「监控」包括了该虚拟机CPU、内存、磁盘、网络的监控数据（可以按照需要调整时间跨度或者平均时间来查看历史监控数据）

>「Note」只有在虚拟机模板中配置安装监控的虚拟机在部署生成后，才可以在监控中看到数据。

 「应用列表」显示当前虚机已安装的应用列表（若该虚机未安装应用，则不显示应用列表菜单）

  「运维操作列表」包括了该虚拟机可执行的操作列表，具体操作介绍会在下文展开

>「Note」只有在业务组设置或服务配置时配置虚拟机的操作许可，虚拟机在部署生成后才能看到允许的操作列表。Default业务组默认业务组管理员启用全部操作，且无审批流程；业务组成员已启用常见操作，且无审批流程。

## 查看云资源详情

「云资源」中可查看相关云资源状态和详情来对其进行管理和操作。

在左侧菜单选择「我的部署」-「云资源」，您将会看到列表左侧有以下几个类别：存储、容器服务、网络资源、PaaS资源、软件资源。

 + 「存储资源」:云硬盘、对象存储
 
 + 「容器服务」：部署、守护进程集、有状态副本集、容器、服务、路由、存储卷、配置字典、保密字典

 + 「网络资源」：负载均衡器、负载均衡监听器、负载均衡成员池、负载均衡SNAT池、浮动IP、防火墙、安全组、域名系统DNS

 + 「PaaS资源」：关系型数据库、Web应用

 + 「软件资源」：软件


# 工单服务


SmartCMP支持租户和系统管理员定义和发布标准的工单服务，支持用户自服务申请与跟踪。接下来的章节将介绍如何建立自己第一个工单，发布并申请服务。

## 定义服务团队

服务团队是工单服务管理过程中处理工单任务的服务人员集合，支持租户管理员自定义关联用户。

创建服务团队的简要步骤：

1.  点击左侧导航栏「组织架构」-「服务团队」，点击服务团队名称，进入编辑页面

2.  「基本信息」页面，键入名称和描述

3.  「用户」页面，关联和取消关联用户

4.  点击「保存」，服务团队创建成功，与用户关联成功

>「Note」如需修改该服务团队的设置，或创建新的服务团队，请参考[组织架构](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理)中的详细步骤。

## 配置与发布服务

配置服务的简要步骤：

1.  在左边导航栏选择「服务建模」-「服务配置」，点击「添加」

2.  填写服务名称、服务描述（选填）、选择业务组，服务类型为手工工单服务时，增选一项服务流程，点击「提交」，进入服务配置「概况」页面

3.  在「基本信息」标签页填入下列信息：名称，描述，logo图像，服务组，顺序，流程配置页面指定处理人来处理工单任务，配置处理人的角色类型和具体的处理人

4.  点击保存按钮，服务将被保存不发布，点击保存并发布按钮，服务将被发布到服务目录页面。

>「Note」请使用租户管理员角色登录SmartCMP平台。如需修改配置与发布的设置，或创建新的配置与发布，请参考[创建和配置服务工单](https://cloudchef.github.io/doc/AdminDoc/08工单服务管理/)中的详细步骤。如需修改服务流程的配置，或创建新的服务流程配置，请参考[服务流程管理](https://cloudchef.github.io/doc/AdminDoc/08工单服务管理/)。

## 工单处理和跟踪

工单处理和跟踪的简要步骤：

1.  在左侧导航栏点击「服务请求」-「待处理」，其中显示处理请求的基本信息：请求编号，请求类型，标题，业务组，项目，申请状态，申请时间，完成时间。

2.  选择一个待处理的服务请求，点击「请求编号」链接，跳转到请求详情页面，查看该请求的基本信息，工单信息，处理记录，流程步骤，服务处理信息等。

3.  处理方式定义为两种，直接处理和转派处理。选择直接处理方式，点击直接处理，填上处理结果描述，即可点击提交处理。

4.  点击「服务请求」-「所有请求」，即可查看所有服务请求的详细信息。

>「Note」具体的工单处理和跟踪，请您参考[处理和跟踪工单](https://cloudchef.github.io/doc/AdminDoc/08工单服务管理/)




# 快速配置云资源蓝图服务 {#快速配置云资源蓝图服务}


本节简述配置以下几个服务所需的步骤以及配置过程的链接，帮助您快速定位内容。

[vSphere 单节点虚拟机服务](#vSphere单节点虚拟机服务)

[VMware NSX 服务](#VMwareNSX服务)

[vSphere MySQL带监控服务](#vSphereMysql带监控服务)

[OpenStack 单节点服务](#OpenStack单节点服务)

[OpenStack Firewall 服务](#OpenStackFirewall服务)

[OpenStack LoadBalancer withSecurityGroup服务](#OpenStackLoadBalanceWithSecurityGroup服务)

[OpenStack FloatingIP服务](#OpenStackFloatingIP服务)

[Kubernetes服务](#Kubernetes服务)

[阿里云服务](#阿里云服务)

[Azure服务](#Azure服务)

[AWS服务](#AWS服务)

[青云服务](#青云服务)

[Hyper-V服务](#Hyper-V服务)

## vSphere单节点虚拟机服务{#vSphere单节点虚拟机服务}

i.  添加vSphere云平台：参照[添加vSphere云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加vSphere云平台)

ii. 添加vSphere 资源池：参照[ 添加vSphere资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加vSphere资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

iv. 配置虚拟机模板：参照[添加一个vSphere虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加vSphere虚拟机模板)

v.  定义计算规格：参照[添加vSphere计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加vSphere计算规格)

vi. 创建vSphere单节点蓝图：参照[创建vSphere单节点蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建vSphere单节点蓝图)

vii. 配置vSphere单节点服务：参照[ 配置vSphere单节点服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置vSphere单节点服务)

viii. 服务申请：参照[服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

ix. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作) 

x.  云主机相关运维操作：参照[云主机运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#云主机运维操作) 

## VMwareNSX服务{#VMwareNSX服务}

i.  添加VMware NSX平台：参照[ 添加VMware NSX平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加VMwareNSX平台)

ii. 添加vSphere云平台：参照[ 添加vSphere云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加vSphere云平台)

iii. 添加vSphere with NSX资源池：参照[ 添加vSphere with NSX资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加vSphereWithNSX资源池)

iv. 配置虚拟机模板：参照[添加一个vSphere虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加vSphere虚拟机模板)

v.  定义计算规格：参照[添加vSphere计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加vSphere计算规格)

vi. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

vii. 创建VMware NSX蓝图：参照[ 创建VMware NSX蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建VMwareNSX蓝图)

viii. 配置VMware NSX服务：参照[ 配置VMware NSX服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置VMwareNSX服务)

ix. 服务申请：参照[ 服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

x.  服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作) 

xi. 云主机相关运维操作：参照[云主机运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#云主机运维操作) 

## vSphereMySQL带监控服务{#vSphereMysql带监控服务}

i.  添加vSphere云平台：参照[ 添加vSphere云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加vSphere云平台)

ii. 添加vSphere 资源池：参照[ 添加vSphere资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加vSphere资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

iv. 配置虚拟机模板：参照[添加vSphere虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加vSphere虚拟机模板)

v.  定义计算规格：参照[添加vSphere计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加vSphere计算规格)

vi. 创建vSphere MySQL带监控蓝图：参照[ 创建vSphereMySQL带监控蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建vSphereMySQL带监控蓝图)

vii. 配置vSphereMySQL带监控服务：参照[配置vSphereMySQL带监控服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置vSphereMySQL带监控服务)

viii. 服务申请：参照[ 服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

ix. 服务部署运维操作：参照[ 服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作)

x.  云主机相关运维操作：参照[云主机运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#云主机运维操作) 

## OpenStack单节点服务{#OpenStack单节点服务}

i.  添加OpenStack云平台：参照[ 添加OpenStack云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加OpenStack云平台)

ii. 添加OpenStack 资源池：参照[ 添加OpenStack资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加OpenStack资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

iv. 配置虚拟机模板：参照[添加一个OpenStack虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#OpenStack虚拟机模板)

v.  定义计算规格：参照[添加OpenStack计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加OpenStack计算规格)

vi. 创建OpenStack单节点蓝图：参照[创建OpenStack单节点蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建OpenStack单节点蓝图)

vii. 配置OpenStack单节点服务：参照[配置OpenStack单节点服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置OpenStack单节点服务)

viii. 服务申请：参照[ 服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

ix. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作) 

x.  云主机相关运维操作：参照[云主机运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#云主机运维操作) 

## OpenStackFirewall服务{#OpenStackFirewall服务}

i.  添加OpenStack云平台：参照[ 添加OpenStack云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加OpenStack云平台)

ii. 添加OpenStack 资源池：参照[ 添加OpenStack资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加OpenStack资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)


xi. 配置虚拟机模板：参照[添加一个OpenStack虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加OpenStack虚拟机模板)

xii. 定义计算规格：参照[添加OpenStack计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加OpenStack计算规格)

iv. 创建OpenStack Firewall蓝图：参照[ 创建OpenStackFirewall蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建OpenStackFirewall蓝图)

v.  配置OpenStack Firewall服务：参照[ 配置OpenStackFirewall服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置OpenStackFirewall服务)

vi. 服务申请：参照[ 服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

vii. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作) 



## OpenStackLoadBalancerWithSecurityGroup服务{#OpenStackLoadBalancerWithSecurityGroup服务}

i.  添加OpenStack云平台：参照[添加OpenStack云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加OpenStack云平台)

ii. 添加OpenStack 资源池：参照[ 添加OpenStack资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加OpenStack资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

iv. 配置虚拟机模板：参照[添加一个OpenStack虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加OpenStack虚拟机模板)

xiii. 定义计算规格：参照[添加OpenStack计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加OpenStack计算规格)

v.  创建OpenStack LoadBalancer with SecuriryGruop蓝图：参照[创建OpenStack LoadBalancer SecurityGroup蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建OpenStackLoadBalancerSecurityGroup蓝图)

vi. 配置OpenStack LoadBalancer with SecuriryGruop服务：参照[配置OpenStack LoadBalancer with SecuriryGruop服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置OpenStackLoadBalancerWithSecuriryGruop服务)

vii. 服务申请：参照[ 服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

viii. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作) 

ix. 云主机相关运维操作：参照[云主机运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#云主机运维操作) 



## OpenStackFloatingIP服务{#OpenStackFloatingIP服务}

i.  添加OpenStack云平台：参照[添加OpenStack云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加OpenStack云平台)

ii. 添加OpenStack 资源池：参照[ 添加OpenStack资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加OpenStack资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

iv. 配置虚拟机模板：参照[添加一个OpenStack虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加OpenStack虚拟机模板)

v.  定义计算规格：参照[添加OpenStack计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加OpenStack计算规格)

vi. 创建OpenStack FloatingIP蓝图：参照[ 创建OpenStackFloatingIP蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建OpenStackFloatingIP蓝图)

vii. 配置OpenStack Firewall服务：参照[ 配置OpenStackFloatingIP服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置OpenStackFloatingIP服务)

viii. 服务申请：参照[ 服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

ix. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作) 



## OpenStackDNS服务{#OpenStackDNS服务}

i.  添加OpenStack云平台：参照[ 添加OpenStack云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加OpenStack云平台)

ii. 添加OpenStack 资源池：参照[ 添加OpenStack资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加OpenStack资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

iv. 配置虚拟机模板：参照[添加一个OpenStack虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加OpenStack虚拟机模板)

v.  定义计算规格：参照[添加OpenStack计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加OpenStack计算规格)

vi. 创建OpenStack DNS蓝图：参照[创建OpenStackDNS蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建OpenStackDNS蓝图)

vii. 配置OpenStack DNS服务：参照[ 配置OpenStack DNS服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置OpenStackDNS服务)

viii. 服务申请：参照[ 服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

ix. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作) 



## Kubernetes服务{#Kubernetes服务}

i.  添加Kubernetes云平台：参照[ 添加Kubernetes云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加Kubernetes云平台)

ii. 添加Kubernetes 资源池：参照[添加Kubernetes资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加Kubernetes资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

iv. 创建Kubernetes蓝图：参照[ 创建Kubernetes蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建Kubernetes蓝图)

v.  配置Kubernetes服务：参照[ 配置Kubernetes服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置Kubernetes服务)

vi. 服务申请：参照[ 服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

vii. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作) 



## 阿里云服务{#阿里云服务}

i.  添加阿里云云平台：参照[添加阿里云云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加阿里云云平台)

ii. 添加阿里云资源池：参照[添加阿里云资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加阿里云资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

iv. 配置虚拟机模板(阿里云虚拟机模板配置与Azure的配置步骤相似)：参照[添加一个Azure虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加Azure虚拟机模板)

v.  定义计算规格(阿里云计算规格以及云平台规格的定义与Azure相似)：参照[添加Azure计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加Azure计算规格)

vi. 创建阿里云蓝图：参照[创建阿里云蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建阿里云蓝图)

vii. 配置阿里云服务：参照[配置阿里云服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置阿里云服务)

viii. 服务申请：参照[服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

ix. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作)

x.  云主机相关运维操作：参照[云主机运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#云主机运维操作) 

## Azure服务{#Azure服务}

i.  添加Azure云平台：参照[添加Azure云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加Azure云平台)

ii. 添加Azure资源池：参照[添加Azure资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加Azure资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

iv. 配置虚拟机模板：参照[添加一个Azure虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加Azure虚拟机模板)

v.  定义计算规格：参照[添加Azure计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加Azure计算规格)

vi. 创建Azure蓝图：参照[创建Azure蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建Azure蓝图)

vii. 配置Azure服务：参照[配置Azure服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置Azure服务)

viii. 服务申请：参照[服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

ix. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作)

x.  云主机相关运维操作：参照[云主机运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#云主机运维操作) 



## AWS服务{#AWS服务}

i.  添加AWS云平台：参照[添加AWS云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加AWS云平台)

ii. 添加AWS资源池：参照[添加AWS资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#添加AWS资源池)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)


xiv. 配置虚拟机模板(AWS虚拟机模板配置与Azure的配置步骤相似)：参照[添加一个Azure虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加Azure虚拟机模板)

xv. 定义计算规格(AWS计算规格以及云平台规格的定义与Azure相似)：参照[添加Azure计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加Azure计算规格)


iv. 创建AWS蓝图：参照[创建AWS蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建AWS蓝图)

v.  配置AWS服务：参照[配置AWS服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#[配置AWS服务)

vi. 服务申请：参照[服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

vii. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作)

viii. 云主机相关运维操作：参照[云主机运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#云主机运维操作) 

## 青云服务{#青云服务}

i.  添加青云云平台：参照[添加青云云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加青云云平台)

ii. 添加青云资源池：参照[添加青云资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

xvi. 配置虚拟机模板(青云虚拟机模板配置与Azure的配置步骤相似)：参照[添加一个Azure虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加Azure虚拟机模板)

xvii. 定义计算规格(青云计算规格以及云平台规格的定义与Azure相似)：参照[添加Azure计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加Azure计算规格)


iv. 创建青云蓝图：参照[创建青云蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建青云蓝图)

v.  配置青云服务：参照[配置青云服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置青云服务)

vi. 服务申请：参照[服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

vii. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作)

viii. 云主机相关运维操作：参照[云主机运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#云主机运维操作) 


## Hyper-V服务{#Hyper-V服务}

i.  添加Hyper-V云平台：参照[添加Hyper-V云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加Hyper-V云平台)

ii. 添加Hyper-V资源池：参照[添加Hyper-V资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#)

iii. 添加业务组与资源池的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

iv. 配置虚拟机模板：参照[添加Hyper-V虚拟机模板](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/虚拟机模板.html#添加Hyper-V虚拟机模板)

v.  定义计算规格(Hyper-V计算规格定义与vSphere相似)：参照[添加vSphere计算规格](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/计算规格.html#添加vSphere计算规格)

vi. 创建Hyper-V 蓝图：参照[创建Hyper-V蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建Hyper-V蓝图)

vii. 配置Hyper-V服务：参照[配置Hyper-V服务](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置Hyper-V服务)

viii. 服务申请：参照[服务目录申请](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/#服务目录申请)

ix. 服务部署运维操作：参照[服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作) 

x.  云主机相关运维操作：参照[云主机运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#云主机运维操作) 

## F5服务{#F5服务}

平台支持F5的管理和建模，主要功能点包括：
1.  新建和设计蓝图部署虚拟机和应用软件时，可以协同F5的Virtual
    Server，Pool以及SNAT Pool网络配置同时自动化部署下发服务。

2. 支持为已经部署好的虚拟机添加F5负载均衡
3. 服务部署完成之后，支持对Virtual Server和SNAT Pool的配置进行运维修改

您可以通过以下步骤部署F5服务：

i.  添加F5 BIG-IP云平台：参照[添加F5 BIG-IP云平台](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/云平台管理.html#添加F5BIG-IP云平台)

ii. 添加IP池：参照[添加IP池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/IP地址管理.html#添加IP池)

iii. 创建F5 BIG-IP资源池：参照[创建F5 BIG-IP资源池](https://cloudchef.github.io/doc/AdminDoc/03基础设施管理/资源池管理.html#创建F5BIG-IP资源池)

iv. 创建F5 BIG-IP资源池与业务组的关联：参照[业务组添加资源池](https://cloudchef.github.io/doc/AdminDoc/04组织架构管理/业务组.html#业务组添加资源池)

v.  创建F5蓝图：参照[创建F5与OpenStack组合蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/蓝图设计.html#创建F5与OpenStack组合蓝图)

vi. 配置F5服务：参照[配置F5与OpenStack组合蓝图](https://cloudchef.github.io/doc/AdminDoc/05服务建模/服务配置.html#配置F5与OpenStack组合蓝图)

vii. F5服务部署运维操作：参照[ 服务部署运维操作](https://cloudchef.github.io/doc/AdminDoc/06云服务管理/我的部署.html#服务部署运维操作) 
