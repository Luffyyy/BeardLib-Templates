# PD2-Templates
Templates for creating bunch of mods using the power of BeardLib!

## 3 Localization Types
BeardLib used JSON for localization since forever, but JSON posed a few issues for people that liked to edit it by hand. It's not very friendly, it's strict and hard to write multilines with it. These things are fixed in JSON5, but unfortunately there's no Lua package to add JSON5 as of yet.

Then at a later point BeardLib added YAML, I decided to use it for BeardLib's own localization files. YAML is mostly fine for localization and is friendlier.

Then in BeardLib 4.6 the 3rd was added - Lua itself! Lua has been used for localization too in many mods, it being Lua by itself, means you can use its full potential. Thanks to a SBLT function `blt.vm.dofile` I was able to make it as straight forward as possible. So all you need to do is do your localization as usual and just return a table like so: 
```lua
return {
  string_id: "Hello!"
}
```
