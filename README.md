FaultSight
-----------

FaultSight is a web-based visualization tool designed to be used together with a fault injector (Such as [FlipIt](https://github.com/aperson40/FlipIt) - an LLVM based fault injector designed for HPC applications). The tool is written in such a way that it should be applicable to most fault injectors, regardless of whether they are memory based or instruction based. FaultSight performs analysis upon the injection data, and provides concrete data regarding an application's fault tolerance capabilities. The data is presented in a interactive web page using [D3.js](http://d3js.org) to visualize the fault injection campaign, and allows the user to easily impose custom constraints on the visualized data.

Generated graphs include:

- Classification of injections based on instruction type
- Percent of injections based on function (includes type information)
- Signals generated by execution of code
- Trials with detection (includes bit locations and types)
- Latency of detection
- Trials that unexpectedly terminate (includes bit locations and types)


This program depends on:


- flask_sqlalchemy
```
pip install flask_sqlalchemy
```
- numpy
```
pip install numpy
```
- scipy
```
pip install scipy
```



Usage
-----

To use this tool:

1.) Run an injection campaign via the fault injector of your choosing. We recommend FlipIt, as it is natively supported by this tool.

2.) Generate a FaultSight database (.db) file, which follows a generalized schema that should be applicable to most fault injectors. Follow the information provided in the `Generating a FaultSight database` section below. Place this database file in `/faultSight/database/`, and make sure the database file is called `campaign.db`

3.) `cd` to the `/faultSight/` directory, and run the following command:

```
python run.py
```

4.) FaultSight is now running at the following url:

```
http://127.0.0.1:5000/ (Developed on Google chrome, but there should not be any major issues for other web browsers)
```



Generating a FaultSight database
-----
This tool requires the user to generate the FaultSight database, which follows a generalized schema that should be applicable to most fault injectors. For this purpose, a python script is included, `databaseSetup/databaseSetup.py`, which provides the user with useful API calls (essentially wrappers to SQL queries). Therefore, the user will be required to write a custom python script that parses the output data from their fault injection, and make the appropriate calls to the methods provided in `databaseSetup.py`. This custom script is already provided for users of FlipIt (`databaseSetup/examples/FlipIt/database.py`), and should be used as example code when writing such a script for other fault injectors. If anyone does write such scripts for other fault injectors, I would really appreciate it if you contributed your code to this repository!

For detailed information on generating the database file, look at the README located at `/databaseSetup/README.md`. If you are using FlipIt, there are specific instructions located at `databaseSetup/examples/FlipIt/README.md`


Need more help?
-----
Feel free to email me at eahorn2@illinois.edu with questions anytime!

The [wiki](https://github.com/einarhorn/FaultSight/wiki) will be updated shortly.
