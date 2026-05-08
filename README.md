# Rotation Calculator

A self-contained, single-file HTML rotation calculator for robotics work. Compose multiple rotations and convert between Euler angles, quaternions, axis-angle, and rotation matrices — all formats shown side-by-side, with a live 3D axis preview per rotation.

Inspired by [articulatedrobotics.xyz/tools/rotation-calculator](https://articulatedrobotics.xyz/tools/rotation-calculator).

## Usage

Open `rotation-calculator.html` in any modern browser. No build step, no server, no dependencies.

```bash
open rotation-calculator.html
```

## Features

- **Compose rotations**: add any number of rotations; the rightmost **Result** card shows their left-to-right matrix product. Use `Ignore` to skip a rotation, or `Invert` semantics via inputting the inverse.
- **Four input formats** per card: Euler angles, Quaternion, Axis-Angle, and Rotation Matrix.
- **All four output formats** shown simultaneously, with independent unit (deg/rad) and convention selectors.
- **Euler conventions**: all 12 intrinsic sequences (XYZ, ZYX, ZYZ, …) via Ken Shoemake's algorithm.
- **Quaternion conventions**: switch freely between `w, x, y, z` and `x, y, z, w` — both for input and output, independently per card.
- **Paste-to-fill**: paste any text containing numbers (`[0.1, 0.2, 0.3]`, `1 2 3 4`, `(0.5; 0.5; 0.5)`, etc.) and the calculator extracts the first N floats in order.
- **Validation**: warns on non-unit quaternions and matrices that aren't proper rotations (det ≠ 1 or non-orthogonal).
- **Copy as Python**: every output block has a `copy` button that produces a Python list / nested list ready to paste into code.
- **Live 3D preview**: per-card Canvas 2D isometric axis triad shows the rotation visually.
- **Configurable precision**: global decimal-places control in the header.
- **Light / dark theme** toggle.

## Math notes

- All Euler angles are **intrinsic** (rotations apply about the moving body frame).
- For ROS roll-pitch-yaw (extrinsic XYZ): select **ZYX** intrinsic, which is mathematically equivalent.
- Matrix-to-Euler uses the Shoemake algorithm (Graphics Gems IV) with gimbal-lock detection.
- Matrix-to-quaternion uses the Shepperd method.
- Axis-angle conversion goes via quaternion for numerical stability.

## License

MIT
