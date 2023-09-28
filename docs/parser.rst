======
parser
======

.. automodule:: dateutil.parser

Functions
---------

.. automethod:: dateutil.parser.parse

.. automethod:: dateutil.parser.isoparse


Classes
-------

.. autoclass:: dateutil.parser.parserinfo
  :members:
  :undoc-members:


Warnings and Exceptions
-----------------------

.. autoclass:: dateutil.parser.ParserError

.. autoclass:: dateutil.parser.UnknownTimezoneWarning

.. testsetup:: parser

Examples
--------

Parser "parse" examples::

.. doctest:: parse

    >>> from dateutil.tz import gettz
    >>> from dateutil.parser import parse
    >>> from dateutil.parser import isoparse

    >>> parse("2012-01-19 17:21:00 CST", tzinfos=tzinfos)
    2012-01-19 17:21:00-06:00
    >>> tzinfos = {"BRST": -7200, "CST": gettz("America/Chicago")}
    >>> parse("2012-01-19 17:21:00 BRST", tzinfos=tzinfos)
    2012-01-19 17:21:00-02:00

fuzzy_with_token is set to True, returns a tuple with the parsed date and a tuple with unrecognized keywords::

.. doctest:: parse

    >>> parse("Today is January 1, 2047 at 8:21:00AM", fuzzy_with_tokens=True)
    (datetime.datetime(2047, 1, 1, 8, 21), ('Today is ', ' ', ' ', 'at '))

Parser "isoparse" (ISO-8601) examples::

.. doctest:: isoparse

    >>> from dateutil.parser import isoparse

Format 'YYYY-MM-DD hh:mm:ss'

.. doctest:: isoparse

    >>> isoparse('2012-01-19 17:21:05')
    2012-01-19 17:21:05

Format 'YYYYMMDD'

.. doctest:: isoparse

    >>> isoparse('20120119')
    2012-01-19 00:00:00

Format 'YYYYMMDD hhmmss'

.. doctest:: isoparse

    >>> isoparse('20120119 172105')
    2012-01-19 17:21:05

Format 'DDMMYYY hhmmss.ssssss'

.. doctest:: isoparse

    >>> isoparse('20120119 172105.123456')
    2012-01-19 17:21:05.123456
    >>> isoparse('2020-08-20T03:33:46.000Z')
    2020-08-20 03:33:46+00:00


