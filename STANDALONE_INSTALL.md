## Standalone run instructions

For running this locally, without a Civis datascience Docker container

#### Python, pip, and make

Install them, preferrably the latest versions of each. Tested on `Python 3.10.4` and `pip 22.0.2`.

If you're on MacOs or Windows, make sure you have `make` installed (check by running `make --version` in the terminal)

#### Dependencies discovered so-far:

* `pandas`
* `scipy`
* `openpyxl`
* `matplotlib`
* `ipython`
* `nameparser`

Install by running:

```
pip install pandas scipy openpyxl matplotlib ipython nameparser
```

Add dependencies you discover here. Theoretically this should be a subset of what's included in the [Civis Analytics datascience-python docker image @ version 4.20](https://github.com/civisanalytics/datascience-python/blob/v4.2.0/Dockerfile).

### Running a task

Let's say we want to run the `import` task in `individual/roster_1936-2017_2017-04_p058155`. We'd cd into the directory:

```
cd individual/roster_1936-2017_2017-04_p058155/import
```

then run

```
make -f src/Makefile all
```

Once your code runs, you should see a new file in `individual/roster_1936-2017_2017-04_p058155/import/output`

#### Context and more details

There's a lot in the README, but to summarize, each subdirectory of the `individual` directory corresponds to a dataset from CPD. Each subdirectory of `merge` is a task you can perform on one or more CPD datasets.

For subdirectories of `individual`, there are a couple subdirs contained within that describe tasks to be performed on the given data. For instance, the directory `individual/roster_1936-2017_2017-04_p058155` contains the subdirectories:

* `assign-unique-ids`
* `clean`
* `export`
* `import`

All of which describe tasks to be performed on the `roster_1936-2017_2017-04_p058155` file.

Within the `individual/roster_1936-2017_2017-04_p058155/import` directory, we need a bunch of directories, but most crucially we need an `input` directory with the 

If you're ever in doubt about what files you need to make a particular task run, look inside the `src` directory for a python file named the same as your task. For example `individual/roster_1936-2017_2017-04_p058155/import/src/import.py`. In there, you'll see the arguments to the script listed out, as well as the output and metadata files. Eg:

```python
def get_setup():
  ...
  args = {
        'input_file': 'input/P058155_-_Kiefer.xlsx',
        'output_file': 'output/roster_1936-2017_2017-04.csv.gz',
        'metadata_file': 'output/metadata_roster_1936-2017_2017-04.csv.gz',
        'drop_column': 'star11',
        'column_names_key': 'roster_1936-2017_2017-04_p058155'
        }
  ...
```

#### Issues

... There are many. But, for one thing, running 
