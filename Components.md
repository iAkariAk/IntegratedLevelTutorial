# 组件文档 0.4.3 & 0.4.4

## 目录

- [组件文档](#组件文档)
  - [目录](#目录)
  - [AutoZombiePoint 组件](#autozombiepoint-组件)
  - [LevelProperty 组件](#levelproperty-组件)
  - [BungeeBlitz 组件](#bungeeblitz-组件)
  - [ColumnPlanting 组件](#columnplanting-组件)
  - [ConveyorBelt 组件](#conveyorbelt-组件)
  - [DefaultPlantOnLawn 组件](#defaultplantonlawn-组件)
  - [ManualZombiePoint 组件](#manualzombiepoint-组件)
  - [MustHaveZombie 组件](#musthavezombie-组件)
  - [OverrideZombieProperty 组件](#overridezombieproperty-组件)
    - [例子](#例子)
  - [SeedBank 组件](#seedbank-组件)
  - [SpawnFog 组件](#spawnfog-组件)
  - [SpawnGraveStone 组件](#spawngravestone-组件)
  - [VaseLevel 组件](#vaselevel-组件)
  - [Tool 组件](#tool-组件)

---

## AutoZombiePoint 组件

此组件代表关卡自动增长出怪点数，不可与 ManualZombiePoint 同时使用。

- **初始出怪点数 (StartingPoints)**: `int`, 默认值: `1`，出怪时的初始点数。
- **出怪点数增速 (PointIncrementPerWave)**: `float`, 默认值: `0.333334`，每一波僵尸后的出怪点数增加量。
- **一大波僵尸时出怪点数倍率 (FlagPointMultiplier)**: `float`, 默认值: `2.5`，一大波僵尸时的出怪点数乘数。

---

## LevelProperty 组件

该组件定义了关卡的基本信息，是关卡必备的组件，包含关卡名、作者、背景等基本属性。

- **关卡名 (Name)**: `string`, 默认值: `null`，关卡的名称。
- **作者 (Creator)**: `string`, 默认值: `null`，关卡的作者。
- **背景 (Background)**: `int`, 默认值: `0`，关卡的背景类型。
- **初始植物列数 (InitPlantColumn)**: `int`, 默认值: `0`，关卡中初始可种植植物的列数。
- **紫卡是否不用种在对应绿卡上 (EasyUpgrade)**: `bool`, 默认值: `false`，是否允许紫卡无需种植在绿卡之上。
- **僵尸波数 (NumWaves)**: `int`, 默认值: `40`，僵尸波数的总数。
- **多少波僵尸算一面旗帜 (WavesPerFlag)**: `int`, 默认值: `10`，每一面旗帜的僵尸波数。
- **初始阳光数 (StartingSun)**: `int`, 默认值: `50`，关卡开始时的阳光数。
- **初始波数 (StartingWave)**: `int`, 默认值: `0`，关卡开始时的初始僵尸波数。
- **初始出怪等待时间 (StartingTime)**: `int`, 默认值: `1800`，游戏开始时出怪的等待时间。
- **可出现的僵尸 (AllowedZombies)**: `List<int>`, 默认值: `null`，本关卡允许出现的僵尸类型，如`[0,2]`代表本关可出现普通僵尸，路障僵尸。
- **是否出现旗帜僵尸 (SpawnFlagZombie)**: `bool`, 默认值: `true`，是否允许一大波僵尸出现时自动刷出旗帜僵尸。
- **最大刷出普通僵尸数 (MaxPlainZombiesPerFlag)**: `int`, 默认值: `8`，一大波僵尸强制出现普通僵尸的最大数量。
- **背景音乐种类 (MusicType)**: `int`, 默认值: `-1`，背景音乐种类，-1为默认，0为不播放。

---

## BungeeBlitz 组件

此组件代表关卡出怪为天上的蹦极僵尸放僵尸。

- **一大波僵尸时是否提示蹦极僵尸来袭 (ShowHugeFlagAdvice)**: `bool`, 默认值: `true`，一大波僵尸时是否提示蹦极僵尸来袭。

---

## ColumnPlanting 组件

此组件代表关卡种植植物时一次种一列。

- **种植时间 (PlantTime)**: `int`, 默认值: `1000`，植物种植的时间（假设值，如果没有默认值请忽略）。

---

## ConveyorBelt 组件

此组件代表关卡为传送带关卡，不可与 SeedBank 同时使用。

- **可出现的植物和权重 (AllowedPlants)**: `List<(int, int)>`, 默认值: `[]`，可以出现的植物及其权重，如`[[0,30],[2,15]]`代表可出现豌豆射手（权重30）和樱桃炸弹（权重15）。
- **初始植物 (InitCards)**: `List<int>`, 默认值: `null`，初始传送带上的植物，如`[0,0,2]`代表初始依次出现豌豆射手，豌豆射手，樱桃炸弹。
- **等待时间倍率 (PrepareTimeMultiplier)**: `float`, 默认值: `1.0`，传送带植物出现的准备时间倍率。

---

## DefaultPlantOnLawn 组件

此组件代表关卡加载时生成一系列植物。

- **初始植物列表 (Plants)**: `List<(int, int, int)>`, 默认值: `[]`，关卡初始时生成的植物列表，三个值分别为植物类型，列数，行数，列数和行数从0开始计算，如`[[69,1,0],[69,1,1],[69,1,2],[69,1,3],[69,1,4],[69,1,5]]`代表关卡开始前在第1列0-5行分别种植胡萝卜导弹车。

---

## ManualZombiePoint 组件

此组件代表关卡手动指定出怪点数，不可与 AutoZombiePoint 同时使用。

- **每一波僵尸的出怪点数 (Density)**: `List<int>`, 默认值: `[]`，每波僵尸的指定出怪点数，元素数必须与LevelProperty组件指定的关卡波数相等。

---

## MustHaveZombie 组件

此组件代表关卡拥有特定波数必须出现的僵尸。

- **必须出现的僵尸列表 (Zombies)**: `List<(int, List<int>)>`, 默认值: `[]`，必须出现在某些波数的僵尸列表，两个值分别为波数，出怪列表，波数从0开始计算，如`[[12,[2,23,23]],[13,[0,0]],[14,[23]]]`代表第12波必出一个路障僵尸和两个巨人僵尸，第13波必出两个普通僵尸，第14波必出一个巨人僵尸。

---

## OverrideZombieProperty 组件

此组件代表关卡拥有需要特殊指定属性的僵尸。

- **僵尸属性列表 (Properties)**: `List<ZombieProperty>`, 默认值: `[]`，需要特殊指定属性的僵尸列表。
  - **僵尸属性 (ZombieProperty)**:
    - **ZombieType**: `int`, 必选值，僵尸类型。
    - **BodyHealth**: `int`, 僵尸本体血量。
    - **HelmHealth**: `int`, 僵尸头饰血量。
    - **ShieldHealth**: `int`, 僵尸手持物血量。
    - **FlyingHealth**: `int`, 僵尸飞行物血量。
    - **ZombieValue**: `int`, 僵尸点数。
    - **FirstAllowedWave**: `int`, 僵尸首次出现的波数，从0开始计算。
    - **PickWeight**: `int`, 僵尸出现权重。
    - **CanGoInPool**: `bool`, 是否可在泳池出现。
    - **CanGoOnHighGround**: `bool`, 是否可在高地出现。

### 例子

下述示例作用是
1. 设置渔夫僵尸血量为6000
2. 设置气球僵尸本体血量500，气球血量40，点数为1，首次出现波数为0，出现权重为1000

```json
{
  "Type": "OverrideZombieProperty",
  "Properties": [
    {
      "ZombieType":74,
      "BodyHealth":6000
    },
    {
      "ZombieType": 16,
      "BodyHealth": 500,
      "FlyingHealth": 40,
      "ZombieValue": 1,
      "FirstAllowedWave": 0,
      "PickWeight": 1000
    }
  ]
}
```

---

## SeedBank 组件

此组件代表关卡为普通选卡关卡，不可与 ConveyorBelt 同时使用。

- **卡槽数 (NumPackets)**: `int`, 默认值: `-1`，卡槽的数量，-1代表和玩家拥有的卡槽数相同。
- **禁止选择的卡片列表 (BannedCards)**: `List<int>`, 默认值: `null`，被禁止选择的卡片列表，如`[0,1,2]`代表禁止选卡豌豆射手，向日葵，樱桃炸弹。
- **锁定选择的卡片列表 (LockedCards)**: `List<int>`, 默认值: `null`，被锁定选择的卡片列表，如`[0,1,2]`代表锁定选卡豌豆射手，向日葵，樱桃炸弹。
- **是否需要手动选卡 (UserChoose)**: `bool`, 默认值: `true`，是否需要玩家手动选卡。

---

## SpawnFog 组件

此组件代表关卡出现浓雾。

- **浓雾列数 (Column)**: `int`, 默认值: `3`，关卡中出现浓雾的列数。

---

## SpawnGraveStone 组件

此组件代表关卡出现墓碑。

- **每一列的墓碑数 (CountPerColumn)**: `int[9]`, 默认值: `[0,0,0,0,0,0,0,0,0]`，每一列出现的墓碑数，生成位置在相同列随机，每一列最多出现六个墓碑，如`[2,2,2,2,2,2,2,2,2]`代表每一列都出现两个墓碑。

---

## VaseLevel 组件

此组件代表关卡为砸罐子关卡。

- **最小生成罐子的列数 (MinColumn)**: `int`, 默认值: `4`，最小生成罐子的列数，列数从0开始计算。
- **最大生成罐子的列数 (MaxColumn)**: `int`, 默认值: `8`，最大生成罐子的列数，列数从0开始计算。
- **出现的植物列表 (PlantVases)**: `List<(int, int)>`, 默认值: `[]`，在罐子中出现的植物列表，两个值分别为植物种类和个数，如`[[2,2],[20,2],[15,1]]`代表生成2个樱桃炸弹，2个火爆辣椒，1个末日菇。
- **出现的僵尸列表 (ZombieVases)**: `List<(int, int)>`, 默认值: `[]`，在罐子中出现的僵尸列表，两个值分别为僵尸种类和个数，如`[[0,6],[7,5],[18,5],[8,3],[23,1]]`代表生成6个普通僵尸，5个橄榄球僵尸，5个蹦蹦僵尸，3个舞王僵尸，1个巨人僵尸。
- **必出植物的罐子数 (NumPlantVases)**: `int`, 默认值: `3`，生成必定包含植物的绿色罐子数。
- **必出僵尸的罐子数 (NumZombieVases)**: `int`, 默认值: `0`，生成必定包含僵尸的灰色罐子数。

---

## Tool 组件

此组件代表关卡道具是否可用。

- **是否出现铲子 (ShowShovel)**: `bool`, 默认值: `true`，关卡内是否显示铲子。
- **是否出现锤子 (ShowMallet)**: `bool`, 默认值: `false`，关卡内是否显示锤子。
- **是否出现阳光500 (ShowGoldFinger1)**: `bool`, 默认值: `false`，关卡内是否显示阳光500道具。
- **是否出现樱桃风雷 (ShowGoldFinger2)**: `bool`, 默认值: `false`，关卡内是否显示樱桃风雷道具。
- **是否出现极速冷却 (ShowGoldFinger3)**: `bool`, 默认值: `false`，关卡内是否显示极速冷却道具。

---
