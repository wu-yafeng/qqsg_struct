# 玩家角色偏移量

``` cpp
// file Charactor.h

#include "status.h"

// playerinfo+0x304 玩家横轴速度结构
// playerinfo+0x330 玩家竖轴速度结构
typedef struct Speed {
	DWORD Unknown;
	// 速度值
	DWORD SpeedVal;
	DWORD Unknown2;
	
	// 速度向量
	DWORD SpeedVector1;
	DWORD SpeedVector2;
	DWORD SpeedVector3;
	DWORD SpeedVector4;
	
	DWORD UnknownFields[0x2C/4];
} *PSpeed;

// 可以自己去分析这块内存的数据，包含了（当前实体的坐标、名字、职业、国家、三国币、五铢、5维属性、基础生命值、当前生命值等等）
typedef struct PGameEntity
{
	DWORD UnknownBlock[0x304/4];
	// X轴移速
	PSpeed SpeedX;
	// Y轴跳跃高度
	PSpeed SpeedY;
	// Y轴移速 固定2000
	PSpeed SpeedUnknown;
    	DWORD UnknownBlock2[(0x8658-0x304-sizeof(PSpeed) * 3)/4];
    	// 树的状态根节点
	PPlayerStatusNode Root;
	// 树的最高根节点（此节点是默认拥有的，即玩家就算没有任何状态，也有此节点，如果 Root == TopRoot，则说明实体没有任何状态）
	PPlayerStatusNode TopRoot;
	// 树的节点数量
	DWORD Count;
};

```
