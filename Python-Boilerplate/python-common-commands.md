----------------------------------------------

# Initialization

## Add Common Poetry Dev Dependencies
from anywhere in project:  
```zsh
poetry add --group=dev black coverage isort pdoc pylint pyright pytest
```

- formatting: `isort` & `black`
- linting: `pylint`
- lsp & typechecking: `pyright`
- testing: `pytest` + `pytest-cov`
- auto-documentation: `pdoc`


---------------------------------------------

# General

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

____________________________________________


# Workarounds
Poetry, if it downloads a bad hash does not try to automatically re-download said hash nor do the built in commands succeed in clearing the cache.
The following pipeline will take all the reported downloads for which the hash wasn't found, find them in the folder that Poetry keeps them, and then, with confirmation request, delete those hashes.
Just pipe an install command into it.  e.g. `poetry install foo | poethashnotfoundworkaround` and continue to re-run the line until it stops prompting you to delete the bad hashes.

**Note**: this may require the `POETRY_CACHE_DIR` variable be manually set, e.g. in your `.zshenv`; it also assumes the presence of [ripgrep](https://github.com/BurntSushi/ripgrep), [choose](https://github.com/theryangeary/choose/tree/d434bd289d043997058d9a08d5e02642060fcde9/), and [fd](https://github.com/sharkdp/fd) (grep, awk, and find can be substituted with appropriate syntactic changes)

```zsh
alias poethashnotfoundworkaround='rg "not found in known hashes" | choose -f "archive" 1 | choose 0 | xargs -I_ fd _ $POETRY_CACHE_DIR | xargs -o rm -i'
```

