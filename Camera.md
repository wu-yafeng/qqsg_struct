# 游戏相机对象

``` cpp

// 含相机的坐标，跟随的实体等信息，可能可以用于编写观战和录像的插件，适合那些喜欢看大佬打架的围观群众
typedef struct Camera {
    void *vftable;
	int pad[4];
    // 图层，人物、陷阱、NPC、怪物都在某个图层中，同图层无单位体积碰撞，不同图层存在碰撞
	vector<void*> MapLayers;
	int unknown[9];
	GameTree<MapMetadata *> MapTree;
	int pad32[22];
    // 地图矩形 长和宽
	GRectangle MapRect;
	int pad40[6];

    // 屏幕的矩形
	GRectangle ScreenRect;

	int pad43;
    // 视角的位置
	CoordinateInfo FovPos;
    // 视角矩形大小
	GRectangle FovRect;
    // 浮点数的位置
	float CameraPosX;
	float CameraPosY;
	int unknown_0[2];
    // 当前角色的图层
	MapLayer *MasterLayer;
	int unknown4;
    // 角色位置偏移 三国这个游戏没用
	CoordinateInfo MasterPosOffset;
	int IsPlayAnimation;
    // fov的观察者信息，在播放动画的时候，人物的相机不跟随角色
	FovWatcher FovWatcher;
	int unknown_6[6];
    // 当前地图的id
	int CurrentMapId;
    // 全局的视角偏移，fov总是比角色往下一点，角色不是在地图的正中央
	CoordinateInfo GlobalPosOffset;
	int pad50[26];
	int todo2[7];

	int unknown_1[13];
    // 失明大遮罩
	int Shadow1;
	int unknown_2;
    // 失明小遮罩
	int Shadow2;
	int unknown3[25];
    // 当前地图的动态路径信息
	GameTree<MoveDynamicLapMeta *> DynamicLap;
	int unknown98[18];
	/// <summary>
	/// 镜头跟踪的目标坐标
	/// </summary>
	CoordinateInfo MasterPos;
	int pad100[20];
    // 当前玩家的id吧
	int PlayerId;
	int unknown100[100];
	int unknown200;
};


```
## Sample

暂无例子
