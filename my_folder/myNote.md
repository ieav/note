
<p align="center"  style="font-size:30px;color:purple">*** <b>myNote</b> ***</p>

### java
---
- 后台接收参数：
> -   接收json 参数  ： @RequestBody 

#### jvm

- **java 执行class 文件问题**

~~~txt

一、java执行class文件是根据CLASSPATH指定的地方来找，不是我们理解当前目录。如果希望它查询当前目录，需要在CLASSPATH中加入“.;”,代表当前目录。

二、java执行class文件对package的路径是强依赖的。它在执行的时候会严格以当前用户路径为基础，按照package指定的包路径转化为文件路径去搜索class文件。各位同学以后注意就OK啦。至于网上说的要在CLASSPATH要加各种包等等都是泛泛而谈，真正静下心分析这个问题的资料不多。很多都没有说到点子上，会误导人的。
~~~
---

#### spring
 > 某个博客 spring 系列 https://www.cnblogs.com/lifullmoon/
 > 
 
##### spring ioc
>> https://www.cnblogs.com/lifullmoon/p/14436372.html

###### spring bean 的生命周期
Bean 完整的生命周期

文字解释如下：

————————————初始化————————————
BeanNameAware.setBeanName() 在创建此bean的bean工厂中设置bean的名称，在普通属性设置之后调用，在InitializinngBean.afterPropertiesSet()方法之前调用
BeanClassLoaderAware.setBeanClassLoader(): 在普通属性设置之后，InitializingBean.afterPropertiesSet()之前调用
BeanFactoryAware.setBeanFactory() : 回调提供了自己的bean实例工厂，在普通属性设置之后，在InitializingBean.afterPropertiesSet()或者自定义初始化方法之前调用

EnvironmentAware.setEnvironment(): 设置environment在组件使用时调用
EmbeddedValueResolverAware.setEmbeddedValueResolver(): 设置StringValueResolver 用来解决嵌入式的值域问题
ResourceLoaderAware.setResourceLoader(): 在普通bean对象之后调用，在afterPropertiesSet 或者自定义的init-method 之前调用，在 ApplicationContextAware 之前调用。

ApplicationEventPublisherAware.setApplicationEventPublisher(): 在普通bean属性之后调用，在初始化调用afterPropertiesSet 或者自定义初始化方法之前调用。在 ApplicationContextAware 之前调用。
MessageSourceAware.setMessageSource(): 在普通bean属性之后调用，在初始化调用afterPropertiesSet 或者自定义初始化方法之前调用，在 ApplicationContextAware 之前调用。
ApplicationContextAware.setApplicationContext(): 在普通Bean对象生成之后调用，在InitializingBean.afterPropertiesSet之前调用或者用户自定义初始化方法之前。在

