# materialsystem

### Functions:

#### materialsystem.arms\_material

`materialsystem.arms_material()`: table (material object)

Returns a reference to the arms material when 'Viewmodel arms' is enabled

#### materialsystem.chams\_material

`materialsystem.chams_material()`: table (material object)

Returns a reference to the player chams material

#### materialsystem.find\_material

`materialsystem.find_material(path: string[, force_load: boolean])`: table (material object)

| Argument        | Type    | Description                                   |
| --------------- | ------- | --------------------------------------------- |
| **path**        | string  | Path to material including filename           |
| **force\_load** | boolean | Boolean. Load the material if it isn't loaded |

Returns a reference to the material

#### materialsystem.find\_materials

`materialsystem.find_materials(partial_path: string[, force_load: boolean])`: table (material objects)

| Argument          | Type    | Description                                    |
| ----------------- | ------- | ---------------------------------------------- |
| **partial\_path** | string  | Partial path to material                       |
| **force\_load**   | boolean | Boolean. Load each material if it isn't loaded |

Returns a table of references to materials that have partial\_path in their name

#### materialsystem.find\_texture

`materialsystem.find_texture(path: string)`

| Argument | Type   | Description                        |
| -------- | ------ | ---------------------------------- |
| **path** | string | Path to texture including filename |

Returns a reference to the texture that can be used with set\_shader\_param

#### materialsystem.get\_model\_materials

`materialsystem.get_model_materials(entindex: number)`: table (material objects)

| Argument     | Type              | Description  |
| ------------ | ----------------- | ------------ |
| **entindex** | number (entindex) | Entity index |

Returns a table of references to materials used by the entity

#### materialsystem.override\_material

`materialsystem.override_material(material: table, material_new: table)`

| Argument          | Type                    | Description                      |
| ----------------- | ----------------------- | -------------------------------- |
| **material**      | table (material object) | The material to override         |
| **material\_new** | table (material object) | The material to override it with |

Overrides all of a material properties with another material.

#### :alpha\_modulate

`material_object:alpha_modulate(a: number)`

| Argument | Type   | Description                             |
| -------- | ------ | --------------------------------------- |
| **a**    | number | New alpha value of the material (0-255) |

Overrides the alpha of the material object it's called on. Doesn't work with some materials

#### :color\_modulate

`material_object:color_modulate(r: number, g: number, b: number)`

| Argument | Type   | Description                             |
| -------- | ------ | --------------------------------------- |
| **r**    | number | New red value of the material (0-255)   |
| **g**    | number | New green value of the material (0-255) |
| **b**    | number | New blue value of the material (0-255)  |

Overrides the color of the material object it's called on. Doesn't work with some materials

#### :get\_material\_var\_flag

`material_object:get_material_var_flag(material_var_flag: number)`: boolean

| Argument                | Type                       | Description                 |
| ----------------------- | -------------------------- | --------------------------- |
| **material\_var\_flag** | number (material var flag) | Material var flag as number |

Returns the boolean value of the material var flag

#### :get\_name

`material_object:get_name()`: string

Returns name of the material

#### :get\_shader\_param

`material_object:get_shader_param(shader_param: string)`: any

| Argument          | Type                  | Description       |
| ----------------- | --------------------- | ----------------- |
| **shader\_param** | string (shader param) | Shader param name |

Returns the value of the shader param or nil

#### :reload

`material_object:reload()`

Restores the original material properties of the material it's called on.

#### :set\_material\_var\_flag

`material_object:set_material_var_flag(material_var_flag: number, value: any)`

| Argument                | Type                       | Description                                |
| ----------------------- | -------------------------- | ------------------------------------------ |
| **material\_var\_flag** | number (material var flag) | Material var flag as number                |
| **value**               | any                        | New boolean value of the material var flag |

Sets the value of the material var flag of the material

#### :set\_shader\_param

`material_object:set_shader_param(shader_param: string, value: any)`

| Argument          | Type                  | Description                   |
| ----------------- | --------------------- | ----------------------------- |
| **shader\_param** | string (shader param) | Shader param name             |
| **value**         | any                   | New value of the shader param |

Sets the value of the shader param of the material

### Examples:

```lua
-- materialsystem example here
```
