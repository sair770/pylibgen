# pylibgen

[![PyPI](https://img.shields.io/pypi/v/pylibgen.svg)](https://pypi.org/project/pylibgen/)
[![Travis CI](https://travis-ci.org/JoshuaRLi/pylibgen.svg?branch=master)](https://travis-ci.org/JoshuaRLi/pylibgen)
[![License MIT](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/JoshuaRLi/pylibgen/blob/master/LICENSE)

Python interface to Library Genesis. Currently, only the LibGen/Sci-Tech database is supported.

You may also be interested in [libgen-cli](https://github.com/JoshuaRLi/libgen-cli).


## Installation

pylibgen is well-tested on Python 3.6 - 3.7, and can be installed via `pip`. For example:

    python3 -m pip install pylibgen --user


## Usage

```python
>>> from pylibgen import Library
>>> l = Library()
>>> ids = l.search('stallman essays')
>>> ids
['112887', '310297', '688326', '1594161', '1610379']
>>> book1, book2, *_ = l.lookup(ids)
>>> book1.__dict__
{'id': '112887', 'title': 'Free software, free society: selected essays of Richard M. Stallman', 'author': 'Richard M. Stallman, Lawrence Lessig, Joshua Gay, Laurence Lessig', 'year': '2002', 'edition': 'First Printing, First Edition', 'pages': '230', 'identifier': '9781882114986,1882114981', 'extension': 'pdf', 'filesize': '2210323', 'md5': '861C055B960E7F36D95164CAB34E0E97'}
>>> book2.__dict__
{'id': '310297', 'title': 'Free Software Free Society: Selected Essays of Richard Stallman', 'author': 'Richard Stallman', 'year': '2010', 'edition': '2nd Edition', 'pages': '278', 'identifier': '0983159203,9780983159209', 'extension': 'pdf', 'filesize': '1597349', 'md5': '6C3C2593BBB5D77154D50DFDDC0EA669'}
>>> book1.get_url()
'https://libgen.pw/item/detail/id/112887'
>>> book1.get_url(filehost='b-ok.org')
'http://b-ok.org/md5/861C055B960E7F36D95164CAB34E0E97'
```


## Support Library Genesis\!

`Book.get_url(filehost='...')` will return the standard filehost gateway url.

There is no functionality to bypass any intermediate advertisement pages, and this behavior is intended because Library Genesis is a service worth supporting.


## Development Setup

You'll need python 3.6 and 3.7, as well as `pipenv` and `tox` installed, preferably under the latest python. It's recommended to use [`pyenv`](https://github.com/pyenv/pyenv) to install + manage python versions and executable modules. For example:

    pyenv install 3.6.6
    pyenv install 3.7.0
    pyenv global 3.7.0 3.6.6
    python3.7 -m pip install pipenv tox

To setup and enter the virtual environment for development:

    pipenv install --dev
    pipenv shell
    pre-commit install


## Disclaimer

Use `pylibgen` responsibly and at your own risk. The author(s) are not responsible or liable for any piracy, copyright infringement, or other offences committed by anyone using this software. Please consider supporting your favorite authors by purchasing their works\!
