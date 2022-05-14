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

### Running an operation

Let's say we want to run the `import` operation in `individual/roster_1936-2017_2017-04_p058155`. We'd cd into the directory:

```
cd individual/roster_1936-2017_2017-04_p058155
```

then run

```
make -f src/Makefile all
```

Once your code runs, you should see a new file in `individual/roster_1936-2017_2017-04_p058155/import/output`

#### Context and more details

There are details in the README, but to summarize, each subdirectory of the `individual` directory corresponds to a dataset from CPD. Each subdirectory of `merge` is an operation you can perform on one or more CPD datasets.

For subdirectories of `individual`, there are a couple subdirs contained within that describe operations to be performed on the given data. For instance, the directory `individual/roster_1936-2017_2017-04_p058155` contains the subdirectories:

* `assign-unique-ids`
* `clean`
* `export`
* `import`

All of which describe operations to be performed on the `roster_1936-2017_2017-04_p058155` file.

Within the `individual/roster_1936-2017_2017-04_p058155/import` directory, we need 

#### Issues

... There are many. But, for one thing, running 
