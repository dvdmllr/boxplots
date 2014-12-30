# Boxplots
Boxplots is a tiny Java library that creates simple ascii-graphs for input datasets. Build to quickly print data distribution to logging output from code or inspect data from command line.

## Usage
### From Code

```java
List<Pair<String, double[]>> data = new ArrayList<>();
data.add(Pair.create("IRIS_SEPAL_LENGTH", IrisData.IRIS_SEPAL_LENGTH));
data.add(Pair.create("IRIS_SEPAL_WIDTH",  IrisData.IRIS_SEPAL_WIDTH));

Plot plot = new Boxplot.BoxplotBuilder(data).plotObject();
plot.printPlot();
```

This will produce the following output to command line:

```
IRIS_SEPAL_LENGTH|                   |-----[░░░░░|░░░░]------------||
IRIS_SEPAL_WIDTH ||-----[░|░]--------|                              |
                 |2.00                                          7.90|
```

### From Command Line
mvn:install will produce an executable jar in the target folder. The program only expects a string representation of a data series as input object. Running on custom data is as easy as:

```
java -jar boxplots-1.0.jar -min 0 -max 20 -data '{series1|1,2,1,2,3,3,4,5,8,2,1}{series2|1,2,1,9,3,7,4,15,8,2,1}'
```

Each data series is enclosed with curly brackets and contains a name and the data points divided by a pipe ("|"). Data is split by a comma (","). Future versions will include parsing of csv files to allow for handling of larger data sets. Setting optional min and max parameters will visually restrict / expand the graph to given range.

## Next Steps
This library will be completed as I see the need for use in other personal projects. Ideas include

* An improved CLI which reads CSV and other data formats
* Tukey boxplots (different treatment of Whiskers and plotting of outliers)
* Improve the legend by showing meaningful values between the min and max
* Allow customized formatting
* Add histograms

Feel free to contribute!