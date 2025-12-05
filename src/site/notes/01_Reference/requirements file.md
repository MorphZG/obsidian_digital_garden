---
{"dg-publish":true,"permalink":"/01_Reference/requirements file/","title":"Requirements file","tags":["python","programming"],"created":"2025-12-05T03:27:51.078+01:00"}
---


# Requirements file

```sh
# Output the list of installed packages
pip list
# Output the list of dependancy versions
pip freeze
# Export it to a text file
pip freeze > requirements.txt
# Install by reading from requirements.txt
pip install -r requirements.txt
```

Install specific version of package (you can use * global sign)

```sh
python3 -m pip install "package==1.4"
pip install "package==1.4"
pip install "package==1*" (will install any version starting with 1)
```

Install greater than or equal to version 1 and less than version 2:

```sh
python3 -m pip install "SomeProject>=1,<2"
```

All INFO at official page:
https://packaging.python.org/tutorials/installing-packages/
