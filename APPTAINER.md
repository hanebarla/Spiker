# Apptainer container for Python execution

This repository includes `apptainer-python.def` to build an Apptainer image suitable for running Spiker tutorials and scripts.

## Build

```bash
apptainer build spiker-python.sif apptainer-python.def
```

## Run Python directly

```bash
apptainer run spiker-python.sif --version
apptainer run spiker-python.sif Tutorials/2_net_builder/1_net_builder.py
```

## Work with the local repo inside the container

Bind the current repository and install `spikerplus` in editable mode:

```bash
apptainer exec --bind "$PWD":/workspace/Spiker spiker-python.sif \
  bash -lc "cd /workspace/Spiker && pip install -e ./spiker"
```

Then execute any tutorial:

```bash
apptainer exec --bind "$PWD":/workspace/Spiker spiker-python.sif \
  bash -lc "cd /workspace/Spiker && python Tutorials/7_vivado/1_vhdl_gen.py"
```
