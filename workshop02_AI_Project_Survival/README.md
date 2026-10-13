#Project

Repository URL: https://github.com/richzhang/colorization.git

Exact commit used: 4f6009ed1495b1300231ebeb41cc4015557ddef7

Inference task: Real-Time User-Guided Image Colorization




#Repo map

Environment: requirements.txt

Entry point: demo_release.py

Model: Model loading in Python

Input:/colorization/imgs/ansel_adams.jpg

Output: /colorization/saved_eccv16.png
/colorization/saved_siggraph17.png




#Environment setup

1. First, creat a new folder. eg:workshop02_project

2. Enter the directory: 
cd workshop02_project 

3. Clone the repository:
git clone https://github.com/richzhang/colorization.git

4. Enter the colorization: 
cd colorization

5. Create a virtual environment: 
(1)open VS code, Ctrl+` open Terminl: 
code .

(2)Use an AI coding agent to determine a compatible Python version and avoid dependency conflicts, the AI told us which verison is beat to use:

Inspect this repository and its README.
Do not install anything.
Do not modify any files.
Do not create or change a virtual environment.
Based on the repository files, README, dependency files, and package version requirements:
1. Which Python version should I use for this project?
2. Which Python version is least likely to cause dependency conflicts?
Give me one recommended Python version and briefly explain why.

(3)The AI told me the best version to use is Python 3.8: 
uv venv --python 3.8

(4)Activate the environment: 
source .venv/bin/activate

(5)Check where Python is installed-it should ususally point to the .venv directory:
which python

(6)Check the installed Python version:
python --version

6. Install the dependencies(This process takes a while, please wait patiently):
python3.8 -m ensurepip --upgrade
python3.8 -m pip install torch scikit-image numpy matplotlib pillow ipython




#Inference

python3.8 demo_release.py -i imgs/ansel_adams.jpg





#One real failure

**Category:** 
ModuleNotFoundError

**Root cause:**
The virtual environment created by 'uv venv' does not include the pip tool by default, so running 'pip install requirements.txt' failed with 'No module named pip'. 

**Minimal fix:** 
(1)Manually install the pip tool:
python -m ensurepip --upgrade

(2)Manually install the project's dependencies:
python -m pip install torch scikit-image numpy matplotlib Pillow ipython





#AI agent check

**Which AI coding agent did you use?:**
GitHub Copilot Chat

**What did it change?:**
(1)It diagnosed the cause of the dependency installation failure.
(2)It provide the correct installation commands.
(3)

**How did you verify the change?:** 

The first run:

Running 'pip install requirements.txt' caused an error:
zsh: pip: command not found...

AI recommendation:
python3 -m pip install -r requirements.txt

But then an error occurs:
No module named pip

AI recommendation:
If you want to avoid touching the project environment, use the system Python instead, if it has pip:
python3 -m pip --version
If that works, then install from the repo root:
cd /home/s5815658/Desktop/class/Machine_learning/workshop02_projects/colorization
python3 -m pip install -r requirements.txt
If python3 -m pip also fails, then the machine’s Python installation is missing pip entirely, and the next step is to install pip for the system Python — but that is outside the repo itself and not a repo change.

But then an error occurred:
No module named pip

The AI assistant prepared to run a diagnostic command to check the current state of Python and pip in my environment, and then it popped up a warning asking whether I aggred to execute it.

AI:
What’s actually wrong
I verified this from the environment:
python3 --version returned Python 3.9.25
python3 -m pip --version failed with “No module named pip”
the project-local .venv exists, but its interpreter is a Python 3.8 symlink and still has no pip
So the failure is from the environment, not from the repo itself.
Next step
Do not use the broken local venv. Use a system Python 3.8 with pip, or install pip for that interpreter:
python3.8 --version
python3.8 -m ensurepip --upgrade
python3.8 -m pip install -r requirements.txt

But then an error occurred:
Collecting torch
Using cached torch-2.4.1-cp38-cp38-manylinux1_x86_64.whl (797.1 MB)
Collecting skimage
Using cached skimage-0.0.tar.gz (757 bytes)
Preparing metadata (setup.py) ... error
error: subprocess-exited-with-error 
  × python setup.py egg_info did not run successfully.
  │ exit code: 1
  ╰─> [3 lines of output]
   *** Please install the `scikit-image` package (instead of `skimage`) *** 
      [end of output] 
  note: This error originates from a subprocess, and is likely not a problem with pip.
error: metadata-generation-failed
× Encountered error while generating package metadata.
╰─> See above for output.
note: This is an issue with the package mentioned above, not pip.
hint: See above for details.
WARNING: There was an error checking the latest version of pip.

AI recommendation:
python3.8 -m pip install torch scikit-image numpy matplotlib pillow

But then an error occurred:
python demo_release.py -i imgs/ansel_adams3.jpg
Traceback (most recent call last):
  File "demo_release.py", line 5, in <module>
    from colorizers import *
  File "/home/s5815658/Desktop/class/Machine_learning/workshop02_projects/colorization/colorizers/__init__.py", line 3, in <module>
    from .eccv16 import *
  File "/home/s5815658/Desktop/class/Machine_learning/workshop02_projects/colorization/colorizers/eccv16.py", line 5, in <module>
    from IPython import embed
ModuleNotFoundError: No module named 'IPython'

AI recommendation:
python3.8 -m pip install torch scikit-image numpy matplotlib pillow ipython
python3.8 -m pip install -r requirements.txt

But then an error occurs:
Requirement already satisfied: torch in ./.venv/lib/python3.8/site-packages (from -r requirements.txt (line 1)) (2.4.1)
Collecting skimage
  Using cached skimage-0.0.tar.gz (757 bytes)
  Preparing metadata (setup.py) ... error
  error: subprocess-exited-with-error 
  × python setup.py egg_info did not run successfully.
  │ exit code: 1
  ╰─> [3 lines of output] 
      *** Please install the `scikit-image` package (instead of `skimage`) *** 
      [end of output]
  note: This error originates from a subprocess, and is likely not a problem with pip.
error: metadata-generation-failed
× Encountered error while generating package metadata.
╰─> See above for output.
note: This is an issue with the package mentioned above, not pip.
hint: See above for details.
WARNING: There was an error checking the latest version of pip.

AI recommendation:
./.venv/bin/python -m pip install scikit-image numpy matplotlib pillow ipython
./.venv/bin/python demo_release.py -i imgs/ansel_adams3.jpg

Succeful!

And I also asked the AI: Coriganize the order of the following:
Then AI gave me advice:
python3.8 --version
python3.8 -m ensurepip --upgrade
python3.8 -m pip install torch scikit-image numpy matplotlib pillow ipython
./.venv/bin/python demo_release.py -i imgs/ansel_adams3.jpg


Then I run it again in new folder.
Successful!