ResourceLoaderAware.setResourceLoader，ApplicationEventPublisherAware.setApplicationEventPublisher，MessageSourceAware之后调用。
ServletContextAware.setServletContext(): 运行时设置ServletContext，在普通bean初始化后调用，在InitializingBean.afterPropertiesSet之前调用，在 ApplicationContextAware 之后调用注：是在WebApplicationContext 运行时
BeanPostProcessor.postProcessBeforeInitialization() : 将此BeanPostProcessor 应用于给定的新bean实例 在任何bean初始化回调方法(像是InitializingBean.afterPropertiesSet或者自定义的初始化方法）之前调用。这个bean将要准备填充属性的值。返回的bean示例可能被普通对象包装，默认实现返回是一个bean。

BeanPostProcessor.postProcessAfterInitialization() : 将此BeanPostProcessor 应用于给定的新bean实例 在任何bean初始化回调方法(像是InitializingBean.afterPropertiesSet或者自定义的初始化方法)之后调用。这个bean将要准备填充属性的值。返回的bean示例可能被普通对象包装
InitializingBean.afterPropertiesSet(): 被BeanFactory在设置所有bean属性之后调用(并且满足BeanFactory 和 ApplicationContextAware)。
————————————销毁————————————
在BeanFactory 关闭的时候，Bean的生命周期会调用如下方法:

DestructionAwareBeanPostProcessor.postProcessBeforeDestruction(): 在销毁之前将此BeanPostProcessor 应用于给定的bean实例。能够调用自定义回调，像是DisposableBean 的销毁和自定义销毁方法，这个回调仅仅适用于工厂中的单例bean(包括内部bean)

实现了自定义的destory()方法

#####  spring boot

#####  spring cloud
#####  spring data

#### tomcat 
---


#### mybatis
---


#### MQ
---

####  Redis
---


### mysql
---
#### mysql 安装~~~~
> 参考链接：[mysql 安装链接： https://blog.csdn.net/qq_16183731/article/details/86516468](https://blog.csdn.net/qq_16183731/article/details/86516468)
* mysql 安装后生成临密码
./mysqld --initialize --user=xzb --basedir=/opt/modules/mysql --datadir=/opt/modules/mysql/data

#### mysql 8.0 新特性
[mysql 8.0新特性： https://www.jianshu.com/p/be29467c2b0c](https://www.jianshu.com/p/be29467c2b0c)

1. 默认字符集由latin1变为utf8mb4
2. MyISAM系统表全部换成InnoDB表
3. 自增变量持久化
4. DDL原子化
5. 参数修改持久化
6. 新增降序索引
7. group by 不再隐式排序
8.  JSON特性增强
   MySQL 8 大幅改进了对 JSON 的支持，添加了基于路径查询参数从 JSON 字段中抽取数据的 JSON_EXTRACT() 函数，以及用于将数据分别组合到 JSON 数组和对象中的 JSON_ARRAYAGG() 和 JSON_OBJECTAGG() 聚合函数。在主从复制中，新增参数 binlog_row_value_options，控制JSON数据的传输方式，允许对于Json类型部分修改，在binlog中只记录修改的部分，减少json大数据在只有少量修改的情况下，对资源的占用。
9. redo & undo 日志加密
10. innodb select for update跳过锁等待
11.  增加SET_VAR语法
12. 支持不可见索引
13. 支持直方图
14. 新增innodb_dedicated_server参数
       能够让InnoDB根据服务器上检测到的内存大小自动配置innodb_buffer_pool_size，innodb_log_file_size，innodb_flush_method三个参数
15. 日志分类更详细
16. undo空间自动回收
17.  增加资源组
18. 增加角色管理

```sql
 -- 创建角色
mysql> create role role_test;
Query OK, 0 rows affected (0.03 sec)
 
 -- 给角色授予权限
mysql> grant select on db.* to 'role_test';
Query OK, 0 rows affected (0.10 sec)
 
-- 创建用户
mysql> create user 'read_user'@'%' identified by '123456';
Query OK, 0 rows affected (0.09 sec)
 
-- 给用户赋予角色
mysql> grant 'role_test' to 'read_user'@'%';
Query OK, 0 rows affected (0.02 sec)
 
-- 给角色role_test增加insert权限
mysql> grant insert on db.* to 'role_test';
Query OK, 0 rows affected (0.08 sec)
 
-- 给角色role_test删除insert权限
mysql> revoke insert on db.* from 'role_test';
Query OK, 0 rows affected (0.10 sec)

-- 查看默认角色信息
mysql> select * from mysql.default_roles;
 
-- 查看角色与用户关系
mysql> select * from mysql.role_edges;
-- 删除角色
mysql> drop role role_test;
-- 导入数据
mysql> mysql -u root -p -h test < test.sql 

```

>>
> 
>
>
>>

-------------

#### oracle
---


---
----
----

### java 后端模板语言
#### thymeleaf  
https://www.cnblogs.com/msi-chen/p/10974009.html


### nginx 

----
----
----

### Maven 
---
https://www.w3cschool.cn/maven/varq1ht4.html

>> 约定优于配置  Maven 使用约定而不是配置，意味着开发者不需要再自己创建构建过程。

开发者不需要再关心每一个配置细节。Maven 为工程提供了合理的默认行为。当创建 Maven 工程时，Maven 会创建默认的工程结构。开发者只需要合理的放置文件，而在 pom.xml 中不再需要定义任何配置。

举例说明，下面的表格展示了工程源码文件、资源文件的默认配置，和其他一些配置。假定 ${basedir} 表示工程目录：
|   配置项  |     默认值  |
| --- | --- |
|   source code  |    ${basedir}/src/main/java |
|   resources  |   ${basedir}/src/main/resources  |
|   Tests  |  ${basedir}/src/test   |
|   Complied byte code  |  ${basedir}/target   |
|   distributable JAR  |   ${basedir}/target/classes  |


为了构建工程，Maven 为开发者提供了选项来配置生命周期目标和工程依赖（依赖于 Maven 的插件扩展功能和默认的约定）。大部分的工程管理和构建相关的任务是由 Maven 插件完成的。

开发人员不需要了解每个插件是如何工作的，就能够构建任何给定的 Maven 工程。详细内容请参考 Maven 插件部分。

**环境要求**
   JDK : 
   Maven 3.3 要求 JDK 1.7 或以上 ；
   Maven 3.2 要求 JDK 1.6 或以上  
   Maven 3.0/3.1 要求 JDK 1.5 或以上  

 **环境配置**
```txt
操作系统 输出
Windows:使用系统属性设置环境变量。
M2_HOME=C:\Program Files\Apache Software Foundation\apache-maven-3.2.5
M2=%M2_HOME%\bin
MAVEN_OPTS=-Xms256m -Xmx512m

Linux:打开命令终端设置环境变量。
export M2_HOME=/usr/local/apache-maven/apache-maven-3.2.5
export M2=$M2_HOME/bin
export MAVEN_OPTS=-Xms256m -Xmx512m

Mac:打开命令终端设置环境变量。
export M2_HOME=/usr/local/apache-maven/apache-maven-3.2.5
export M2=$M2_HOME/bin
export MAVEN_OPTS=-Xms256m -Xmx512m


```
并将配置的环境变量配置到系统 path 中或者etc/profile 中。

----
- **pom相关**
需要说明的是每个工程应该只有一个 POM 文件。

所有的 POM 文件需要 project 元素和三个必须的字段：groupId, artifactId,version。
在仓库中的工程标识为 groupId:artifactId:version
POM.xml 的根元素是 project，它有三个主要的子节点：

>1. groupId：这是工程组的标识。它在一个组织或者项目中通常是唯一的。例如，一个银行组织 com.company.bank 拥有所有的和银行相关的项目。
>2. artifactId：这是工程的标识。它通常是工程的名称。例如，消费者银行。groupId 和 artifactId 一起定义了 artifact 在仓库中的位置。
>3. version：这是工程的版本号。在 artifact 的仓库中，它用来区分不同的版本。例如：
>com.company.bank:consumer-banking:1.0
>com.company.bank:consumer-banking:1.1.

#### maven  构建配置文件
> 构建配置文件是一组配置的集合，用来设置或者覆盖 Maven 构建的默认配置。使用构建配置文件，可以为不同的环境定制构建过程，例如 Producation 和 Development 环境。

- Profile 主要有三种类型。

|    类型     |                           在哪里定义                           |
| ----------- | ------------------------------------------------------------- |
| Per Project | 定义在工程 POM 文件 pom.xml 中                                  |
| Per User    | 定义在 Maven 设置 xml 文件中 （%USER_HOME%/.m2/settings.xml）    |
| Global      | 定义在 Maven 全局配置 xml 文件中 （%M2_HOME%/conf/settings.xml） |

在 maven_path/conf/settings.xml 下配置 激活profile

  ```xml
  <activeProfiles>
    <activeProfile>development</activeProfile>
  </activeProfiles>
  ```
-  **Maven 仓库有三种类型：**
* 本地（local）
* 中央（central）
* 远程（remote）

#### **maven 添加外部依赖 （中央仓库，私服仓库都找不到jar 的情况下）**

```xml
<!-- 在src 目录下 lib 文件夹下存放 外部jar  -->
         <dependency>
             <groupId>ldapjdk</groupId>
             <artifactId>ldapjdk</artifactId>
             <scope>system</scope>
             <version>1.0</version>
             <systemPath>${basedir}\src\lib\ldapjdk.jar</systemPath>
          </dependency>
```
>外部依赖（library jar location）能够像其他依赖一样在 pom.xml 中配置。
>指定 groupId 为 library 的名称。
>指定 artifactId 为 library 的名称。
>指定作用域（scope）为系统。
>指定相对于工程位置的系统路径。

#### maven 模板
~~~xml

<project xmlns="http://maven.apache.org/POM/4.0.0" 
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
  http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.companyname.insurance</groupId>
  <artifactId>health</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>jar</packaging>
  <name>health</name>
  <url>http://maven.apache.org</url>
  <properties>
     <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>
  <dependencies>
     <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>3.8.1</version>
        <scope>test</scope>
     </dependency>
      <dependency>
         <groupId>data-service</groupId>
         <artifactId>data-service</artifactId>
         <version>1.0-SNAPSHOT</version>
         <scope>test</scope>
     </dependency>
  </dependencies>
</project>

~~~
#### maven 快照
虽然，对于快照，Maven 每次自动获取最新的快照，但你可以在任何 maven 命令中使用 -U 参数强制 maven 下载最新的快照。
```cmd
    mvn clean package -U
```


#### Apache Maven 构建自动化
可以用CI  自动化构建工具 来配合处理

#### 管理依赖
         exclusion 排除依赖 
#### 自动化部署



#### 


### Gradle 

### vue 


----
----
----

### linux 



----
----
----

### algorithm 
---
<mark>小顶堆</mark>

<mark>第k小数</mark>

----
----
----

### version Control
 
#### git 
> * 测试 资源 https 链接：*
 https://github.com/ieav/gittest.git
* 初始化 
linux 更新git:  git clone git://git.kernel.org/pub/scm/git/git.git

git init 
git config   
        --global   对所有仓库生效
        --system  修改配置文件 需要管理员权限

**git config --list**  查看配置列表
git config --list --show-origin  查看git 所以的配置以及所在的文件

<mark> 配置用户名 和密码 </mark>
**git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
git config --global user.passwd xxxxx**

- 
git rm --cached “文件路径”，不删除物理文件，仅将该文件从缓存中删除；
git rm --f “文件路径”，不仅将该文件从缓存中删除，还会将物理文件删除（不会回收到垃圾桶）。

        
git add 文件夹/文件
git commit 文件夹/文件

#####  git  常用操作
---
> 
>>* pull && clone && fetch （获取资源）
>  git clone https://github.com/libgit2/libgit2 本地名称  -- 克隆仓库
> 
> 
>
>> * git branch （分支管理）
>            git branch  --查看有哪些分支
>
>>* checkout  （更换分支） commit (修改后的提交)
>
>> * remote 远程配置  
>  git remote -v   -- 显示远程仓库。
>   运行 git remote add <shortname> <url> 添加一个新的远程 Git 仓库
>          git push origin master -- 提交的代码远程推送 
>  git remote show <remote>  查看某个远程仓库
> git remote rename pb paul    -- 远程仓库重命名。

>>* stage (备份)
>
>>* merge .... (冲突处理)
>
>>* restore and head (回滚)
>
>> * 查看本地当前状况
> git ls-files         查看已存放
>  git status         查看还没添加的文件/查看哪些文件处于什么状态
>（在状态报告中可以看到新建的 README 文件出现在 Untracked files 下面。 未跟踪的文件意味着 Git 在之前的快照（提交）中没有这些文件；Git 不会自动将之纳入跟踪范围。 表示没有加入git 控制中。）
> git status -s  ( git status --short 的缩写。 可以简要显示 git status 命令的输出十分详细,繁琐的信息。) 
>  git diff    （查看尚未暂存的文件更新了哪些部分）
>  git diff --staged （条命令将比对已暂存文件与最后一次提交的文件差异：）

>> * git log   --查看提交历史
>git log -p -2   --显示最近两次提交 （每次的差异）
>git log  --stat   -- 每次提交 的简略统计信息
>      ~ --pretty  -- 项可以使用不同于默认格式的方式展示提交历史 ，这个选项有一些内建的子选项供你使用。 比如 oneline 会将每个提交放在一行显示
>       还有  short，full 和 fuller
>         git log --pretty=oneline
>    git log --pretty=format:"%h - %an, %ar : %s"  （定制化输出）

* git 更新单个文件
>1. 如果想拿远端git服务器上的最新版本(或某个特定版本)覆盖本地的修改,可以使用git pull命令,
但这会全面更新本地代码库和工作拷贝.
>
> 2. 如果想放弃本地工作拷贝所做修改,可以使用git checkout file/to/path命令,
但该命令只能用本地库覆盖你的工作拷贝,并不能取得远端版本的更新.
所以,正确的方法应该是先更新本地库(但不更新工作拷贝),然后用本地库来更新单个的工作拷贝文件.
具体如下:
git fetch
git checkout origin/master -- path/to/fil
>


---
- git 用于忽略某些文件的 配置
        gitHub  有一个十分详细的针对数十种项找目及 到它。 语言的 .gitignore 文件列表， 你可以在https://github.com/github/gitignore 找到他。
        
git mv file_from file_to   (移动文件，重命名)

  git fetch <remote>  从远程仓库中抓取与拉取。
git push origin master

#####  以前整理的git 常用命令
>
temp files

面是我整理的常用 Git 命令清单。几个专用名词的译名如下。

Workspace：工作区
Index / Stage：暂存区
Repository：仓库区（或本地仓库）
Remote：远程仓库

> 一、新建代码库
---
- 在当前目录新建一个Git代码库
$ git init
- 新建一个目录，将其初始化为Git代码库 这个 用在本地新建 推送到远程git 服务上的。
$ git init [project-name]  
- 下载一个项目和它的整个代码历史
$ git clone [url]

> 二、配置
---
Git的设置文件为.gitconfig，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。
- 显示当前的Git配置
$ git config --list

- 编辑Git配置文件
$ git config -e [--global]

- 设置提交代码时的用户信息
$ git config [--global] user.name "[name]"

$ git config [--global] user.email "[email address]"



> 三、增加/删除文件
---
- 添加指定文件到暂存区
$ git add [file1] [file2] ...

- 添加指定目录到暂存区，包括子目录
$ git add [dir]

- 添加当前目录的所有文件到暂存区
$ git add .

- 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...

- 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]

- 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]



> 四、代码提交
---
- 提交暂存区到仓库区
$ git commit -m [message]

- 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]

