### My First GitHub Actions 

This project demonstrates a simple CI pipeline using GitHub Actions.
Whenever code is pushed to the repository, GitHub Actions automatically:

1. Starts a runner

2. Sets up multiple Python versions

3. Installs dependencies

4. Runs unit tests

This helps ensure the code works properly in different Python environments.

### Workflow File

The workflow is stored inside:

`.github/workflows/main.yml`

---

### How This GitHub Actions Workflow Works

✔ 1. Triggers on push

Whenever you push code, the pipeline starts automatically:

`on: [push]`

✔ 2. GitHub starts an Ubuntu runner

It creates a fresh Linux machine to run your code:

`runs-on: ubuntu-latest`

✔ 3. Matrix testing

Your code will be tested on two Python versions: 3.8 and 3.9.

`matrix:
  python-version: [3.8, 3.9]`


This means two parallel test jobs will run.

✔ 4. Checkout the repository

This downloads your code into the runner:

`uses: actions/checkout@v3`

✔ 5. Set up Python

GitHub installs each Python version during matrix testing:

`uses: actions/setup-python@v2
with:
  python-version: ${{ matrix.python-version }}
`
✔ 6. Install dependencies

It installs pytest which is used for running tests:

`pip install pytest`

✔ 7. Run tests

The workflow enters the src folder and runs tests using pytest:

`cd src`
`python -m pytest addition.py`


🎯 Summary

This project demonstrates:

✔ GitHub Actions workflow creation

✔ Testing across multiple Python versions

✔ Installing dependencies using pip

✔ Running automated tests on push

✔ Using pytest inside GitHub CI

This is a great first example of using CI/CD with GitHub Actions.
