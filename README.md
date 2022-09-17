# Setting up and running notebooks

*These are only suggested options.
Of course, you are welcome to try and set everything up your own way.*

## Table of contents
* [On JetBrains DataLore](#on-jetbrains-datalore)
  * [For CUDA machines with CUDA examples](#for-cuda-machines-with-cuda-examples)
  * [Without CUDA](#without-cuda)
  * [Per-notebook setup](#per-notebook-setup)
    * [Seminar 1](#seminar-1)
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

#### Seminar 1

**seminar1.ipynb** includes a demonstration C++ Python module compilation via Torch extensions.
Code for this example is in the file **cpp_intro.cc**.
To upload it to **DataLore** go to **Attached data** via the left menu, then under **Notebook files** click **Upload files...**
You should be good to go.

## Locally on your computer

### TODO: This section

We encourage you use a Linux distribution to run the notebooks.
The notebooks weren't tested on Windows or Mac and CUDA does not even work on newer Macs at all.

If you're on Windows and don't want to set up a graphical VM or dual boot, take a look at [WSL](https://learn.microsoft.com/en-us/windows/wsl/install).

We provide an **env.yml** (TODO: we don't yet) file to set up a **Conda** environment with all needed packages.
