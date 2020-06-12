# API Documentation

## _class_ saleae.data.GraphTime\(datetime: datetime, millisecond=0, \*, microsecond=0, nanosecond=0, picosecond=0\)

A high-precision wall clock time.

The primary way to use this type of value is to subtract two `GraphTime`s to produce a `GraphTimeDelta`. `GraphTimeDelta`s may be freely added and subtracted from each other, and converted to floating point seconds. They can also be added to or subtracted from `GraphTime`s to produce a suitable offset `GraphTime`.

Constructs a `GraphTime` using a [`datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime), and optionally sub-millisecond precision values.

The sub-millisecond precision values must be converible to float.

### \__add\__\(\)

Add a `GraphTimeDelta` value to produce a new `GraphTime`.

### \__str\__\(\)

Converts `GraphTime` to an ISO 8601 string with picosecond precision.

Timezone is always UTC, using the Z suffix.

### \__sub\__\(\)

Subtract a `GraphTime` or `GraphTimeDelta` value.

When subtracting a `GraphTime`, produces a `GraphTimeDelta`.When subtracing a `GraphTimeDelta`, produces a `GraphTime`.

### as\_datetime\(self: GraphTimedatetime\)

Produces a [`datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime) value that is as close as possible to the given value.

The produced [`datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime) is always timezone aware an in the UTC timezone. Local time can be procured using the standard Python [`datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime) conversion functions.

## _class_ saleae.data.GraphTimeDelta\(second=0, millisecond=0, \*, microsecond=0, nanosecond=0, picosecond=0\)

A high-precision duration.

Constructs a GraphTimeDelta using numerical values.

All values must be convertible to float. Multiple prefixes may be specified, the resulting value will be all the values added together.

### \__add\__\(\)

Add a `GraphTimeDelta` value to produce a new `GraphTimeDelta`.

### \__eq\__\(\)

Determine if two `GraphTimeDelta` values are equal, up to a tolerance.

### \__float\__\(\)

Convert to a floating point number of seconds. Note that this can cause a loss of precision for values &gt; 1ms.

### \__ge\__\(\)

Determine if the first `GraphTimeDelta` value is greater than or equal to the second, up to a tolerance.

### \__gt\__\(\)

Determine if the first `GraphTimeDelta` value is greater than the second, up to a tolerance.

### \__le\__\(\)

Determine if the first `GraphTimeDelta` value is less than or equal to the second, up to a tolerance.

### \__lt\__\(\)

Determine if the first `GraphTimeDelta` value is less than the second, up to a tolerance.

### \__ne\__\(\)

Determine if two `GraphTimeDelta` values are not equal, up to a tolerance.

### \__sub\__\(\)

Subtract a `GraphTimeDelta` value to produce a new `GraphTimeDelta`.

## _class_ saleae.analyzers.HighLevelAnalyzer\(\)

Base class for High Level Analyzers. Subclasses must implement the `decode()` function

### decode\(frame: saleae.analyzers.high\_level\_analyzer.AnalyzerFrame\)

Decode a frame from an input analyzer, and return None or 1 or more `AnalyzerFrame` objects.

## _class_ saleae.analyzers.AnalyzerFrame\(type: [str](https://docs.python.org/3/library/stdtypes.html#str), start\_time: saleae.data.timing.GraphTime, end\_time: saleae.data.timing.GraphTime, data: [dict](https://docs.python.org/3/library/stdtypes.html#dict) = None\)

A frame produced by an analyzer. The types of frames and the fields in each will depend on the analyzer.

* **Variables**
  * [**type**](https://docs.python.org/3/library/functions.html#type) \([_str_](https://docs.python.org/3/library/stdtypes.html#str)\) – Frame type
  * **start\_time** \(_saleae.data.GraphTime_\) – Start of frame
  * **end\_time** \(_saleae.data.GraphTime_\) – End of frame
  * **data** \([_dict_](https://docs.python.org/3/library/stdtypes.html#dict)\) – Key/value data associated with this frame

## _class_ saleae.analyzers.StringSetting\(\*\*kwargs\)

String setting.

## _class_ saleae.analyzers.NumberSetting\(\*, min\_value=None, max\_value=None, \*\*kwargs\)

Number setting, with an option min\_value/max\_value.

## _class_ saleae.analyzers.ChoicesSetting\(choices, \*\*kwargs\)

Choices setting.
