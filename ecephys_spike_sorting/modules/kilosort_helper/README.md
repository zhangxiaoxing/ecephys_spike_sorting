Kilosort Helper
==============
Python wrapper for Matlab-based spike sorting with Kilosort/Kilosort2.

This module auto-generates the channel map, configuration file, and master file for Kilosort, and runs everything via the Matlab engine.

Dependencies
------------
[Kilosort](https://github.com/MouseLand/Kilosort2) or [Kilosort2](https://github.com/cortex-lab/kilosort) - requires Matlab >=R2016b with Signal Processing and Parallel Computing Toolboxes, Visual Studio Community 2013, and a CUDA-compatible GPU
[Matlab Engine API for Python](https://www.mathworks.com/help/matlab/matlab_external/install-the-matlab-engine-for-python.html) - this may restrict the Python version you're able to use

Running
-------
```
python -m ecephys_spike_sorting.modules.kilosort_helper --input_json <path to input json> --output_json <path to output json>
```
See the schema file for detailed information about input json contents.


Input data
----------
- **ap band .dat or .bin file** : in16 binary files written by [Open Ephys](https://github.com/open-ephys/plugin-GUI), [SpikeGLX](https://github.com/billkarsh/spikeglx), or the `extract_from_npx` module.

Output data
-----------
- **Kilosort output files** : .npy files containing spike times, cluster labels, templates, etc.