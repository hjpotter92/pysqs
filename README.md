# sqspy

[![codecov][codecov-badge]][codecov] [![Build Status][travis-badge]][travis]

A more pythonic approach to SQS producer/consumer utilities. Heavily
inspired from the [the pySqsListener][1] package.

## Install

```Shell
pip install sqspy
```

## Usage

```Python
from sqspy import Consumer


class MyWorker(Consumer):
    def handle_message(self, body, attributes, message_attributes):
        print(body)


listener = MyWorker('Q1', error_queue='EQ1')
listener.listen()
```

More documentation coming soon.

## Why

The mentioned project had a few issues which I faced while trying to
implement at my organisation. The local environment testing setup was
very flaky. The signatures for `sqs_listener` and `sqs_producer` were
very different from each other.

This rewrite supports __python 3.6+ versions only__, and makes use of a
lot of newer python features. It also makes use of service resources (for
lazy calls) from the boto3 library instead of making calls via the low
level client.


  [1]: https://pypi.org/project/pySqsListener/ "pySqsListener on PyPI"
  [codecov-badge]: https://codecov.io/gh/hjpotter92/sqspy/branch/master/graph/badge.svg?token=6XLSO7NPF9
  [codecov]: https://codecov.io/gh/hjpotter92/sqspy
  [travis-badge]: https://travis-ci.com/hjpotter92/sqspy.svg?branch=master
  [travis]: https://travis-ci.com/hjpotter92/sqspy
