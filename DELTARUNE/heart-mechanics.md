# Heart / SOUL Mechanics

The player's SOUL (heart) in battle is controlled by `obj_heart`. Its color mode determines movement behavior and visual appearance.

---

## `scr_heartcolor`

```gml
function scr_heartcolor(arg0)
{
    __heartcolor = arg0;
    if (__heartcolor == "red" || __heartcolor == 0)
    {
        with (obj_heart)
        {
            color = 0;
            sprite_index = spr_dodgeheart;
        }
    }
    if (__heartcolor == "yellow" || __heartcolor == 1)
    {
        with (obj_heart)
        {
            color = 1;
            sprite_index = spr_yellowheart;
        }
        obj_grazebox.sprite_index = spr_grazeappear_yellow;
    }
}
```

### Color Modes

| Input | `color` | Sprite | Behavior |
|---|---:|---|---|
| `"red"` or `0` | 0 | `spr_dodgeheart` | Standard dodge movement |
| `"yellow"` or `1` | 1 | `spr_yellowheart` | Shooter mode (can fire projectiles) |

Yellow mode also changes the graze box sprite to `spr_grazeappear_yellow`.

---

## Heart Movement (`scr_moveheart`)

`scr_moveheart` processes input each frame during bullet phases:

- Reads directional input
- Applies movement speed (affected by holding cancel button for precision mode)
- Clamps position to the bullet box bounds (`obj_yourbox`)
- Handles fractions for sub-pixel accuracy

The bullet box is dynamically resized by battle scripts using `scr_get_box` / `scr_charbox`.

---

## Invulnerability

After taking damage, the heart enters invulnerability:

- `global.inv = global.invc * 40` — standard 40-frame window
- Heart flashes during invulnerability
- `global.inv` is decremented each frame
- Damage only processes when `global.inv < 0`

Equipment can modify `global.invc` to change the window duration.

---

## Graze System

The graze box (`obj_grazebox`) surrounds the heart and detects proximity to bullets:

- When a bullet enters the graze zone without hitting the heart core, TP is generated
- Graze size is affected by `global.grazesize` and equipment modifiers
- Visual sparks appear on successful graze

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Add a new heart mode | Extend `scr_heartcolor` with a new color branch |
| Change heart speed | Edit `scr_moveheart` |
| Change precision mode | Edit the cancel-button speed reduction in `scr_moveheart` |
| Change invulnerability | Modify `global.invc` in `scr_gamestart` |
| Change graze detection | Edit `obj_grazebox` and `global.grazesize` |