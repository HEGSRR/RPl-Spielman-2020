# Environment

Store detailed information about the hardware and software environment requirements for procedures and code here. You may also document a recipe or container of the computational environment here.

This directory is specifically for hardware and software environments.
Contextual factors or confounds of human subjects research or field research should be communicated in protocol documents and stored in the `protocols` directory.

For users of R, our template code, at a minimum, saves environment information using the `sessionInfo()` function.

## Environment Setup

We have used `pipenv` to manage the computational python environment for this study. To reproduce, install Python and Jupyter and run the code found in [environment_setup.ipynb](environment_setup.ipynb)
Alternatively, we have saved a version of the `requirements.txt` package requirements in the root folder so that the study can be run in a Docker container on Binder: https://mybinder.org/v2/gh/HEGSRR/RPl-Spielman-2020/HEAD 