- 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a

- 提交时显示所有diff信息
$ git commit -v

- 使用一次新的commit，替代上一次提交
- 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]

- 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...



> 五、分支
---
- 列出所有本地分支
$ git branch

- 列出所有远程分支
$ git branch -r

- 列出所有本地分支和远程分支
$ git branch -a

- 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]

- 新建一个分支，并切换到该分支
$ git checkout -b [branch]

- 新建一个分支，指向指定commit
$ git branch [branch] [commit]

- 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]

- 切换到指定分支，并更新工作区
$ git checkout [branch-name]

- 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]

- 合并指定分支到当前分支
$ git merge [branch]

- 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

- 删除分支
$ git branch -d [branch-name]

- 删除远程分支
$ git push origin --delete [branch-name]

$ git branch -dr [remote/branch]

> 六、标签
---
- 列出所有tag
$ git tag

- 新建一个tag在当前commit
$ git tag [tag]

- 新建一个tag在指定commit
$ git tag [tag] [commit]

- 查看tag信息
$ git show [tag]

- 提交指定tag
$ git push [remote] [tag]

- 提交所有tag
$ git push [remote] --tags

- 新建一个分支，指向某个tag
$ git checkout -b [branch] [tag]

> 七、查看信息

- 显示有变更的文件
$ git status

