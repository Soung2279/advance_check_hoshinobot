# Advance_check for Hoshinobot
***

→→→ [前往更新日志](#更新日志)

## bot 服务器检查


### 功能介绍

利用 python库-[WMI](https://pypi.org/project/WMI/) 查询电脑硬件配置相关信息。并定时向超级用户发送当前服务器全屏截图。
**仅** 适用于 **Windows** 平台 Bot。

~~人称小鲁大师~~

查询的信息如下：
- 获取 **电脑使用者** 信息
- 获取 **操作系统** 信息
- 获取 **电脑IP和MAC** 信息
- 获取 **电脑CPU** 信息
- 获取 **BIOS** 信息
- 获取 **磁盘** 信息
- 获取 **显卡** 信息
- 获取 **内存** 信息
- 获取 **服务器当前全屏截图**
- ……


默认需要 **@bot** 使用，可以自己改成无需@。在 **advance_check.py** 文件里有可用的注释

### 安装

#### 通过github克隆

在 ``hoshino/modules`` 文件夹中，运行 ``cmd`` 或者 ``powershell`` ，输入以下代码按回车执行：

```powershell
git clone https://github.com/Soung2279/advance_check_hoshinobot.git
```

之后不要关闭 ``cmd`` 或 ``powershell`` 窗口，输入以下代码安装依赖

```powershell
py -3.9 -m pip install -i https://pypi.tuna.tsinghua.edu.cn/simple -r requirements.txt
# 如果你是python 3.8，请改为 py -3.8 ......
```

或

```powershell
pip install wmi
```

之后关闭 ``cmd`` 或 ``powershell`` 窗口，前往 ``hoshino/config`` 的 `__bot__.py` 文件，在 ``MODULES_ON = {}`` 里添加 "advance_check"
```python
# 启用的模块
MODULES_ON = {
    'xxx',
    'advance_check',  #注意英文逗号！
    'xxx',
}
```

#### 直接安装

直接下载本仓库源码 [advance_check_hoshinobot](https://github.com/Soung2279/advance_check_hoshinobot/archive/refs/heads/main.zip) ，将其放入hoshino/modules中，并安装依赖 [WMI](https://pypi.org/project/WMI/)

提供如下安装依赖代码，可直接复制到 ``cmd/powershell`` 当中，按回车执行。

```powershell
pip install wmi
```

之后关闭 ``cmd`` 或 ``powershell`` ，在 ``hoshino/config`` 的 `__bot__.py` 文件中，在 ``MODULES_ON = {}`` 里添加 "advance_check"

```python
# 启用的模块
MODULES_ON = {
    'xxx',
    'advance_check',  #注意英文逗号！
    'xxx',
}
```

### 指令

- **`[@bot adcheck/鲁大师/看看配置/看看服务器/adck]`** 看看服务器硬件配置

- **`[帮助advance_check]`** 查看详情

- **`[服务器截图/bot截图]`** 查看当前时间服务器全屏截图

- **`[清理adck/清除adck]`**  清空截图文件夹

- **`[启用adcheck_push]`**  启用定时推送服务，将于每日特定时间推送全屏截图给第一位 **超级管理员**

### 自定义内容

在 **[advance_check.py](https://github.com/Soung2279/advance_check_hoshinobot/advance_check.py)** 文件的第 **28** 行可自行设置**需要收到消息的超级管理员**

```python
...
receiver = hoshino.config.SUPERUSERS[0]  #需要收到消息的超级管理员,[0]表示第一位,[1]表示第二位
# 也可直接填写qq号
...
```

在 **[advance_check.py](https://github.com/Soung2279/advance_check_hoshinobot/advance_check.py)** 文件的第 **22-26** 行可自行设置是否启用**合并转发**和**定时撤回**功能

```python
forward_msg_exchange = 1  #是否启用合并转发。1是启用，0是禁用
forward_msg_name = '在这里输入合并转发的呢称'  #转发用的昵称
forward_msg_uid = '756160433'  #转发用的UID，懒得想或者要用官方的UID可以参考下面
recall_msg_set = 1  #是否启用定时撤回。1是启用，0是禁用
RECALL_MSG_TIME = 30  #撤回前的时长，单位s
```

在 **[advance_check.py](https://github.com/Soung2279/advance_check_hoshinobot/advance_check.py)** 文件的第 **213，214和232** 行需同步设置**截图存放路径**

```python
    shots_all_num = countFile(str(main_path+"img/advance_check/"))  #同上
    shots_all_size = getdirsize(f"{main_path}img/advance_check/")  #同上
...
    after_size = getdirsize(f"{main_path}img/advance_check/")  #同上
```

同理，在 **[advance_check.py](https://github.com/Soung2279/advance_check_hoshinobot/advance_check.py)** 文件的第 **205** 行可自行设置**截图存放路径**

>默认的截图存放为 你的资源库目录/img/advance_check/

>例如: D:/Resources/img/advance_check/

在 **[advance_check.py](https://github.com/Soung2279/advance_check_hoshinobot/advance_check.py)** 文件的第 **394，410和426** 行可自行设置**每日推送时间**

```python
@svadpush.scheduled_job('cron', hour='9', minute='30')  #每天9:30推送
...
@svadpush.scheduled_job('cron', hour='14', minute='30')  #每天14:30推送
...
@svadpush.scheduled_job('cron', hour='20', minute='30')  #每天20:30推送
```


### 其它

本人非专业程序员，业余写着玩玩，代码很菜，大佬们看看就好QwQ。

made by [Soung2279@Github](https://github.com/Soung2279/)

### 鸣谢

灵感来源：自检[check](https://github.com/pcrbot/Hoshino-plugin-transplant#%E8%87%AA%E6%A3%80)  作者 **[Watanabe-Asa](https://github.com/Watanabe-Asa?tab=repositories)**

### 更新日志

2021-9-10

【新增】
获取服务器当前全屏截图，支持手动查询和自动推送，需安装依赖 shutil ，需为 Windows 环境。
截图文件夹默认为 /img/advance_check/，可[前往自定义内容](#自定义内容)查看更改
推送时间默认为 每天9：30，14：30和20：30推送。可[前往自定义内容](#自定义内容)查看更改

【更新】
部分逻辑代码优化。

2022-7-10

【更新】
更新README，优化代码逻辑

移除了对Linux的支持。

对于Linux等非Windows平台，有更优选的插件：[sys_stats_HoshinoBot](https://github.com/pcrbot/sys_stats_HoshinoBot) - [轻尘](https://github.com/SlightDust)