# Project Structure

```text
kimodo/
├── kimodo/                       # Main Python package
│   ├── model/                    # Model architecture and loading
│   │   ├── kimodo_model.py       # Kimodo diffusion model wrapper
│   │   ├── twostage_denoiser.py  # Two-stage denoising architecture
│   │   ├── backbone.py           # Transformer encoder backbone
│   │   ├── diffusion.py          # Diffusion process
│   │   ├── cfg.py                # Classifier-free guidance
│   │   ├── load_model.py         # Model loading and registry lookup
│   │   ├── loading.py            # Checkpoint loading utilities
│   │   ├── registry.py           # Model registry (skeleton, checkpoint URLs)
│   │   ├── text_encoder_api.py   # Text encoder API client
│   │   ├── tmr.py                # TMR compatibility
│   │   └── llm2vec/              # LLM-based text encoder
│   ├── motion_rep/               # Motion representation
│   │   ├── reps/                 # Skeleton-specific motion reps
│   │   │   ├── kimodo_motionrep.py
│   │   │   └── tmr_motionrep.py
│   │   ├── conditioning.py      # Conditioning (text, constraints)
│   │   ├── feature_utils.py      # Feature extraction
│   │   ├── feet.py               # Foot contact / smoothing
│   │   ├── smooth_root.py        # Smooth root representation
│   │   └── stats.py             # Normalization statistics
│   ├── skeleton/                 # Skeleton definitions and kinematics
│   │   ├── definitions.py        # Skeleton topology (joints, chains)
│   │   ├── registry.py           # Skeleton registry
│   │   ├── base.py               # Base skeleton types
│   │   ├── kinematics.py         # Forward kinematics
│   │   ├── transforms.py         # Rotation/transform utilities
│   │   └── bvh.py                # BVH I/O
│   ├── viz/                      # Visualization
│   │   ├── scene.py              # 3D scene setup
│   │   ├── playback.py           # Timeline / motion playback
│   │   ├── viser_utils.py        # Viser 3D helpers
│   │   ├── gui.py                # Demo GUI components
│   │   ├── constraint_ui.py      # Constraint editing UI
│   │   ├── coords.py             # Coordinate frames
│   │   ├── soma_skin.py          # SOMA character skinning
│   │   ├── soma_layer_skin.py    # SOMA layer-based skinning
│   │   ├── smplx_skin.py         # SMPL-X skinning
│   │   └── g1_rig.py             # G1 robot rig
│   ├── demo/                     # Interactive web demo
│   │   ├── app.py                # Demo entry (Gradio / Viser)
│   │   ├── config.py             # Demo configuration
│   │   ├── state.py              # Application state
│   │   ├── ui.py                 # UI layout and callbacks
│   │   ├── generation.py         # Generation pipeline for demo
│   │   └── embedding_cache.py   # Cached text embeddings
│   ├── exports/                  # Motion export formats
│   │   ├── bvh.py                # BVH export
│   │   ├── mujoco.py             # MuJoCo export
│   │   └── smplx.py              # SMPL-X export
│   ├── metrics/                  # Evaluation metrics
│   │   ├── base.py               # Metric base classes
│   │   ├── foot_skate.py         # Foot skate metric
│   │   ├── constraints.py       # Constraint satisfaction
│   │   └── tmr.py                # TMR-based metrics
│   ├── scripts/                  # CLI and helper scripts
│   │   ├── generate.py           # CLI for motion synthesis (kimodo_gen)
│   │   ├── run_text_encoder_server.py  # Text encoder server (kimodo_textencoder)
│   │   ├── generate_eval.py      # Evaluation generation
│   │   ├── gradio_theme.py       # Gradio theme for demo
│   │   └── ...                   # G1/SOMA asset scripts
│   ├── assets/                   # Package data (shipped with package)
│   │   ├── demo/                 # Demo examples and config
│   │   └── skeletons/            # Skeleton assets
│   ├── constraints.py            # Constraint definitions and handling
│   ├── geometry.py               # Geometric utilities
│   ├── postprocess.py            # Post-processing (e.g. MotionCorrection)
│   ├── meta.py                   # Motion metadata
│   ├── sanitize.py               # Input sanitization
│   ├── assets.py                 # Asset path resolution
│   └── tools.py                  # General utilities
├── MotionCorrection/             # Optional C++/Python post-processing
│   ├── python/motion_correction/ # Python bindings
│   └── src/cpp/                  # C++ implementation
├── docs/                         # Documentation (Sphinx)
│   └── source/                   # RST/MD sources
├── assets/                       # Repo-level assets (banner, screenshots)
├── pyproject.toml                # Package config and entry points
├── setup.py                      # Setuptools entry (if needed)
└── README.md
```

Entry points (from `pyproject.toml`):

- **`kimodo_gen`** — command-line motion synthesis (`kimodo.scripts.generate:main`)
- **`kimodo_demo`** — interactive web demo (`kimodo.demo:main`)
- **`kimodo_textencoder`** — text encoder server (`kimodo.scripts.run_text_encoder_server:main`)