- 显示当前分支的版本历史
$ git log

- 显示commit历史，以及每次commit发生变更的文件
$ git log --stat

- 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]

$ git whatchanged [file]

- 显示指定文件相关的每一次diff
$ git log -p [file]

- 显示指定文件是什么人在什么时间修改过
$ git blame [file]

- 显示暂存区和工作区的差异
$ git diff

- 显示暂存区和上一个commit的差异
$ git diff --cached [file]

- 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD

- 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]

- 显示某次提交的元数据和内容变化
$ git show [commit]

- 显示某次提交发生变化的文件
$ git show --name-only [commit]

- 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]

- 显示当前分支的最近几次提交
$ git reflog



> 八、远程同步
---
- 下载远程仓库的所有变动
$ git fetch [remote]

- 显示所有远程仓库
$ git remote -v

- 显示某个远程仓库的信息
$ git remote show [remote]

- 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]

- 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]

- 上传本地指定分支到远程仓库
$ git push [remote] [branch]

- 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force

- 推送所有分支到远程仓库
$ git push [remote] --all



> 九、撤销
---
- 恢复暂存区的指定文件到工作区
$ git checkout [file]

- 恢复某个commit的指定文件到工作区
$ git checkout [commit] [file]

- 恢复上一个commit的所有文件到工作区
$ git checkout .

- 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]

- 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard

- 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]

- 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]

- 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]

- 新建一个commit，用来撤销指定commit
- 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]


##### 十、git 简单操作
###### git 学习地址
>> https://learngitbranching.js.org/
---
- 生成一个可供发布的压缩包
$ git archive

```perl
git config --user.username 'xxx'
git config --user.emal 'xxx'
git config --list 

git config --help
##情况 1： 本地已经创建了项目,希望用git 来管理
git init 
git status
git add 
git commit
git reset 
git log


---
##情况 2： 远程仓库里的项目，希望下载下来继续开发
git clone <url> <where to clone>
git remote -v
git branch -a 

git diff
git status
git add -A
git commit -m ''

git pull origin master 
git push origin master
git branch 分支名称
git branch  --查看all分支

git checkout 分支名称

git push -u origin 本地分支名称
git branch -a 

git branch  --merged   --查看哪些分支被merge 了
git merge 分支名称  --merge 这个分支到当前分支
git push origin master
 
 ## 删除分支
 git branch --merged
 git branch  -d 分支名称
 git branch -a 
 git push origin --delete 分支名称
 
--------------------------
以上只是基本常规操作
--------------------------

**--------------------------
常用命令
--------------------------**

命令	说明
git init	初始化git本地库
git add .	将当前文件夹下的所有文件添加到git的跟踪中，意思就是交给git经管，提交到本地库，暂存所有的更改
git checkout .	丢弃所有的更改
git add src	将文件夹src提交到本地库
git commit -m "first commit" (也可以是-am)	提交并写提交信息
git remote add origin git@github.com:zhchji777/ShoppingMall.git	设置远程库
git remote set-url origin 你的远端地址	设置远端仓库地址
Git config –global user.name “用户名 ” ，git config –global user.email 邮箱地址	设置用户名和邮箱
git push -u origin master (也可强制提交git push -u -f origin master)	将本地变更推送到远程库 (出错时可先执行git pull)
git pull --rebase origin master	将远程库变更更新到本地库
git clone git＠github.com:zhchji7/zhchji-gitgub.git	将github上的项目down下来
git status	状态查询命令
git branch	查看位置
git checkout -b V1.0.1 origin/master	创建分支
git push origin HEAD -u	将分支推送到远程
git checkout master	切换回master分支
git remote –v	查看远端地址
git config --list	查看配置
git config –global https.proxy http://127.0.0.1:1080	设置代理
git config --global http.proxy	查看代理
git config –global –unset https.proxy	取消设置代理
git rm -r --cached < file name >	移除对文件的跟踪

git remote add origin https://github.com/ieav/gittest.git

```

