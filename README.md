# AR游戏 - 正牌天神

## 游戏简介

这是一款AR第三人称塔防游戏，游戏中玩家扮演天神，协助信仰之塔里的子民抵御来自四面八方的邪恶怪物的围攻。

## 游戏亮点

1. 游戏采用AR技术，增强玩家与环境空间的交互体验，带给玩家不同于传统伪3D手游的新感觉。
2. 游戏难度循序渐进，初期让玩家能熟悉玩法，及时排兵布阵；后期难度逐步提升，愈发考验玩家的操作和意识。
3. 游戏过程中奖励机制合理，适度的奖励使得玩家愿意继续闯关，而又不会因奖励过多打乱难度设置而使玩家觉得无聊。

## 团队简介

| 学号 | Github账号 | 分工 |
|:-:|:-:|:-:|
| 15336250 | keven2148 | 展示ppt等文档编写 |
| 15331087 | JacKnights | 游戏场景设计，代码编写及AR配置运行 |
| 15331094 | gzm1997 | 游戏素材收集 |
| 15331049 | Chengwch | 策划文档编写 |


## 开发与模型需求

### 开发需求

**开始界面：**开始界面可选择3个关卡，其中仅有第一关解锁，第二第三关未解锁不可点击。

**第一关：**

##### 配件:

- **地图：** 细节待定，主要考虑因素为地图大小，坐标定位，地图单位长度，怪物出生点，怪物行进路线。
- **信仰之柱：** 血量，防御值，等级。随等级增长防御和血量都增长。 
- **广场大门**：怪物出生点，所在位置
- **步兵：** 拥有属性攻击力，攻击范围（近战，仅可攻击地面单位），攻击范围（单体），攻击频率，级别（初，中，高三个级别，每个级别分3个等级）。随等级增长攻击力与攻击速度提高，成长公式为$初始属性 + 成长系数*等级 $
- **魔法之塔**：拥有的属性有攻击力，攻击范围（远程），攻击频率，级别（分为初始与初级两级，每个级别分4个小级），初级魔法之塔拥有初级魔法火球，可对小范围敌人造成定额伤害。魔法之塔随等级提升，全属性提升，成长公式与步兵相同。
- **怪物**：拥有的属性有攻击力，攻击距离，防御，血量，行进速度，行进方式（空中或地面）。第一关有红色与橙色怪物，都是地面单位。

##### 设定：

- 所有拥有血量的单位头上都会有血条，长度越长血量越高。


- 只有一个怪物出生点，当次波怪物完全被消灭时，刷新下一波怪物。怪物按固定路线前进，当怪物进入作战单位攻击范围时，作战单位自动对怪物发起攻击（优先最近单位or优先血量最少）

- 玩家通过点击作战单位进行选中，信仰之柱与步兵弹出升级选项，满级时升级选项不可选。初级魔法之塔弹出升级与释放魔法选项，对魔法图标长按拖动可释放魔法。其余目标不可选中。

- 怪物向信仰支柱前进，当信仰之柱进入怪物攻击范围时，怪物对信仰之柱发起攻击。当信仰之柱血量为0时，弹出游戏结束界面，有重新开始与退出两个选项，退出则退回开始界面。

- 当所有怪物被消灭，弹出闯关成功界面，有进入下一关和退出两个选项，由于第二关暂未开发，此时点击进入下一关选项无法选中。点击退出则退回主界面，此时第二关按钮解锁。

- 游戏中伤害计算公式$攻击 - 防御 = 伤害$



### 美术需求：

信仰之柱模型，生成与销毁动画。

魔法之塔，步兵模型及生成动画。

怪物模型（可同一模型不同颜色），出生与销毁动画，前进动作。


## 策划文档

### 1. 基本信息

- **游戏名称：**正牌天神


- **游戏类型**：单人SLG塔防类
- **游戏概述：** 这是一款运行在安卓平台简易塔防类手游，核心玩法是玩家采取一切手段抵御怪物进攻，保护己方基地。游戏一共分为3个关卡，每一关的游戏场景（地图）为固定场景，怪物从固定位置生成，不断向基地发起进攻，玩家可通过操作己方作战单位，对作战单位升级等抵挡怪物进攻，达到特定条件后可进入下一关。

### 2. 游戏背景

   天神（玩家）的子民们生活在一个城堡中，居民们通过信仰之柱对天神供奉。天神通过信仰之柱汲取信仰之力让增加自身修为，同时利用自身神力对子民反馈，保佑城堡一方安宁。

有一天，天神的子民中出现了背叛者，将灵魂献祭给恶魔获得了强大的实力。他开始觊觎天神的信仰之力，妄图取而代之成为新的天神，掌控城堡让城堡为他服务，于是他将城堡外的动物异化成怪物，对信仰之柱发起了进攻。天神为了阻止这场灾难，捍卫自己的地位，组织起城堡里的作战单位抵御进攻，最终城堡沦陷，天神组织最后的战力在信仰之柱所在的广场进行最后一战。



### 3. 游戏设定

#### 操作方式：

玩家通过排石特定场景加载游戏地图，点击游戏中的单位进行选中，点击弹出的选项选择对单位进行操作，通过滑动到指定位置的方式释放主动技能。

#### 信仰系统：

作战单位通过击杀怪物增加士气，进而为天神提供信仰之力，转化为天神（玩家）的修为。玩家可通过消耗修为为作战单位升级，也可以消耗修为释放魔法。



#### 游戏配件：

