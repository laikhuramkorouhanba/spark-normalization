Normalising the numerical columns of a household power consumption log using Spark.

The data is minute-by-minute electrical readings from a single household over several years, which makes it large enough that the normalisation is worth distributing rather than doing in memory. That is really the point of the exercise. Min-max scaling is trivial arithmetic, but computing it across a distributed dataset means one pass to find each column's minimum and maximum and a second to apply the transform, and being deliberate about that is the difference between something that runs and something that runs out of memory.

The file is semicolon-separated with nine fields per record, and missing readings appear as question marks rather than empty cells, so parsing has to handle that before any arithmetic happens.

##$$ Data

Individual Household Electric Power Consumption, UCI Machine Learning Repository:
https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption

Fields are date, time, global active power, global reactive power, voltage, global intensity, and three sub-metering readings.