---------------------------------------====================================
连接远程服务器：
打开终端使用ssh命令链接远程服务器。
命令格式 ： ssh root@192.168.1.1（root对应你使用的用户名，192……对应的服务器ip地址，一般服务器端口22，命令默认22.如果需要更改端口在ssh后面 -p 端口）

---------------------------------------==================================== 
夜晚屏幕亮度设置 
sudo echo 20 > /sys/class/backlight/intel_backlight/brigh2ness

----------------------------------------====================================  
		chrome 软件包记录

google-chrome-73.0.3683.103-1-x86_64.pkg.tar.xz                    perl-file-which-1.23-1-any.pkg.tar.xz
google-chrome-73.0.3683.75-1-x86_64.pkg.tar.xz                     perl-path-tiny-0.108-1-any.pkg.tar.xz
google-chrome-73.0.3683.86-1-x86_64.pkg.tar.xz
>



---
<p align="center" style="font-size:30px"> end</p>         

#### svn

----
[svn 主页 下载地址](https://tortoisesvn.net/index.zh.html)

----

## windows
### windows cmd 常用命令
> 1、Windows常用命令~~~~打开命令窗口(WIN建+R)
>>1.calc：启动计算器
>>2.appwiz.cpl：程序和功能
>>3.certmgr.msc：证书管理实用程序
>>4.charmap：启动字符映射表
>>5.chkdsk.exe：Chkdsk磁盘检查(管理员身份运行命令提示符)
>>6.cleanmgr: 打开磁盘清理工具
>>7.cliconfg：SQL SERVER 客户端网络实用工具

>>8.cmstp：连接管理器配置文件安装程序

>>
>>9.cmd.exe：CMD命令提示符

>>10.Shutdown：关机命令

>>11.colorcpl：颜色管理，配置显示器和打印机等中的色彩

>>12.CompMgmtLauncher：计算机管理

>>13.compmgmt.msc：计算机管理

>>14.credwiz：备份或还原储存的用户名和密码

>>15.comexp.msc：打开系统组件服务

>>16.control：控制面版

>>17.dcomcnfg：打开系统组件服务

>>18.Dccw：显示颜色校准

>>19.devmgmt.msc：设备管理器

>>20.desk.cpl：屏幕分辨率

>>21.dfrgui：优化驱动器 Windows 7→dfrg.msc：磁盘碎片整理程序

>>22.dialer：电话拨号程序

>>23.diskmgmt.msc：磁盘管理

>>24.dvdplay：DVD播放器

>>25.dxdiag：检查DirectX信息

>>26.eudcedit：造字程序

>>27.eventvwr：事件查看器

>>28.explorer：打开资源管理器

>>29.Firewall.cpl：Windows防火墙

>>30.FXSCOVER：传真封面编辑器

>>31.fsmgmt.msc：共享文件夹管理器

>>32.gpedit.msc：组策略

>>33.hdwwiz.cpl：设备管理器

>>34.inetcpl.cpl：Internet属性

>>35.intl.cpl：区域

>>36.iexpress：木马捆绑工具，系统自带

>>37.joy.cpl：游戏控制器

>>38.logoff：注销命令

>>39.lusrmgr.msc：本地用户和组

>>40.lpksetup：语言包安装/删除向导，安装向导会提示下载语言包

>>41.lusrmgr.msc：本机用户和组

>>42.main.cpl：鼠标属性

>>43.mmsys.cpl：声音

>>44.magnify：放大镜实用程序

>>45.mem.exe：显示内存使用情况(如果直接运行无效，可以先管理员身份运行命令
提示符，在命令提示符里输入mem.exe>d:a.txt 即可打开d盘查看a.txt，里面的就
是内存使用情况了。当然什么盘什么文件名可自己决定。)

>>46.MdSched:Windows内存诊断程序

>>47.mmc：打开控制台

>>48.mobsync：同步命令

>>49.mplayer2：简易widnows media player

>>50.Msconfig.exe：系统配置实用程序

>>51.msdt：微软支持诊断工具

>>52.msinfo32：系统信息

>>53.mspaint：画图

>>54.Msra：Windows远程协助

>>55.mstsc：远程桌面连接

>>56.NAPCLCFG.MSC：客户端配置

>>57.ncpa.cpl：网络连接

>>58.narrator：屏幕“讲述人”

>>59.Netplwiz：高级用户帐户控制面板，设置登陆安全相关的选项

>>60.netstat : an(TC)命令检查接口

>>61.notepad：打开记事本

>>62.Nslookup：IP地址侦测器

>>63.odbcad32：ODBC数据源管理器

>>64.OptionalFeatures：打开“打开或关闭Windows功能”对话框

>>65.osk：打开屏幕键盘

>>66.perfmon.msc：计算机性能监测器

>>67.perfmon：计算机性能监测器

>>68.PowerShell：提供强大远程处理能力

>>69.printmanagement.msc：打印管理

>>70.powercfg.cpl：电源选项

>>71.psr：问题步骤记录器

>>72.Rasphone：网络连接

>>73.Recdisc：创建系统修复光盘

>>74.Resmon：资源监视器

>>75.Rstrui：系统还原

>>76.regedit.exe：注册表

>>77.regedt32：注册表编辑器

>>78.rsop.msc：组策略结果集

>>79.sdclt：备份状态与配置，就是查看系统是否已备份

>>80.secpol.msc：本地安全策略

>>81.services.msc：本地服务设置

>>82.sfc /scannow：扫描错误并复原/windows文件保护

>>83.sfc.exe：系统文件检查器

>>84.shrpubw：创建共享文件夹

>>85.sigverif：文件签名验证程序

>>86.slui：Windows激活，查看系统激活信息

>>87.slmgr.vbs -dlv ：显示详细的许可证信息

>>88.snippingtool：截图工具，支持无规则截图

>>89.soundrecorder：录音机，没有录音时间的限制

>>90.StikyNot：便笺

>>91.sysdm.cpl：系统属性

>>92.sysedit：系统配置编辑器

>>93.syskey：系统加密，一旦加密就不能解开，保护系统的双重密码

>>94.taskmgr：任务管理器(旧版)

>>95.TM任务管理器(新版)

>>96.taskschd.msc：任务计划程序

>>97.timedate.cpl：日期和时间

>>98.UserAccountControlSettings用户账户控制设置

>>99.utilman：辅助工具管理器

>>100.wf.msc：高级安全Windows防火墙

>>101.WFS：Windows传真和扫描

>>102.wiaacmgr：扫描仪和照相机向导

>>103.winver：关于Windows

>>104.wmimgmt.msc：打开windows管理体系结构(WMI)

>>105.write：写字板

>>106.wscui.cpl：操作中心

>>107.wuapp：Windows更新

>>108.wscript：windows脚本宿主设置

>>

>2、CMD常用命令1
打开"运行"对话框（Win+R），输入cmd，打开控制台命令窗口
也可以通过cmd /c 命令 和 cmd /k 命令的方式来直接运行命令（/c表示执行完命令后关闭cmd窗口；/k表示执行完命令后保留cmd窗口）

>>1.cd ：切换目录
例：cd (显示当前目录)
例：cd … (进入父目录)

>>2.dir：显示目录中的内容
例：dir (显示当前目录中的子文件夹与文件)
例：dir /b (只显示当前目录中的子文件夹与文件的文件名)
例：dir /p ( 分页显示当前目录中的子文件夹与文件)
例：dir /ad (显示当前目录中的子文件夹)
例：dir /S (递归显示当前目录中的内容)

>>3.tree：显示目录结构

>>4.ren：文件或目录重命名
例：ren rec.txt rec.ini (将当前目录下的rec.txt文件重命名为rec.ini)
例：ren c:\test test_01 (将c盘下的test文件夹重命名为test_01)

>>5.md：创建目录
例：md movie music (在当前目录中创建名为movie和music的文件夹)
例：md d:\test\movie (创建d:\test\movie目录)

>>6.rd：删除目录
例：rd movie (删除当前目录下的movie空文件夹)
例：rd /s /q d:\test (使用安静模式删除d:\test)

>>7.copy：拷贝文件
例：copy key.txt c:\doc (将当前目录下的key.txt拷贝到c:\doc下)
注：若doc中也存在一个key.txt文件，会询问是否覆盖
例：copy jobs c:\doc (将当前目录下jobs文件夹中文件（不递归子目录）拷贝到c:\doc下)
例：copy key.txt c:\doc\key_bak.txt // 将当前目录下的key.txt拷贝到c:\doc下，并重命名为key_bak.txt（若doc中也存在一个key_bak.txt文件，会询问是否覆盖）
例：copy /Y key.txt c:\doc (将当前目录下的key.txt拷贝到c:\doc下，不询问，直接覆盖写）
例：copy key.txt + (复制文件到自己，实际上是修改了文件日期)
例：copy /Y key1.txt + key2.txt key.txt ( 将当前目录下的key1.txt与key2.txt的内容合并写入key.txt中，不询问，直接覆盖写）

>>8.xcopy ：更强大的复制命令
例：xcopy c:\bat\hai d:\hello\ (将c:\bat\hai中的所有内容拷贝到d:\hello中)
注：需要在hello后加上\ 表示hello为一个目录，否则xcopy会询问hello是F，还是D。

>>9.move 移动文件
例：move .png test (将当前目录下的png图片移动到当前目录下test文件夹中)
注：若test中也存在同名的png图片，会询问是否覆盖。
例：move /Y .png test (将当前目录下的png图片移动到当前目录下test文件夹中 )
例：move 1.png d:\test\2.png ( 将当前目录下的1.png移动到d盘test文件夹中，并重命名为2.png)
例：move test d:\new ( 若d盘中存在new文件夹，将当前目录下的test文件夹移动到d盘new文件夹中；若不存在，将当前目录下的test文件夹移动到d盘，并重命名为new)

>>10.del 删除文件
注：目录及子目录都不会删除
例：del test (删除当前目录下的test文件夹中的所有非只读文件)

>>11.replace 替换文件
注：即使这个文件在使用，仍然可以替换成功
例：replace d:\love.mp3 d:\mp3 (使用d盘下的love.mp3强制替换d盘mp3目录中的love.mp3文件)

>>12.attrib 查看或修改文件或目录的属性
例：attrib 1.txt (查看当前目录下1.txt的属性)
例：attrib -R 1.txt (去掉1.txt的只读属性)
例：attrib +H movie ( 隐藏movie文件夹)

>>13.assoc 设置’文件扩展名’关联到的’文件类型’
例：assoc (显示所有’文件扩展名’关联)
例：assoc .txt (显示.txt代表的’文件类型’，结果显示.txt=txtfile)
例：assoc .doc (显示.doc代表的’文件类型’，结果示.doc=Word.Document.8)
例：assoc .exe (显示.exe代表的’文件类型’，结果显示.exe=exefile)
例：assoc .txt=txtfile ( 恢复.txt的正确关联)

>>14.ftype 设置’文件类型’关联到的’执行程序和参数’
例：ftype (显示所有’文件类型’关联)
例：ftype exefile (显示exefile类型关联的命令行，结果显示 exefile="%1" %*)

>>15.type 显示文本文件内容
例：type c:\11.txt (显示c盘中11.txt的文本内容)
例：type conf.ini (显示当前目录下conf.ini的文本内容)
例：type c:\11.txt | more (分页显示c盘中11.txt的文本内容)

>>16.more 逐屏的显示文本文件内容
例：more conf.ini (逐屏的显示当前目录下conf.ini的文本内容 )

>>17.& 顺序执行多条命令，而不管命令是否执行成功
例：cd /d d:\src&work.exe /o c:\result.txt (先将当前工作目录切换到d:\src下，然后执行work.exe /o c:\result.txt命令)

>>18.&& 顺序执行多条命令，当碰到执行出错的命令后将不执行后面的命令
例：find “ok” c:\test.txt && echo 成功 (如果找到了"ok"字样，就显示"成功"，找不到就不显示)

>>19.|| 顺序执行多条命令，当碰到执行正确的命令后将不执行后面的命令
例：find “ok” c:\test.txt || echo 不成功 (如果找不到"ok"字样，就显示"不成功"，找到了就不显示)

>>20.| 管道命令
例：dir . /s/a | find /c “.exe” ( 先执行dir命令，然后对输出结果（stdout）执行find命令)

>>21.> 将当前命令输出以覆盖的方式重定向
例：tasklist > p1.txt (将tasklist的输出结果（stdout）以覆盖的方式重定向到p1.txt文件中)
注：tasklist的输出结果就不会打印到屏幕上了
例：tasklist 1> p1.txt (等同于：tasklist > p1.txt)
例：dir bin 2> p1.txt (输出结果（stdout）打印在屏幕上，错误信息（stderr）以覆盖的方式重定向到p1.txt中)
注：bin目录不存在时，会输出错误信息

>>22.>> 将当前命令输出以追加的方式重定向
例：tasklist >> p2.txt ( 将tasklist的输出结果（stdout）以追加的方式重定向到p2.txt文件中)
注：tasklist的输出结果就不会打印到屏幕上了
例：tasklist 1>> p2.txt (等同于：tasklist >> p2.txt)

>>23.< 从文件中获得输入信息，而不是从屏幕上，一般用于date time label等需要等待输入的命令
例：date <temp.txt ( temp.txt中的内容为2005-05-01)

>>24.@ 命令修饰符 在执行命令前，不打印出该命令的内容
例：@cd /d d:\me (执行该命令时，不打印出命令的内容：cd /d d:/me)

>>25., 在某些特殊的情况下可以用来代替空格使用
例：dir,c:\ (相当于：dir c:)

>>26.; 当命令相同的时候,可以将不同的目标用;隔离开来但执行效果不变。如执行过程中发生错误则只返回错误报告但程序还是会继续执行
例：dir c:;d:;e:\ (相当于顺序执行：dir c:\ dir d:\ dir e:)

>>27.echo 输出一个"回车换行"，空白行
例：echo off (后续所有命令在执行前，不打印出命令的内容)
例：echo on (后续所有命令在执行前，打印出命令的内容)
例：echo 123 (输出123到终端屏幕)
例：echo “Hello World!!!” ( 输出Hello World!!!到终端屏幕)
例：echo %errorlevel% (每个命令运行结束，可以用这个命令行格式查看返回码；默认值为0，一般命令执行出错会设errorlevel为1)
例：echo test > p1.txt (输出test的字符串到当前目录中的p1.txt文件中)

>>28.set 显示当前用户所有的环境变量
例：set path (查看以path开头的环境变量)
例：set path= (清空path变量)

>>29.path 显示当前path变量的值
例：path d:\xxx;%PATH% (将d:\xxx路径添加到path中)

>>30.cls 清除屏幕

>>31.ver 显示当前windows系统的版本号

>>32.winver 弹框显示当前windows系统信息

>>33.vol 显示当前分区的卷标

>>34.label 显示当前分区的卷标，同时提示输入新卷标

>>35.label c:system 设置c盘的卷标为system

>>36.time 显示或设置当前时间
例：time /t (显示当前时间)
例：time (设置新的当前时间"格式：hh:mm:ss"，直接回车则表示放弃设置)

>>37.date 显示或设置当前日期
例：date /t (显示当前日期)

>>38.title 正在做命令行测试

>>39.start 运行某程序或命令
例：start /max notepad.exe (最大化的方式启动记事本)
例：start /min calc.exe (最小化的方式启动计算器)
例：start tasklist (启动一个cmd实例窗口，并运行tasklist)

>>40.exit 退出当前cmd窗口实例
例：exit 0 (退出当前cmd窗口实例，并将过程退出代码设置为0)
注：0表示成功，非0表示失败
例：exit /B 1 (退出当前bat脚本，并将ERRORLEVEL系统变量设置为1)

>>41.pause 暂停批处理程序，并显示出：请按任意键继续…

>>42.color 设置当前cmd窗口背景色和前景色（前景色即为字体的颜色）

>>43.systeminfo 查看当前计算机的综合信息

>>44.wmic 查看进程信息

>>45.logoff 注销当前用户

>>46.shutdown 关闭、重启、注销、休眠计算机
例：shutdown /s (关闭计算机)
例：shutdown /s /t 3600 ( 一小时后，关闭本地计算机)
例：shutdown /a ( 终止系统关闭)
例：shutdown /r ( 关闭并重启本地计算机)
例：shutdown /m 192.168.1.166 /r (关闭并重启ip为192.168.1.166的计算机)

>>47.net 非常重要的命令，但需要通过子命令来完成操作。
例：net start (查看已经启动的服务)
例：net start “Task Scheduler” (开启任务计划服务)
例：net stop “Task Scheduler” (关闭任务计划服务)
例：net start dnscache (开启dns缓存服务)
例：net stop dnscache (关闭dns缓存服务)
例：net share ( 查看当前用户下的共享目录)
例：net share workFile /delete ( 取消名为workFile的共享状态)
例：net share xxx=c:\360Downloads (将c:\360Downloads设为共享，并取名为xxx)
例：net share ipc$ (开启ipc共 享 ) 例 ： n e t s h a r e i p c 共享) 例：net share ipc共享)例：netshareipc /del (删除ipc共 享 ) 例 ： n e t s h a r e c 共享) 例：net share c共享)例：netsharec /del (删除c盘共享)

