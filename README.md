# Setting up and running notebooks

*These are only suggested options.
Of course, you are welcome to try and set everything up your own way.*

## Table of contents
* [On JetBrains DataLore](#on-jetbrains-datalore)
  * [For CUDA machines with CUDA examples](#for-cuda-machines-with-cuda-examples)
  * [Without CUDA](#without-cuda)
  * [Per-notebook setup](#per-notebook-setup)
    * [Multidimensional Arrays](#01---multidimensional-arrays)
* [Locally on your computer](#locally-on-your-computer)

## On JetBrains DataLore

### For CUDA machines with CUDA examples

On [DataLore](https://datalore.jetbrains.com/), the notebooks were tested using [conda](https://docs.conda.io/en/latest/), because it has proven more handy for setting up requirements for **numba**'s `@cuda.jit` kernels support.

With the notebook open on **DataLore**, do the following:

1. **Switch to conda for package management**: via the left panel, enter the **Environment** menu.
There, under **Packages**, you will probably have **Pip - Default**.
Click **Change**, and change your package manager to **Conda**.
1. **Install the required packages**:
   * **via terminal**: Go to **Tools -> Terminal** and install the required packages by typing in commands:
     ```shell
     conda install pytorch numba -y
     conda install -c nvidia cuda-nvcc -y
     ```
     You will need to perform this setup every time the mahine is restarted.
   * **via `init.sh`**: Go to **Environment** menu and click **init.sh**. Add the commands from the above to the file.
   Now the machine will install the dependencies automatically every time it starts up (this increases startup times greatly though).

### Without CUDA

If you don't have access to a CUDA machine, the default **Pip** configuration should do just fine for you.
The only thing you need to do is install **numba**:
1. Navigate to the **Environment** menu (via the left panel)
2. On **Explore** tab search for **numba**
3. Install **numba**
4. DataLore should remember your choice and will provide **numba** automatically next time you launch the notebook

### Per-notebook setup

#### 01 &mdash;  Multidimensional Arrays

**01-multidimensional-arrays.ipynb** includes a demonstration C++ Python module compilation via Torch extensions.
Code for this example is in the file **cpp_intro.cc**.
To upload it to **DataLore** go to **Attached data** via the left menu, then under **Notebook files** click **Upload files...**
You should be good to go.

## Locally on your computer

We encourage you use a Linux distribution to run the notebooks.
The notebooks weren't tested on Windows or Mac and CUDA does not even work on newer Macs at all.

If you're on Windows and don't want to set up a graphical VM or dual boot, take a look at [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) ([it even supports CUDA](https://docs.nvidia.com/cuda/wsl-user-guide/index.html)).
On Mac, you can run Linux via [Lima](https://github.com/lima-vm/lima).

We provide a [YML](numerics-env.yml) file to set up a **Conda** environment with all needed packages.

0. _It is expected that you already have **Conda** and **g++** installed_
1. Clone or download this repository
1. Navigate to the repository folder and run
   ```
   conda env create -f numerics-env.yml
   ```
1. Conda will create a virtual environment with all dependencies (including **Jupyter**) installed
1. Switch to a newly created environment with
   ```
   conda activate numerics-2022
   ```
1. Run **Jupyter** with
   ```
   jupyter notebook
   ```
