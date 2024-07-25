# XLA Built-in Presets / Transforms v1.0.0


## Conventions

This document uses markdown. All the information about presets / transforms
is structured is a very specific ways, to allow easy parsing of this document
in the future. This can allow for creating common documentation in a different
format, for use by UI or other apps/projects/websites.

Also note how a lot of variables exposed are similar for presets described.
This is made so that transforms can be applied to as much presets as possible.
Transforms also have common elements, for those to have better support and
"special treatmeant" in UI.

Some common variables (constants) include: `MULTIPLIER`, `WIDTH`, `HEIGHT`,
`SIZE`, `COLOR`, `COLORS`, `DEPTH`, `RADIUS`, `QUALITY`.


## Built-in Presets (mesh type)

Here, all the built-in mesh presets are listed and documented. They can
be reffered to in XLA as `mesh.<category>.<name>`, where `category` is used
to divide this document section into subsections. Note that for each preset,
described here, full name will be still listed in the header!

### Category: trivial

Trivial mesh presets. Simple shapes, intended for general usage.

#### 1. mesh.trivial.rectangle

Mesh to be used for 2D square/rectangular shapes. It is a small `1fx` by `1fx`
square initially, with configurable size and color (one solid color, or
a list of colors for all 4 points, starting from bottom-left point and going
clockwise). Note that `width` and `height` variables take precedance over
`size` variable.

**Full name:** mesh.trivial.rectangle

**Human-readable name:** Simple Rectangle

**Exposed variables:** `WIDTH`, `HEIGHT`, `SIZE`, `COLOR`

#### 2. mesh.trivial.ellipse

Mesh to be used for 2D ellipse/circle shape. It is a small `1fx` by `1fx`
circle initially, with configurable radiuses (first one is horizontal,
second one - vertical axis) and color (one solid color). You can also adjust
the quality (which is the number of segments used to create an ellipse/circle)

**Full name:** mesh.trivial.ellipse

**Human-readable name:** Simple Ellipse

**Exposed variables:** `RADIUS1`, `RADIUS2`, `COLOR`, `QUALITY`

#### 3. mesh.trivial.polygon

Mesh to be used for 2D regular polygons. It is a small triangle (that
of 1fx radius) initially, with configurable radius, color (one solid color,
or a list of colors, for each vertex), and vertex number.

**Full name:** mesh.trivial.polygon

**Human-readable name:** Regular Polygon

**Exposed variables:** `RADIUS`, `COLOR`, `MULTIPLIER`

### Category: enemy

Enemy mesh presets. Resemble official and some custom enemies, intended to be
used for recreating given enemies, or creating their variations.

#### 4. mesh.enemy.asteroid

Mesh, that closely resembles official asteroid enemy. Spec for it is W.I.P.

**Full name:** mesh.enemy.asteroid

**Human-readable name:** Asteroid Enemy

**Exposed variables:** `COLOR`, `SPEED`

#### 5. mesh.enemy.baf

Mesh, that closely resembles official baf enemy. There are no different
variations, such as red or blue baf, since that can be configured through
color variable (a single solid color, or two colors for start/end gradient).
You can change the size, note that separate parameters, like lenght and radius
take precedance over that.

**Full name:** mesh.enemy.baf

**Human-readable name:** Baf Enemy

**Exposed variables:** `COLOR`, `SPEED`, `SIZE`, `LENGHT`, `RADIUS`

#### 6. mesh.enemy.inertiac

Mesh, that closely resembles official inertiac enemy.

**Full name:** mesh.enemy.inertiac

**Human-readable name:** Inertiac Enemy

**Exposed variables:** `COLOR`, `SPEED`

#### 7. mesh.enemy.mothership

Mesh, that closely resembles official mothership enemy.

**Full name:** mesh.enemy.mothership

**Human-readable name:** Mothership Enemy

**Exposed variables:** `COLOR`, `SPEED`

#### 8. mesh.enemy.mothership_bullet

Mesh, that closely resembles official mothership bullet.

**Full name:** mesh.enemy.mothership_bullet

**Human-readable name:** Mothership Bullet

**Exposed variables:** `COLOR`, `SPEED`

#### 9. mesh.enemy.rolling_cube

Mesh, that closely resembles official rolling cube enemy.

**Full name:** mesh.enemy.rolling_cube

**Human-readable name:** Rolling Cube Enemy

**Exposed variables:** `COLOR`, `SPEED`

#### 10. mesh.enemy.rolling_sphere

Mesh, that closely resembles official rolling sphere enemy.

**Full name:** mesh.enemy.rolling_sphere

**Human-readable name:** Rolling Sphere Enemy

**Exposed variables:** `COLOR`, `SPEED`

#### 11. mesh.enemy.ufo

Mesh, that closely resembles official ufo enemy.

**Full name:** mesh.enemy.ufo

**Human-readable name:** Ufo Enemy

**Exposed variables:** `COLOR`, `SPEED`

#### 12. mesh.enemy.wary

Mesh, that closely resembles official wary enemy.

**Full name:** mesh.enemy.wary

**Human-readable name:** Wary Enemy

**Exposed variables:** `COLOR`, `SPEED`

#### 13. mesh.enemy.crowder

Mesh, that closely resembles official crowder enemy.

**Full name:** mesh.enemy.crowder

**Human-readable name:** Crowder Enemy

**Exposed variables:** `COLOR`, `SPEED`

#### 14. mesh.enemy.wary_missile

Mesh, that closely resembles official wary missile.

**Full name:** mesh.enemy.wary_missile

**Human-readable name:** Wary Missile

**Exposed variables:** `COLOR`, `SPEED`

#### 15. mesh.enemy.ufo_bullet

Mesh, that closely resembles official ufo bullet.

**Full name:** mesh.enemy.ufo_bullet

**Human-readable name:** Ufo Bullet

**Exposed variables:** `COLOR`, `SPEED`


<!-- mesh.enemy.ship -->
<!-- mesh.enemy.bombmbles -->
<!-- mesh.enemy.player_bullet -->
<!-- mesh.enemy.bomb_explosion -->
<!-- mesh.enemy.player_explosion -->
<!-- mesh.enemy.bonus -->
<!-- mesh.enemy.floating_message -->
<!-- mesh.enemy.pointonium -->
<!-- mesh.enemy.bonus_implosion -->
