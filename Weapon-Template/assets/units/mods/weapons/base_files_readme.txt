Custom weapon base:
To create base for custom weapon you need reuse weapon base files from PD2 that custom weapon will be using. After extracting files by using one of tools you will need these 5 files:

.cooked_physics		- In case of weapons it don't contains any physics data but be present.
.model				- Contains data about bones, animations and other undiscovered data.
.object				- Mostly contains what animations are enabled.
.unit				- Weapon base.
_npc.unit			- Weapon base when used by AI.

Other files found in base folder are not needed for custom weapon base. After renaming these files and adding them to XML you will need edit data in following files:

.unit

In unit file path to object file and "base" - "name_id" must be changed.

_npc.unit

In npc unit only path to object file must be changed.

--------------------------------------------------------------------------------------------------------------------

For example lets breakdown template unit files and how they are configured correctly for data stored in XML.

>> wpn_fps_YOUR_WEAPON_NAME.unit

<unit type="wpn" slot="1" >
    <object file="units/mods/weapons/wpn_fps_YOUR_WEAPON_NAME/wpn_fps_YOUR_WEAPON_NAME" />	-- Object Path
	<dependencies>
		<depends_on bnk="soundbanks/weapon_m4"/>
		<depends_on bnk="soundbanks/weapon_tecci"/>
	</dependencies>
    <extensions>
        <extension name="unit_data" class="ScriptUnitData" />
        <extension name="base" class="NewRaycastWeaponBase" >
			<var name="name_id" value="YOUR_WEAPON_NAME" /> 										-- Base name_id (Unique ID of custom weapon)
		</extension>
    </extensions>
</unit>

>> wpn_fps_YOUR_WEAPON_NAME_npc.unit

<unit type="static" slot="1" >
    <object file="units/mods/weapons/wpn_fps_YOUR_WEAPON_NAME/wpn_fps_YOUR_WEAPON_NAME" />	-- Object Path
	<dependencies>
		<depends_on bnk="soundbanks/weapon_m4"/>
	</dependencies>
    <extensions>
        <extension name="unit_data" class="ScriptUnitData" />
        <extension name="base" class="NewNPCRaycastWeaponBase" >
			<var name="name_id" value="m4_crew" />
		</extension>
    </extensions>
</unit>