---
{"dg-publish":true,"permalink":"/01-reference/virtualenvs/","title":"Python virtual environments","tags":["python","utility"]}
---


# Python virtual environments

Once you are in the directory where you would like the environments to live, you can create an environment by running the following command:

```sh
python3 -m venv env_name
```

or alternative:

```sh
virtualenv env_name
```

Essentially, this sets up a new directory that contains installed libraries separated from the rest of the operating system. By running the virtual environment we can also define exact versions of those libraries but also the version of a python interpreter

Together, these files work to make sure that your projects are isolated from the broader context of your local machine, so that system files and project files don’t mix. This is good practice for version control and to ensure that each of your projects has access to the particular packages that it needs.

To use and activate the environment run the following command, it will read (source) the activate script

```sh
source env_name/bin/activate
```

Your terminal prompt will now be prefixed with the name of your environment, in this case it is called `env_name`.

This prefix lets us know that the environment `env_name` is currently active, meaning that when we create programs here they will use only this particular environment’s settings and packages.

> When doing a project within virtual environment you should have a file named `requirements.txt` that will list all dependencies. Tools like `pip` can create it but also install from it very easily.

To leave the environment, simply type the command deactivate and you will return to your original directory.

### Youtube guides

- [Installing Python Packages with pip and virtualenv](https://www.youtube.com/watch?v=UqkT2Ml9beg)
- [Python VENV Explained - Python Virtual Environment Tutorial](https://www.youtube.com/watch?v=SeJvz-ngCnk)
