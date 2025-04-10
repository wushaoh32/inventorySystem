# 基于Python+SQLite + Tkinter的备件库管理系统	

#### 1、页面设计：Tkinter

#### 2、模块安装

​	pandas模块

​	openyxal模块

#### 3、软件打包

​	安装pyinstaller
​        执行打包程序

```python
pyinstaller -F --onefile --noconsole  -n 备件库管理系统 InventorySystem.py	
```
#### 4、代码逻辑
   ##### 基于Python+Sqlite的备件库管理系统
   全屏显示、可执行文件、Sqlite数据实现本地存储
   ##### 主界面介绍
​	**上**         

​	程序主页面分为两部分：按钮占四分之一(颜色#DCDCDC)和数据显示占四分之三，有6个按钮，横向排列，分别为入库、出库、导入、导出（能够实现从excel导入数据源，导出按钮可以实现一个导出的excel文件）、搜索（点击后出现一个弹窗，有两种搜索：物料编号和库存名称，直接定位到这一行）、刷新。

​	**下**

​	下方的四分之三的标头展示框上的显示：1序号、2库房名称、3物料编号、4物料名称、5规格型号、6物料分类、7单位、8库存数量、9货架编号、10层数，11最后库存变动时间。



##### 功能介绍

①入库：点击后显示一个弹窗：显示9条信息，序号和时间自动添加，提交过存储，并在主页面进行展示。重点功能：当输入物料名称时，下方的规格型号文本框，能够自动出现数据库中已有的对应编号，显示出下拉小箭头列表（如：我在物料名称栏输入变频器，下方的规格型号自动出现0-121和0-122等等）。
    在输入信息入库时，如果对应的数据已有，就自动在这一行添加对应的库存数量：如果没有就添加新一行。以编号为依据。如果编号和名称都有但是单位不同，把后入库的单位系统改成和上一个在库中的单位一致。
    入库时，若信息已有，当我输入完物料编号之后，自动补全其他编号的信息，根据数据库数据源。

②出库：显示物料编号和物料名称两个名称，输入完成且匹配一致后点击出库，对应系统中的数据相应减少，若数据库中没有则提示出库失败。
   鼠标点击先对应一行，再点击出库按钮后，显示弹框，显示不可更改的物料编号和物料名称信息，显示可输入的出库数量框，确认出库后，系统对应数量做出相减。
    系统中对应的备件数量小于0时，直接删除这一条数据。

③**导入**

​	1、功能：准备一个有11列数据的一个excel表，点击导入后可以从桌面上选中并把数据添加进系统中，并对已有的数据进行覆盖（加一个点击后的警示提示：数据会进行覆盖），导入时系统中的时间会自动添加。

​	2、读取Excel的9个列，并映射到数据库字段，排除id和last_update，这两个字段通过SQL语句实现自动生成。检查Excel是否包含所有必需列，使用`pd.to_numeric`安全转换数值类型，自动处理空值（NA转为0或1），单条记录失败不影响其他记录导入，详细错误输出到控制台，用户界面显示简明错误提示

​		

2025/4/10

④**导出**：导出一个excel文件表（命名：备件物料表+当时时间），表中显示11行的数据表。

⑤**导入**：，


#### 注意：

​    ①安装Visual studio Code
​    ②下载python解释器
​    ③vscode配置python插件
​    ④在vscode的终端：检查pip是否最新 

```
python -m pip install --upgrade pip
```

 ⑤ 更换pip源

```
pip install pandas -i https://pypi.tuna.tsinghua.edu.cn/simple
```

 ⑥下载git , 在vscode的终端配置用户名和邮箱

```python
git config --global user.name "你的GitHub用户名"       
git config --global user.email "你的GitHubemail"  
```

 ⑦验证是否成功 

```
git config --globle --list
```

​    **1. 在 GitHub 上创建仓库**
   \- **步骤**：

​     1. 访问 [GitHub New Repository](https://github.com/new)。

​     2. 填写仓库名称 `innoventrySystem`。

​     3. 选择 **Public（公开）** 或 **Private（私有）**。

​     4. **不要勾选** “Initialize this repository with a README”（避免与本地仓库冲突）。

​     5. 点击 **Create repository**。



   **结果**：获取远程仓库的 URL，如：https://github.com/你的用户名/innoventrySystem.git
 **2. 在 VS Code 中关联并推送代码**
   \- **步骤**：

1、打开项目根目录（确保已初始化 Git 仓库）。

2、在终端执行以下命令关联远程仓库（替换为你的 URL）
git remote add origin https://github.com/你的用户名/innoventrySystem.git

3、**强制推送**（如果本地仓库已有文件且与远程冲突）：
git push -u origin main --force
\- 如果分支是 `master`，替换 `main` 为 `master`。

4、**正常推送**（如果本地是全新仓库）
	点击推送

