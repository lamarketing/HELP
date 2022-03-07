## FLAKE8
### Установка
`$ pip install --upgrade flake8`
## Настройки
`$ nano setup.cfg`
```
[flake8]
exclude = .git, venv, tests, migrations, config
max-line-length = 119
```
`$ flake8 <dir_or_file>`
### Проверка до commit
```
$ pip install pre-commit
$ pre-commit --version
pre-commit 2.17.0
$ nano .pre-commit-config.yaml
```
```
repos:
-   repo: local
    hooks:
    -   id: flake8
        name: flake8
        description: max-line=119
        entry: flake8
        args: ["--config=setup.cfg"]
        language: python
        types: [python]
```
`$ pre-commit install`