# Doki Doki Mod Manager SDK

The Doki Doki Mod Manager SDK is a small module that allows your mod to interface with DDMM.

## Current features

* Achievements

## Quick Start

1. Download the latest copy of `ddmm_sdk.rpy` and place it anywhere in your `game` folder.
2. Create an init block somewhere in your mod scripts (usually `overrides.rpy`) and register your achievements:

```
init 10:
  call ddmm_register_achievement("ACHIEVEMENT_1", "Achievement Name", "Achievement Description")
  call ddmm_register_achievement("ACHIEVEMENT_2", "Achievement Name 2", "Achievement Description 2")
  ...
```

3. When you want your player to earn an achievement, call the appropriate label:

```
call ddmm_earn_achievement("ACHIEVEMENT_1")
```

4. That's it!

## API

### ddmm_register_achievement(id, name, description)

Label - registers an achievement.

* id (string) = the unique identifier for your achievement, used in code (e.g. `MY_ACHIEVEMENT_1`)
* name (string) = the user-facing name of the achievement (e.g. `My Achievement`)
* description (string) = the user-facing description of the achievement, usually a description of how to earn it (e.g. `Complete Monika's route`)

### ddmm_earn_achievement(id)

Label - grants the user an achievement. Note that if the achievement has not been registered, an error will occur.

* id (string) = the ID passed to `ddmm_register_achievement`

### ddmm_online

Variable - `True` if the mod was launched through DDMM, `False` otherwise.

```
if ddmm_online:
  m "You're using DDMM! Well done!"
else
  m "You should use DDMM, you know."
```