- **信仰之柱：** 怪物进攻的目标，也是玩家守护的对象，一旦信仰之柱被怪物摧毁，游戏失败。
- **广场大门：**  进入广场的大门，怪物出生点。
- **步兵：**近战作战单位，可对地面怪物进行攻击，一共有三种形态，**初级→中级→高级**，每种形态分为3级。
- **魔法之塔：**：远程作战单位，可攻击地面怪物与空中怪物，分4种形态，**初始→初级→中级→高级**，每种形态分为4级。其中初级形态可释放初级魔法火球，中级可释放中级魔法沙龙卷，高级形态可释放高级魔法暴风雪。
- **大地之塔**：辅助型作战单位，共2种形态**初级→高级**，每种形态分为3级。初级仅可使用大地之力铸造大地壁垒阻挡怪物进攻（无法阻挡空中单位），高级还可召唤陨石降落，对怪物造成伤害与减速。
- **红色怪物：**怪物喽啰，行进速度慢，攻击力低，血量低。
- **橙色怪物：**拥有较高的攻击，行进速度块，血量低。
- **黄色怪物**：拥有高额血量，行进速度慢，攻击低。
- **青色怪物：**空中作战单位，行进速度超快，攻击力一般，血量低。
- **怪物头领：**每种怪物都有一个头领，属性是普通怪物的3倍。

### 4. 玩法流程

#### 第1关：

**怪物出生点:**1个

**怪物波数：**5

**怪物种类：**红色怪物与橙色怪物混合。每一波怪物数量增加，橙色怪物的比重增，第三波出现红色首领，最后一波出现橙色首领。

**作战单位：**1个步兵,1座魔法之塔。其中步兵与魔法之塔仅可升级至中级。

**通关条件：**消灭所有怪物

**流程图**

![第一关流程](https://github.com/TrueGodARGame/TrueGodGame/blob/master/Document/%E7%AC%AC%E4%B8%80%E5%85%B3%E6%B5%81%E7%A8%8B.png)


## 设计文档

### 1 总体印象
这款游戏专注制造破坏的快感，是使用破坏方块，使方块碎块四溅的方式展示破坏效果的单人游戏
### 2 故事
### 2.1 场景
游戏发生在一个堡垒附近，以堡垒为场景的核心
### 2.2 人物
故事的人物有：作为神的玩家，NPC
### 2.3 事件
出现的NPC突然攻打玩家的堡垒，在天上观望（拿着手机）的玩家需要用所有他能用到的办法保护自己的堡垒

### 3 游戏结构
该游戏由不同的关卡组成，不同的关卡NPC的强度和能力会不同，玩家可以使用的动作的种类也不同，按照难度逐渐升级。场景也会因为关卡的不同发生些许变化（例如：天气，地面，昼夜）

### 4 玩家
这是单人游戏
### 5 玩家动作
玩家在游戏里被允许
* 点击屏幕射击NPC
* 拖动魔法卡片，指定释放点，释放魔法
* 花费金币（游戏中的货币）升级堡垒血量和修复堡垒
* 花费金币雇佣友军攻击来犯的NPC
* 花费金币购买堡垒的防御设备和外观
* 花费金币升级自身射击和魔法能力
### 6 游戏目标
### 6.1 剧情关卡
玩家要在杀死所有来犯NPC前保护好堡垒免于崩塌
在没有崩塌的前提下，会有分数计数
分数受玩家杀死敌人数，堡垒残余HP，接收友好NPC难民的奖励分数影响
### 6.2 无尽关卡
NPC的数量是无数的，玩家需要在堡垒崩塌前尽可能击杀更多的NPC

### 7 游戏原型
### 7.1 地形
地形将会被摄像机从上往下摄影。由玩家手持手机对指定识别图拍摄，在识别图上生成游戏地形。
地形将会采用使用“MagicaVoxel.exe”制作的，或类似风格的像素风格模型
地形需要有一定的根据特效修改自己的能力，例如：血迹残留，爆炸和闪电留下烧灼的黑色痕迹
摄像机的拍摄方向和高度跟随玩家的手机而定
### 7.2 模型
模型采用“MagicaVoxel.exe”制作的，或相似风格的体素风格模型，包括
* 不同的NPC敌人（包括NPC难民），种类4种以上（近战自爆兵，远程射击兵，NPC难民，Boss）
* 友军
* 防御工事
* 堡垒，包含升级后不同的外观
* 攻击特效的模型（例如：箭矢，火球，投石，炮弹）
### 7.3 屏幕显示

### 7.3.1 UI板
具体UI设计等待UI的结构文档
本文档只提出需要的UI功能
* 暂停，重新开始，放弃本次游戏返回主菜单
* 友军购买
* 魔法使用
* 升级城堡
### 7.3.2 着色器
着色器大部分使用默认“diffuse（漫反射）”，模拟不透明，低反光率，颜色饱和度高的方块材质

### 7.3.3 天气
使用不同的天空盒模拟不同的天气光部署

## 代码仓库

[游戏代码链接](https://github.com/TrueGodARGame/TrueGodGame/tree/master/TrueGod/Assets/Scripts)

## Gif动画

![Gif: TrueGod](https://github.com/TrueGodARGame/TrueGodGame/blob/master/TrueGod.gif)

## 展示视频

[视频网址](https://pan.baidu.com/s/1n-JWl5VKEX1IB_jquwkD2w
15336)

## 游戏下载链接

[Download: TrueGod](https://github.com/TrueGodARGame/TrueGodGame/blob/master/TrueGod.apk)