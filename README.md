# BlenderSTEP

**BlenderSTEP** is a pure STEP I/O add-on for Blender: import STEP bodies, mesh them for display,
bake to a plain mesh, and export STEP again.

## The pipeline

1. **Import STEP** — File → Import → *STEP (.step / .stp)* imports every body of the file as an exact
   CAD object (SMLib solid, stored as a blob) at its real size.
2. **Display / meshing** — the CAD object shows its tessellation: the add-on's own **Fast Mesher**, or
   the kernel's tessellation when the fast mesher is off or cannot handle a face (the panel notes when
   it fell back).
3. **Bake to Mesh** — turns the selected CAD object into a regular Blender mesh (keeps the current
   mesh, drops the exact geometry), for export / 3D printing / downstream tools.
4. **Export STEP** — File → Export → *STEP, exact NURBS (*.step)* writes the selected CAD objects as
   exact STEP solids, at their real size.

## Credits

- **NVIDIA** — thanks for open sourcing the USD B-rep kernel (**SMLib**, Apache-2.0), which this add-on
  uses through **smlibpy** (MIT).
- **Claas Kuhnen** (Info@ckbrd.de) — the author of Blender STEP and of the original NURBS Tools add-on.

## License

GPL-3.0-or-later — see [LICENSE](LICENSE).

## Install

1. Blender → Edit → Preferences → Extensions → **Install from Disk…** → pick the add-on folder
   (it ships the `smlibpy` wheel for Windows, macOS and Linux; the matching wheel is chosen per OS).
2. The **Blender STEP** panel appears in the 3D viewport sidebar (N) / the *STEP* category.

Supported platforms: Windows (x64), macOS (Apple Silicon / Intel), Linux (x64 / ARM64). Requires
Blender 5.2 or newer (Python 3.13, where the smlibpy wheels are built).
