# Python 3 port of https://pypi.org/project/interval/


Python 3 port done by: haavikko@gmail.com

Doctests pass under Python 3.7. Please report any issues.


# Original project info


## PyPI package description

An Interval represents a continuous range of values. An IntervalSet is like the built-in set class, only it can also contain sets of Interval objects.

## Documentation

The interval module provides the Interval and IntervalSet data types.   
Intervals describe continuous ranges that can be open, closed, half-open,
or infinite.  IntervalSets contain zero to many disjoint sets of 
Intervals.

Intervals don't have to pertain to numbers.  They can contain any data 
that is comparable via the Python operators <, <=, ==, >=, and >.  Here's 
an example of how strings can be used with Intervals:

```python
>>> volume1 = Interval.between("A", "Foe")
>>> volume2 = Interval.between("Fog", "McAfee")
>>> volume3 = Interval.between("McDonalds", "Space")
>>> volume4 = Interval.between("Spade", "Zygote")
>>> encyclopedia = IntervalSet([volume1, volume2, volume3, volume4])
>>> mySet = IntervalSet([volume1, volume3, volume4])
>>> "Meteor" in encyclopedia
True
>>> "Goose" in encyclopedia
True
>>> "Goose" in mySet
False
>>> volume2 in (encyclopedia ^ mySet)
True
```

Here's an example of how times can be used with Intervals:

```python
>>> officeHours = IntervalSet.between("08:00", "17:00")
>>> myLunch = IntervalSet.between("11:30", "12:30")
>>> myHours = IntervalSet.between("08:30", "19:30") - myLunch
>>> myHours.issubset(officeHours)
False
>>> "12:00" in myHours
False
>>> "15:30" in myHours
True
>>> inOffice = officeHours & myHours
>>> print(inOffice)
['08:30'..'11:30'),('12:30'..'17:00']
>>> overtime = myHours - officeHours
>>> print(overtime)
('17:00'..'19:30']
```


## From the project home page:

Project home page at http://members.cox.net/apoco/interval/ is not available as of 2020. Latest copy from the Internet Archive:

interval Module

This is the web page for information on the interval module. The interval module is a pure Python module that provides the Interval, IntervalSet, and FrozenIntervalSet classes. It runs under Python 2.4 and later.

An Interval is an abstraction for a continuous range of values. Some examples of intervals are "all values between 2 and 6," "all values less than 0," and "all values not equal to 'Bob'."

An IntervalSet is like the built-in Python set type, only it is an abstraction for a set of ranges and discrete values rather than just a set of discrete values. Another difference is that unlike sets, that can contain any hashable value, IntervalSet values must be hashable and comparable as well (__hash__ and __cmp__ must be implemented).

An IntervalSet containing the discrete values 2, 4, 6 and all values less than 0 is constructed as follows:

```python
>>> IntervalSet([2, 4, 6, Interval.less_than(0)])
```

All of the same operations for sets apply to the resulting IntervalSet.

FrozenIntervalSet objects are to IntervalSet objects as frozenset objects are to set objects; FrozenIntervalSets are immutable, and IntervalSets aren't. Just like in sets and frozensets, some operations are supported in IntervalSet objects that aren't in FrozenIntervalSet objects, and vice versa.

Installation

The interval module was packaged using the excellent distutils, so installation is a snap. After extracting the archive, from the command line, type "python setup.py install" while in the newly-extracted interval directory.


