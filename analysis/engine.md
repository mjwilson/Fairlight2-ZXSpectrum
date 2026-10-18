# 3D engine

From what I can see, the 3D engine is very similar to that in Fairlight 1.

I found these routines corresponding to the FL1 code:

See [Fairlight 1 analysis](https://github.com/VilleKrumlinde/FairlightZ80/blob/main/analysis/overview.md)


| Label |Address |Comment |
| ----------- | ----------- | ----------- |
|`RTN_ZX_RowAddr`|6590|Believe this is equivalent functionality although the code looks different|
|`Fill_SpanFound`|6ED7|We manually reset bits 0,1 of E instead of clearing to 0|
|`Fill_SetupRows`|6EE1||
|`Fill_LookupTexture`|6F18||
|`Fill_StartPixelLoop`|6F2E||
|`Fill_CheckAboveBounds`|6FBF||
|`Fill_CheckRowBounds`|6FC2|Checks bit 0 instead of bit 1 of E|
|`Fill_AboveExhausted`|6FCB||
|`Fill_PushNewRow`|6FCD|Some slight differences from FL1 code but very similar|
|`Fill_WrapLeft`|6FE4|Confirmed called during fill|
|`Rtn_Iso_Project`|7559||
|`DropItem_TestPlacement`|7fbf||
|`RTN_Trigger_Room_Change`|844d||
|`RTN_Refresh_Shape_Data`|8482||
|`Collision_TestOneObject`|8866||
|`RTN_Test_Move_Blocked`|8831||
|`RTN_Load_Room_Objects`|88BD|Some differences in the code here, possibly because the room structure is different|
|`RTN_Cull_Sprites`|8a98||
|`RTN_ObjectPtr_FromIndex`|8b7b||
|`Rtn_Sort_And_Draw_Sprites`|8b89||
|`Rtn_ComputeSortKey`|8def||
|`Rtn_ComparePOsition`|8c2c||
|`Rtn_DrawSprite`|8c46||
|`Rtn_ClearBuffer_256`|8e05||
|`Rtn_ClearBuffer_512`|8e09||