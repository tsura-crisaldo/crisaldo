# Can't use pip to install Qiskit on Mac

**When I used `pip install qiskit`, it told me `Could not find a version that satisfies the requirement qiskit (from versions: ) No matching distribution found for qiskit`; when I used `pip3 install qiskit`, it told me `pip3: command not found`**

***I solved this problem by creating a virtual environment on python to install qiskit, then go back to the base environment to install qiskit.***

   I followed [the official doc of qiskit](https://github.com/Qiskit/qiskit/blob/master/docs/install.rst) to do the first two steps:   

  1. I created a minimal environment with only Python installed in it, by running `conda create -n name name_of_my_env python=3`.
  2. Activated it by running `source activate name_of_my_env`, then you will be in your virtual environment.
   
   After that you create a python virtual environment called *name_of_my_env*, only python3 installed in it, it can be found in the installation path of anaconda3 (**i.e. in my computer it is in /User/myUserID/opt/anaconda3/envs**). There are some examples that you can use to manage these environments:
   
  - Check the virtual environment: `conda env list`.
  - Install packages for virtual environment: `conda install -n name_of_my_env [package]` or `conda install [package]`(when you already in your virtual environment).
  - Delete a virtual environment: `conda remove -n name_of_my_env --all`.
  
   Then I am switching into my virtual environment called `name_of_my_env`:
   
  3. I ran `pip install qiskit`, and it did work, excellent! But an error occured when it tried to install CVXOPT package: `Failed building wheel for cvxopt`.
  4. I followed [the official doc of CVXOPT](https://cvxopt.org/install/), running `conda install -c conda-forge cvxopt` to install all the pre-built CVXOPT packages, then it installed CVXOPT package successfully. I reran `pip install qiskit` to make sure qiskit has installed in my vitual environment. But when I running python3 in my virtual environment by using terminal and jupyter notebook respectively, both of them couldn't import qiskit, they showed: `ModuleNotFoundError: No module named 'qiskit'`
  5. I went back to my base environment, I rerunning `pip install qiskit`, it worked this time, it installed qiskit without errors. Then I imported qiskit in both terminal and jupyter notebook based on python3 in base environment, it worked! Actually I don't know why it worked in this way, but it worked anyway.
  
**By the way, you have to make sure that the kernel path of your python3 in terminal and jupyter notebook are the same.
To check the kernel path:**

```
  import sys
  print(sys.executable)
```
