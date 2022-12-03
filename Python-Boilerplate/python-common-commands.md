

## Add Common Poetry Dev Dependencies
from anywhere in project:  
```zsh
poetry add --group=dev black isort pdoc pylint pyright pytest pytest-cov
```

- formatting: `isort` & `black`
- linting: `pylint`
- lsp & typechecking: `pyright`
- testing: `pytest` + `pytest-cov`
- auto-documentation: `pdoc`


## Run Pre-Commit Hook Manually
from root of project:  
```zsh
.git/hooks/pre-commit
```
from anywhere in project:
```zsh
git hook run pre-commit
```
(using local alias: `ghk pre-commit`)


