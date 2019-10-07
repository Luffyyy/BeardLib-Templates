Custom attachments assets:
To add custom attachment for custom model that you have exported to model already you will need reuse other files that of this model is using in PD2.  After extracting files by using one of tools you will need these 5 files:

.cooked_physics			- In case of weapons it don't contains any physics data but be present.
.material_config		- Textures and materials used for weapon.
.object					- Contains what animations are objects are enabled.
.unit					- Contains data about attachment base.
_thq.material_config	- Textures and materials used for weapon in third person.

Remaining material_config files (cc and cc_thq) are not needed. After renaming these files and adding them to XML you will need edit data in following files:

.material_config and _thq.material_config

Both files will have defined same materials for model objects adjust thier paths to correct texture files that are added in XML.

.object

Contains path to material_configs and you can select what objects of model are enabled or disabled (Not loaded at all).

.unit

Contains path to object file of custom attachment.

--------------------------------------------------------------------------------------------------------------------

For example lets breakdown a custom attachment files - wpn_fps_YOUR_WEAPON_NAME_stock_hk416c (HK416C Stock):

>> wpn_fps_YOUR_WEAPON_NAME_stock_hk416c.material_config

<materials version="3" group="weapon_group">
    <material name="standard_grip" render_template="generic:DEPTH_SCALING:DIFFUSE_TEXTURE:NORMALMAP:NORMALMAP_UV1" version="2">
        <diffuse_texture file="units/mods/weapons/wpn_fps_YOUR_WEAPON_NAME_pts/magpul_moe_df"/>									-- Path to diffuse.
        <bump_normal_texture file="units/mods/weapons/wpn_fps_YOUR_WEAPON_NAME_pts/magpul_moe_nm"/>								-- Path to normal map.
    </material>
</materials>

>> wpn_fps_YOUR_WEAPON_NAME_stock_hk416c_thq.material_config

<materials version="3" group="weapon_group">
    <material name="standard_grip" render_template="generic:DIFFUSE_TEXTURE:NORMALMAP:NORMALMAP_UV1" version="2">
        <diffuse_texture file="units/mods/weapons/wpn_fps_YOUR_WEAPON_NAME_pts/magpul_moe_df" mip="1"/>							-- Path to diffuse.
        <bump_normal_texture file="units/mods/weapons/wpn_fps_YOUR_WEAPON_NAME_pts/magpul_moe_nm" mip="1"/>						-- Path to normal map.
    </material>
</materials>

As we can see both files looks very similiar but there are 2 diffrences in third person one - material use diffrent "render_template" and textures can use only MIPMap level up to 1 (0 is full size) mostly to save memory.

>> wpn_fps_YOUR_WEAPON_NAME_stock_hk416c.object

<dynamic_object>
	<diesel materials="units/mods/weapons/wpn_fps_YOUR_WEAPON_NAME_pts/wpn_fps_YOUR_WEAPON_NAME_stock_hk416c" orientation_object="rp_wpn_fps_upg_ak_s_solidstock" /> -- Path to material_config.
	<graphics>
		<object name="g_g" enabled="true" />							-- Enabled object.
	</graphics>
</dynamic_object>

>> wpn_fps_YOUR_WEAPON_NAME_stock_hk416c.unit

<unit type="wpn" slot="1">
	<object file="units/mods/weapons/wpn_fps_YOUR_WEAPON_NAME_pts/wpn_fps_YOUR_WEAPON_NAME_stock_hk416c" />					-- Path to object.
	<extensions>
		<extension name="unit_data" class="ScriptUnitData" />
	</extensions>
</unit>