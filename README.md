## Git Hooks Tutorial

My public talk about this project at Sberloga:<br>
[Git Hooks Is All You Need](https://youtu.be/92OMAtdVIAs)

### 1. Git Hooks 101

1) Init git repo:
```shell script
mkdir git_repo
cd git_repo

git init
```

2) Git hooks are located in `.git/hooks` folder:
```shell script
ls -lah .git/hooks
```

3) Create executable (`chmod +x`) pre-commit hooks (path: `.git/hooks/pre-commit`):
 - bash [hook](https://github.com/dayyass/git_hooks_is_all_you_need/blob/main/hooks/pre-commit.good) with exit code 0
 - bash [hook](https://github.com/dayyass/git_hooks_is_all_you_need/blob/main/hooks/pre-commit.bad) with exit code 1
 - python [hook](https://github.com/dayyass/git_hooks_is_all_you_need/blob/main/hooks/pre-commit.good.py) with exit code 0

Make commit after each step. You'll see different results.

### 2. Python pre-commit library

1) Create and activate virtual environment:
```shell script
python3 -m venv venv
source venv/bin/activate
```

2) Install and activate pre-commit library:
```shell script
pip install pre-commit
pre-commit install
```

3) Create pre-commit configuration file [.pre-commit-config.yaml](https://github.com/dayyass/git_hooks_is_all_you_need/blob/main/.pre-commit-config.yaml).<br>
Alternatively, you can use [local configuration](https://github.com/dayyass/git_hooks_is_all_you_need/blob/main/.pre-commit-config_local.yaml).


4) Create [main.py](https://github.com/dayyass/git_hooks_is_all_you_need/blob/main/main_before_hooks.py) file.<br>
Make commit. Pre-commit library will reformat file according to PEP8.<br>
Remove unused `import sys` string to get ready-to-commit [main.py](https://github.com/dayyass/git_hooks_is_all_you_need/blob/main/main_after_hooks.py) file.

### 3. Remote repo

1) Init empty "remote" repo:
```shell script
git init --bare ../remote_repo.git
```

2) Link local and "remote" repo:
```shell script
git remote add origin ../remote_repo.git
```

3) Create executable (`chmod +x`) pre-receive [hook](https://github.com/dayyass/git_hooks_is_all_you_need/blob/main/hooks/pre-receive.good) on "remote" (path: `../remote_repo.git/hooks/pre-receive`).<br>
Make push and see the result.

### Reference
Useful links:
- git hooks intro: [link](https://githooks.com)
- git hooks usage: [link](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
- pre-commit page: [link](https://pre-commit.com)
