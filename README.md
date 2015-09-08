# Eve Genie

[![Documentation](https://readthedocs.org/projects/evegenie/badge/?version=latest)](http://evegenie.readthedocs.org/en/latest/) [![Build Status](https://travis-ci.org/newmediadenver/evegenie.svg?branch=master)](https://travis-ci.org/newmediadenver/evegenie) [![Coverage Status](https://coveralls.io/repos/newmediadenver/evegenie/badge.svg?branch=master&service=github)](https://coveralls.io/github/newmediadenver/evegenie?branch=master)

A tool for making Eve schema generation easier.

**Use case**: You need to stand up an api quickly. You know what your data looks like in JSON but don't yet know the syntax for Eve/Cerberus.

## Requirements

    sudo pip install -r requirements.txt

## Use

    python geneve.py your_json_file

### In code

```py
from evegenie import EveGenie
eg = EveGenie(filename='test.json')
# Or
with open('test.json', 'r') as ifile:
    data = ifile.read()
eg = EveGenie(data=data)
eg.write_file('mytest.settings.py')
```

    cat mytest.settings.py

    user = {
        'schema': {
            'name': {'type': 'string'},
            'title': {'type': 'string'},
            'age': {'type': 'integer'},
            'alive': {'type': 'boolean'},
            'inventory': {'type': 'list'},
            'address': {
                'type': 'dict',
                'schema': {
                    'city': {'type': 'string'},
                    'state': {'type': 'string'},
                    'address': {'type': 'string'},
                }
            }
        }
    }

    artifact = {
        'schema': {
            'color': {'type': 'string'},
            'cost': {'type': 'float'},
            'stats': {
                'type': 'dict',
                'schema': {
                    'length': {'type': 'float'},
                    'weight': {'type': 'float'},
                    'power': {'type': 'integer'},
                }
            }
            'name': {'type': 'string'},
        }
    }

## Test

    py.test egtest.py

=======
[More detailed docs](/docs/index.md) or [evegenie.readthedocs.org](http://evegenie.readthedocs.org/en/latest/)