>>48.tasklist 显示当前运行的进程信息（可查看PID）

>>49.taskkill 结束指定的进程
例：taskkill /im notepad.exe (结束名为notepad.exe的进程)
例：taskkill /pid 1230 /pid 1241 /pid 1253 /t ( 结束pid为1230、1241和1253的进程以及由它们启动起来的子进程)
例：taskkill /f /im cmd.exe /t (强制结束有名为cmd.exe的进程以及由它启动起来的子进程)

>>50.ping 用于检测网络是否通畅，以及网络时延情况（工作在ICMP协议上）
例：ping baidu.com (测试与baidu服务器的连接情况)
例：ping 220.181.111.86 ( 测试与ip为220.181.111.86的连接情况)

>>51.ipconfig 查看电脑ip参数配置信息
例：ipconfig /all (查看本地ip地址等详细信息)
例：ipconfig /displaydns ( 显示本地dns缓存的内容)
例：ipconfig /flushdns ( 清除本地dns缓存的内容)

>>52.nslookup 用于查询DNS的记录
例：nslookup www.baidu.com // 获取www.百度.com的域名解析
例：nslookup -d www.baidu.com // 打印出www.baidu.com的域名解析所有记录

>>53.netstat 显示与IP 、TCP 、UDP 和ICMP 协议相关的统计数据，一般用于检验本机各端口的网络连接情况。
例：netstat -a (查看开启了哪些端口)
例：netstat -n (查看端口的网络连接情况)
例：netstat -v (查看正在进行的工作)
例：netstat -p tcp ( 查看tcp协议的使用情况)

