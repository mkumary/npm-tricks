# npm-tricks


Command to find globally installed npm packages in your work station.

```npm list -g --depth 0```


Command to remove all globally installed packages.


```npm ls -gp --depth=0 | awk -F/ '/node_modules/ && !/\/npm$/ {print $NF}' | xargs npm -g rm```


step1  : lists all global top level node-modules 

```npm ls -gp --depth=0``` 

step2 : filter all modules that are not actually npm itself (does not end with /npm)

```awk -F/ '/node_modules/ && !/\/npm$/ {print $NF}'``` 

step 3: removes all modules globally that come over the previous pipe

```xargs npm -g rm``` 
