**使用界面**

您可以通过多个界面登录SmartCMP，进行使用和管理。以下为您介绍SmartCMP不同界面的用途、访问方式和所需权限。

 #  Admin管理控制界面

用途：
 + 在租户中心创建、编辑、删除租户
 + 许可证管理，添加、更新、删除许可证
 + 添加、编辑、删除常见问题解答
 + 自定义租户的展示界面（包括Logo图片和主题配色）


访问方式：
1. 打开浏览器，输入访问地址：http://(SmartCMP-IP地址)/#/login?tenant=admin
2. 登录

所需凭据：
您必须使用系统管理员sysadmin进行登录。

  #   默认租户使用和管理界面 

在SmartCMP安装完成之后，会为您创建一个默认的租户。
 
用途：
 + 接入和管理云平台的资源
 + 管理和配置组织架构
 + 创建和发布服务
 + 申请和使用云资源

访问方式：
1. 打开浏览器，输入访问地址：http://(SmartCMP-IP地址)
2. 登录


所需凭据：
您可以使用系统管理员，租户初始化创建的默认租户用户（admin，bgadmin，或user），或您创建的该租户下的其他用户进行登录。关联不同角色的用户有不同的管理配置和使用权限，详细说明请参考“[角色](https://cloudchef.github.io/doc/foundationConcepts/02组织架构/角色.html)”章节。


# 其它租户使用和管理界面

您可以通过Admin管理控制界面创建其他租户。租户提供了资源使用和管理配置的隔离，有关租户的详细说明请参考“[租户](https://cloudchef.github.io/doc/foundationConcepts/02组织架构/租户.html)”章节。

用途：
 + 接入和管理云平台的资源
 + 管理和配置组织架构
 + 创建和发布服务
 + 申请和使用云资源

访问方式：
1. 打开浏览器，输入访问地址：http://(SmartCMP-IP地址)
2. 登录。

所需凭据：
您可以使用该租户初始化创建的用户，或您创建的该租户下的其他用户进行登录。系统将自动判断用户所属的租户，进行登录。如果您想使用系统管理员sysadmin登录，请在访问地址中指明租户的名称：http://(SmartCMP-IP地址)/#/login?tenant=（租户ID）

例如：
当您在Admin配置管理界面创建租户DemoTenant，系统将为您默认创建Default业务组和三个用户：
+ DemoTenant_admin，租户管理员
+ DemoTenant_bgadmin，Default业务组管理员
+ DemoTenant_user，Default业务组普通用户

若使用系统管理员登录，访问地址为：http://(SmartCMP-IP地址)/#/login?tenant=demotenant


