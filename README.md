![Example Render generated by the renderer](img/example.png)

# 3D Gaussian Splatting Renderer implemented in WebGPU (WGPU) and Rust

This code implements a renderer for the reconstructions obtained with [3D Gaussian Splatting](https://github.com/graphdeco-inria/gaussian-splatting)

[👉 Click to run the web demo 👈](https://keksboter.github.io/web-splat/demo.html)


## Build

First, install the Rust compiler (e.g. with [rustup](https://rustup.rs/)) 

Clone the repository and run

```bash
cargo build --release --bin viewer 
```

## Run

Use the `point_cloud.ply` and `cameras.json` files generated by [3D Gaussian Splatting](https://github.com/graphdeco-inria/gaussian-splatting):

```
cargo run --release --bin viewer point_cloud.ply cameras.json
```

To load [compressed npz files](https://github.com/KeKsBoTer/c3dgs) the `npz` feature must be enabled:

```
cargo run --release --features npz --bin viewer point_cloud.npz cameras.json
```

<details>
  <summary>Usage</summary> 
    3D Gaussian Splatting Viewer

    Usage: viewer [OPTIONS] <INPUT> [SCENE]

    Arguments:
      <INPUT>  Input file
      [SCENE]  Scene json file

    Options:
          --no-vsync  
      -h, --help      Print help
      -V, --version   Print version
</details>

## About

**Splat Sorting**
: We ported the [Fuchsia RadixSort](https://fuchsia.googlesource.com/fuchsia/+/refs/heads/main/src/graphics/lib/compute/radix_sort/) to WGPU for sorting the splats on the GPU.

**Performance**: The renderer reaches >200 FPS on a `NVIDIA 3090 RTX` and ~130 FPS on a `AMD Radeon R9 380 Series` (8 years old). Measurements where taken for the bonsai scene at 1200x799 resolution.


## Citation
If you find our work useful, please cite:
```
@misc{niedermayr2023compressed,
    title={Compressed 3D Gaussian Splatting for Accelerated Novel View Synthesis}, 
    author={Simon Niedermayr and Josef Stumpfegger and Rüdiger Westermann},
    year={2023},
    eprint={2401.02436},
    archivePrefix={arXiv},
    primaryClass={cs.CV}
}
```
