# abc - Apache Benchmark Charter

Simple tool to ease HTTP benchmarks and plot them by:

* Providing a way to store `ab` results
* Providing better and more beatiful graphs from gnuplot
* Providing a (unix-friendly) command to do this for you

Requirements:

* Bash
* GNU Sed
* Apache (or just the `ab` tool)

Patches, bug fixes, improvements, suggestions and beer are very welcome!

# Workflow (or "How to use it")

If you ever used `ab`, you are ready to use `abc`. Just use `abc` instead of `ab`.

`abc` will store the data inside a directory so you can git-it. This directory has a convention:

> A benchmark **project** (site) has **sessions** (configs), that holds the **runs** (results).

For every *session*, `abc` will provide a shell script called `run.sh` that will create new results. *Session* names defaults to the parameters used to run `ab`.

All is kept inside the `ABC_PROJECTS` environment variable, that defaults to `~/abc-projects` and will end up having a structure like this:

```
/home/augustohp/abc-projects/
└── google.com
    └── n10c2
        ├── 2013-08-30_01:21:42
        │   ├── ab.out
        │   ├── gnuplot.data
        │   └── runtime.csv
        ├── 2013-08-30_01:21:47
        │   ├── ab.out
        │   ├── gnuplot.data
        │   └── runtime.csv
        ├── 2013-08-30_01:21:51
        │   ├── ab.out
        │   ├── gnuplot.data
        │   └── runtime.csv
        └── run.sh
```