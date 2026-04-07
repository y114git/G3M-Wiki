# Animations

G3M uses subtle animations throughout the interface for a polished feel. All animations can be disabled for performance or accessibility.

---

## Types of Animations

### Color Transitions

When theme colors change (hover, select, active state), UI elements smoothly transition between colors over a short duration. This applies to:

- Buttons (hover/press/release).
- Tab indicators (switching active tab).
- Mod card highlights (selecting/deselecting).
- Status bar color changes.

### Progress Bar Fill

The progress bar fills smoothly from its current value to the new value, rather than jumping instantly.

### Panel Transitions

When the Mod Details overlay opens or closes in the Mods Browser, it slides in from the right with a smooth animation.

### Scroll Animations

Smooth scrolling when navigating between pages or scrolling to specific elements.

---

## Disabling Animations

1. Go to Settings → Appearance.
2. Check **Disable animations**.
3. All animations are instantly turned off.

When disabled:

- Color transitions are immediate (no interpolation).
- Progress bar jumps to the target value.
- Panel transitions are instant (appear/disappear without sliding).
- Scroll behavior becomes immediate.

---

## Performance

Animations are lightweight and should not cause performance issues on modern hardware. However, if you experience:

- Laggy color transitions.
- Stuttering scroll.
- High CPU usage during UI interactions.

Disabling animations can help, especially on older systems or virtual machines.

---

## Debouncing

Theme color changes are debounced — if you change multiple colors quickly (e.g., importing a theme), the stylesheet is only regenerated once after a 150ms pause. This prevents a cascade of expensive stylesheet recalculations during rapid changes.

---

## Persistence

The `disable_animations` setting is stored in `settings.json` and persists across sessions.