>>54.route 在本地IP路由表中显示和修改条目

>>55.telnet 远程登录到网络中的计算机

>>56.find 文件中搜索字符串
例：find /N /I “pid” 1.txt (在1.txt文件中忽略大小写查找pid字符串，并带行号显示查找后的结果)
例：find /C “exe” 1.txt (只显示在1.txt文件中查找到exe字符串的次数)
例：find /V “exe” 1.txt (显示未包含1.txt文件中未包含exe字符串的行)
> 

------

## 网络
### http 
-- HTTP中post和put的根本区别和优势
```text
作者：知乎用户
链接：https://www.zhihu.com/question/48482736/answer/139024541

put和post的技术实现上应该是没有很大区别的。但在于协议上语义是很大区别。那么区别是什么？
首先，HTTP协议使用的是URI，是一种表示资源标志，那么对应的HTTP Verb就是各种对资源的操作，GET，PUT，DELETE等，明确这些，再往下看。
PUT：client对一个URI发送一个Entity，服务器在这个URI下如果已经又了一个Entity，那么此刻服务器应该替换成client重新提交的，也由此保证了PUT的幂等性。
如果服务器之前没有Entity ，那么服务器就应该将client提交的放在这个URI上。总结一个字：PUT。对的，PUT的方法就是其字面表意，将client的资源放在请求URI上。
对于服务器到底是创建还是更新，由服务器返回的HTTP Code来区别。注：通过上面可以知道，如果用PUT来达到更改资源，需要client提交资源全部信息，
如果只有部分信息，不应该使用PUT（因为服务器使用client提交的对象整体替换服务器的资源）。

POST：这个Verb是比较特殊。不同于一般的增删改，使用场景比较多。根据RFC文档上描述，有以下几个场景：（https://tools.ietf.org/html/rfc2616#section-9.5）- Annotation of existing resources;

- Posting a message to a bulletin board, newsgroup, mailing list, or   
  similar group of articles;

- Providing a block of data, such as the result of submitting a
  form, to a data-handling process;
  
- Extending a database through an append operation.因为服务器在实现POST是不可预知，所以将其定义为不安全、不幂等的Verb。
- 基本上不能方便的归纳为“增删改”之类的行为，都可以使用POST方法。（可以用于“创建不由client决定URI的资源”，但本质上跟第三个有点儿类似，所以我在使用时，基本按照第三个去理解）。
另外使用POST去实现“部分更新资源”可以不错的。如果只有语义上的区别，那么不遵守有什么问题呢？如果只是个人开发或者公司内部这么规定，那也没有很大问题。但是规范上来说，不好。规范带来的好处是很多的，就像是开发人员的语言一样，当大家遵守同样的规范，沟通才更容易，不至于导致出现问题。
公司内部还行，但是如果牵涉到外部工具或者其他公司开发合作，那还是会有问题的。举个比较严重的例子。chrome浏览器为了加快页面加载，会在页面预加载某些GET链接(跳转链接，非资源链接)，这样用户点那个链接时，加载速度就很快。有一个图片还是什么网站，使用GET请求，参数里面有个OPT用来表示动作。用户打开页面时，嵌入了OPT=“DEL”的链接在图片附近的表单中，然后就被Chrome删除了。再举个其他可能接触的例子。公司可能使用工具解析client请求，来分析请求的分布等信息。如果client的User-Agent字段没有遵守协议标准，那么工具将无法正确统计，这样的例子很多。标准的存在意义就是为了统一概念，这样即使从未见面的人，各个国家不同语种的人，甚至火星人也能轻松交流。最好的例子就是数学了
@@ 一个例子是网不好的时候，post提交后没收到响应，于是客户端再次尝试提交，成功后刷新看到新建了两条资源，如果用put的话就不会出现这样的情况。所以尽量使用put去代替pos
==================================================================================
[HTTP POST GET 本质区别详解](https://zhuanlan.zhihu.com/p/158935396)
[get 和post 的区别](https://blog.csdn.net/gideal_wang/article/details/4316691)
ajax 使用的对象 xmlhttpRequest 动态代理。
```

### some code
#### 分页calculate
```java
 // 分页计算 --使用于 mysql
     if(null == pageable){
            start=0;
            end =20;
        }else{
            start=pageable.getPageNum()>1?pageable.getPageSize()*(pageable.getPageNumber()-1):0;
            end=pageable.getPageNum()>1?pageable.getPageSize()*(pageable.getPageNumber()):pageable.getPageSize();
        }
```



