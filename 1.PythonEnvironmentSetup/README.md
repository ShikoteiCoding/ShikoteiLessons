# Python Setup

Most python users get started with jupyter for simplicity purposes. However, this habit leads to technical limitations and lacking understanding of what coding is made for: automation and replication of repetitive tasks. 

```
In a jupyter notebook, people will have to open it, then execute the cells one by one, it is time consumming for repetitive / daily tasks. Let's learn how to setup a proper python environment.
```

## OS for coding

The three main OS known are Windows, Macos and Linux. Windows is not the most appropriate environment for coding as it lacks the Unix Kernel (engine powering the OS). Macos uses the Unix Kernel and thus is preferred for data analysis jobs where you can benefit from either linux distributions and macos softwares.

```
If you have the choice, prefer using linux or macos as your OS for python related tasks (software development or data analysis).
```

## Command Lines

Command Lines is a set of commands used to perform actions and important to increase your productivity. If your automation scripts consist of multiple actions such as copying files, executing them etc.., you will have to give precise instructions to the system, you can't give "mouse click" instructions. 

```
In a computer, any action has a command line equivalent, it is important to learn them and avoid using "mouse clicking".
```

## Projects

When creating a new project, you want to create a new folder, for multiple reasons:
1. Know the location of your code precisely.
2. Use version control (github) tools to share your code.
3. Encapsulate your environment in this folder for this specific project (some project will require specific environment).

## Python Virtual Environment

From the official documentation: https://docs.python.org/3/library/venv.html
```
A virtual environment is a Python environment such that the Python interpreter, libraries and scripts installed into it are isolated from those installed in other virtual environments, and (by default) any libraries installed in a “system” Python, i.e., one which is installed as part of your operating system.
```

## Virtual Environment Setups

### Windows Setup

In windows, you need to use PowerShell to use command lines. This is a key difference between Windows and Macos / Linux. I won't explain how to use PowerShell commands here, I will just give the instructions.

1. Install python https://virtualenv.pypa.io/en/latest/installation.html if you don't have yet.
2. Open PowerShell
3. Choose a directory and navigate there
```
cd path/toFolder/
```
4. Once in your projects folder, create a new folder for a new project
```
mkdir projectname
```
5. Create a virtual environment
```
virtualenv venv
```
6. Activate your virtual environment
```
source venv/bin/activate
```
7. Install a library
```
pip3 install LibraryName
```
8. Execute your file
```
python3 main.py
```

And now you can safely execute python code in a dedicated environment. Don't forget to activate your virtual after starting to code on a project so that you will use your virtual environment python (local) and not your global python.

Deactivate your virtual environment
```
deactivate
```

### Macos Setup

Later. I'm lazy.