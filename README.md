<img width="1194" height="973" alt="Screenshot 2026-11-01 at 1 09 41 PM" src="https://github.com/user-attachments/assets/97f19d47-47a3-4f5d-9c75-11c5dda525da" />

# Blender STEP

**Blender STEP** is a pure STEP importer add-on for Blender: import STEP bodies, mesh them for
display, and bake to a plain mesh.

## The pipeline

1. **Import STEP** — File → Import → *STEP (.step / .stp)* imports every body of the file as an exact
   CAD object (SMLib solid, stored as a blob) at its real size.
2. **Display / meshing** — the CAD object shows its tessellation. The **Mesher** setting picks who makes it: **Auto**
   (default) uses the add-on's own fast mesher on bodies made only of planes, cylinders, cones and spheres
   (many holes, flat plates) and the kernel's tessellation on everything else; **Fast** and **Kernel** force one
   or the other. The kernel also steps in for a face the fast mesher cannot handle (the panel notes when
   it did). **Display Quality** (Draft / Normal / Fine) is a per-part choice, applied to all selected
   CAD objects.
3. **Diagnostic shading** — on a selected CAD object: **Off**, **Zebra** (reflected stripes, running
   smoothly across G2 joins, bending at G1 and breaking at G0), **Highlight Lines** (long straight studio
   lights reflected as thin lines — what designers judge a surface by) or **Environment Image** (chrome
   reflection of a loaded HDRI / panorama). **High Quality** colors the mesh by Gaussian curvature, where
   the tessellation is fine or coarse. A choice made on a part goes to all selected CAD objects.
4. **Bake to Mesh** — turns the selected CAD object into a regular Blender mesh (keeps the current
   mesh, drops the exact geometry), for 3D printing / downstream tools.

## The panel

The **Blender STEP** panel in the 3D viewport sidebar (N) / the *STEP* category reads, top to bottom:

1. **Import STEP** — import every body of a STEP file as an exact CAD object.
2. **Mesher** — Auto / Fast / Kernel (also offered in the import dialog; changing it re-meshes the parts).
3. **Display Quality** — Draft / Normal / Fine, per-part choice that is applied to all selected CAD objects.
4. **Diagnostic** — Off / Zebra / Highlight Lines / Environment Image / High Quality, with its settings,
   per-part choice that is applied to all selected CAD objects (a change made on one part goes to the
   other selected parts too).

**Bake to Mesh** sits at the bottom — the flow is: import, set meshing, verify with the diagnostic
shader, then bake.

## Credits

- **NVIDIA** — thanks for open sourcing the USD B-rep kernel (**SMLib**, Apache-2.0), which this add-on
  uses through **smlibpy** (MIT).
- **Claas Kuhnen** (Info@ckbrd.de) — the author of Blender STEP.

## License

GPL-3.0-or-later — see [LICENSE](LICENSE).

## Install

1. Blender → Edit → Preferences → Extensions → **Install from Disk…** → pick the add-on folder
   (it ships the `smlibpy` wheel for Windows, macOS and Linux; the matching wheel is chosen per OS).
2. The **Blender STEP** panel appears in the 3D viewport sidebar (N) / the *STEP* category.

Supported platforms: Windows (x64), macOS (Apple Silicon / Intel), Linux (x64 / ARM64). Requires
Blender 5.2 or newer (Python 3.13, where the smlibpy wheels are built).
