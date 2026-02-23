# Predictive ML Project, Module 7

## Set Up Project

1. Get Repository: Duplicate datafun-04-notebooks repo

2. Configure Repository Settings:
   - Select your repository **Settings** (the gear icon way on the right).
   -  Go to **Pages** tab / Enable GitHub Pages / Build and deployment / set **Source** to **GitHub Actions**
   -  Go to **Advanced Security** tab / Dependabot / **Dependabot security updates** / **Enable**
   -  Go to **Advanced Security** tab / Dependabot / **Grouped security updates** / **Enable**

3. Clone to local: Open a **machine terminal** in your **`Repos`** folder and clone your new repo.

  ```shell
  git clone https://github.com/kander643/datafun-07-ml
  ```

4. Open project in VS Code: Change directory into the repo and open the project in VS Code by running `code .` ("code dot"):

  ```shell
  cd datafun-07-ml
  code .
  ```

5. Set up a project Python environment (managed by `uv`) and align VS Code with it.

   - Use VS Code menu option `Terminal` / `New Terminal` to open a **VS Code terminal** in the root project folder.
   - Run the following commands, one at a time, hitting ENTER after each:

    ```shell
    uv self update
    uv python pin 3.14
    uv sync --extra dev --extra docs --upgrade
    ```

If asked: "We noticed a new environment has been created. Do you want to select it for the workspace folder?" Click **"Yes"**.

```shell
uvx pre-commit install
git add -A
uvx pre-commit run --all-files
git add -A
uvx pre-commit run --all-files
```

6. Install extrenal packages

```shell
uv add jupyterlab numpy pandas pyarrow matplotlib seaborn scipy
```

## Daily Workflow

Commands are provided below to:

1. Git pull
2. Run and check the Python files
3. Build and serve docs
4. Save progress with Git add-commit-push
5. Update project files

```shell
git pull
```

Run Python checks and tests (as available):

```shell
uv run ruff format .
uv run ruff check . --fix
uv run pytest --cov=src --cov-report=term-missing
```

Build and serve docs (hit **CTRL+c** in the VS Code terminal to quit serving):

```shell
uv run mkdocs build --strict
uv run mkdocs serve
```

While editing project code and docs, repeat the commands above to run files, check them, and rebuild docs as needed.

Save progress frequently (some tools may make changes; you may need to **re-run git `add` and `commit`** to ensure everything gets committed before pushing):

```shell
git add -A
git commit -m "update"
git push -u origin main
```
