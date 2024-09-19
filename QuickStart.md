# PvZ Integrated Mod 自定义关卡 - 快速开始 0.4.5

```json
{
    "Version": 1,
    "Components": [
        {
            "Type": "LevelProperty",
            "Name":"PvZ Integrated Mod Docs",
            "Creator":"Akari",
            ...
        }
    ]
}
```

## 必要准备

1. 了解Json格式以及基础的计算机知识(~~至少会编辑保存文件~~)
2. 使用Integrated 0.4.5版本

## 安装

当前, 你需要把关卡`level{N}.json`放到`~/docs/levels/`目录下 (~代表游戏的安装目录)
然后在游戏中打开创意庭院, 找到DIY - {N}进入即可游玩
**注意 N只能是1到4之间的整数**

## 版本(Version)

版本(`Version`)最小值为1, 当关卡定义的版本与游戏版本不符合时, 游戏将会给出警告但仍可游玩, 但在某些情况下则会直接给出报错拒绝读取. 因此我们建议将`Version`设置为最新的游戏版本

## 组件(Component)

关卡结构采用组件式, 这意味着你能够灵活的结合各种组件创造出各种巧妙的关卡
组件分为必选组件和可选组件, 当前的必选组件只有`LevelProperty`
每个组件都含有`Type`属性, 它用指定组件的类型
你可以在[组件文档](Components.md)中查阅这些组件的详细信息

## 实战

接下来我们来编写一个简易的关卡
首先在~/docs/levels/中创建一个level1.json
填入如下内容
**注意: 下文的#XXX可看作注释, 它会被游戏忽略, 你可以删掉它**

```json
{
    "Version": 1,
    "Components": [
        {
            "Type": "LevelProperty",
            "Name":"Tuition",
            "Creator":"Akari",
            "Background": 1,
            "InitPlantColumn": 0,
            "#InitPlantColumn": "初始种植花盆, 荷叶的到n列. n=0则不种植",
            "EasyUpgrade": false, 
            "NumWaves": 10, 
            "#NumWaves": "波数",
            "WavesPerFlag": 5, 
            "#WavesPerFlag": "每5波算一个旗帜 第5, 10波是旗帜",
            "StartingWave": 1, 
            "#StartingWave": "初始波数",
            "StartingTime": 2400, 
            "#StartingTime": "第一波延时",
            "AllowedZombies": [0, 1, 2, 3, 4, 23],
            "#AllowedZombies": "允许的僵尸 [普通僵尸, 旗帜僵尸, 路障僵尸, 撑杆僵尸, 铁桶僵尸, 巨人僵尸] 参考ZombieType.txt"
        }
    ]
}
```

经过测试发现出怪相当均匀, 并不会随波数增加而增加, 那么如何使僵尸随波增加而增大呢
这时`ManualZombiePoint`和`AutoZombiePoint`便有了用武之地
**注意: 两个组件只能同时存在一个**

```json
{
    "Type": "ManualZombiePoint",
    "Desity": [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
    "#Desity": "数组的第N为即第N波的点数, 长度必须与LevelProperty指定的NumWaves相等"
}
```

尽管`ManualZombiePoint`更为灵活, 可以实现非线性的增长, 但是它却过于繁琐, 如果是简单的线性增长则可以使用`AutoZombiePoint`

```json
{
    "Type": "ManualZombiePoint",
    "StartingPoints": 6,
    "#StartingPoints": "初始点数",
    "PointIncrementPerWave": 2,
    "#PointIncrementPerWave": "每波增加的点数",
    "FlagPointMultiplier": 2.5,
    "#FlagPointMultiplier": "旗帜点数的倍数"
}
```

这两种控制点数的方式各有千秋, 可根据需求选择

至此, 你已经完成了简单的自制关卡, 你可以查阅[组件文档](Components.md)来了解如何自定义其他模式(如排山倒海, 砸罐子)以及进阶的出怪组件
