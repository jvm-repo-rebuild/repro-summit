# Initial tests to rebuild npm or pip packages

## PyPI idna 3.2

UI: https://pypi.org/project/idna/#files

metadata: https://pypi.org/pypi/idna/json

```
...
    "project_url": "https://pypi.org/project/idna/",
    "project_urls": {
      "Changelog": "https://github.com/kjd/idna/blob/master/HISTORY.rst",
      "Issue tracker": "https://github.com/kjd/idna/issues",
      "Source": "https://github.com/kjd/idna"
    },
    "release_url": "https://pypi.org/project/idna/3.4/",
...
    "3.2": [
      {
        "comment_text": "",
        "digests": {
          "md5": "2b8eb29d7f1082ae8a7318cfa84e10bb",
          "sha256": "14475042e284991034cb48e06f6851428fb14c4dc953acd9be9a5e95c7b6dd7a"
        },
        "downloads": -1,
        "filename": "idna-3.2-py3-none-any.whl",
        "has_sig": false,
        "md5_digest": "2b8eb29d7f1082ae8a7318cfa84e10bb",
        "packagetype": "bdist_wheel",
        "python_version": "py3",
        "requires_python": ">=3.5",
        "size": 59633,
        "upload_time": "2021-05-29T16:53:30",
        "upload_time_iso_8601": "2021-05-29T16:53:30.337489Z",
        "url": "https://files.pythonhosted.org/packages/d7/77/ff688d1504cdc4db2a938e2b7b9adee5dd52e34efbd2431051efc9984de9/idna-3.2-py3-none-any.whl",
        "yanked": false,
        "yanked_reason": null
      },
      {
        "comment_text": "",
        "digests": {
          "md5": "08ea8e2ce09e522424e872409c221138",
          "sha256": "467fbad99067910785144ce333826c71fb0e63a425657295239737f7ecd125f3"
        },
        "downloads": -1,
        "filename": "idna-3.2.tar.gz",
        "has_sig": false,
        "md5_digest": "08ea8e2ce09e522424e872409c221138",
        "packagetype": "sdist",
        "python_version": "source",
        "requires_python": ">=3.5",
        "size": 243962,
        "upload_time": "2021-05-29T16:53:32",
        "upload_time_iso_8601": "2021-05-29T16:53:32.008652Z",
        "url": "https://files.pythonhosted.org/packages/cb/38/4c4d00ddfa48abe616d7e572e02a04273603db446975ab46bbcd36552005/idna-3.2.tar.gz",
        "yanked": false,
        "yanked_reason": null
      }
    ],
...
```


Debian package tracker https://tracker.debian.org/pkg/python-idna

checkout `v3.2`

```
python3 setup.py build bdist_wheel sdist
```

results:
```
dist/idna-3.2-py3-none-any.whl
dist/idna-3.2.tar.gz
```

compare with reference PyPI content:
```
wget https://files.pythonhosted.org/packages/cb/38/4c4d00ddfa48abe616d7e572e02a04273603db446975ab46bbcd36552005/idna-3.2.tar.gz
diffoscope idna-3.2.tar.gz dist/idna-3.2.tar.gz

wget https://files.pythonhosted.org/packages/d7/77/ff688d1504cdc4db2a938e2b7b9adee5dd52e34efbd2431051efc9984de9/idna-3.2-py3-none-any.whl
diffoscope idna-3.2-py3-none-any.whl dist/idna-3.2-py3-none-any.whl
```

results:

```
--- idna-3.2.tar.gz
+++ dist/idna-3.2.tar.gz
├── filetype from file(1)
│ @@ -1 +1 @@
│ -gzip compressed data, was "idna-3.2.tar", last modified: Sat May 29 16:50:53 2021, max compression
│ +gzip compressed data, was "idna-3.2.tar", last modified: Wed Nov  2 14:58:11 2022, max compression
├── idna-3.2.tar
│ ├── file list
│ │ @@ -1,37 +1,35 @@
│ │ -drwxr-xr-x   0 kim.davies (475842308) ICANN\Domain Users (1205227579)        0 2021-05-29 16:50:53.469700 idna-3.2/
│ │ --rw-r--r--   0 kim.davies (475842308) ICANN\Domain Users (1205227579)     5112 2021-05-29 16:43:12.000000 idna-3.2/HISTORY.rst
│ │ --rw-r--r--   0 kim.davies (475842308) ICANN\Domain Users (1205227579)     1523 2021-03-08 17:06:35.000000 idna-3.2/LICENSE.md
...
│ │ --rwxr-xr-x   0 kim.davies (475842308) ICANN\Domain Users (1205227579)    24140 2021-03-08 17:06:35.000000 idna-3.2/tools/idna-data
│ │ --rw-r--r--   0 kim.davies (475842308) ICANN\Domain Users (1205227579)     1933 2021-03-08 17:06:35.000000 idna-3.2/tools/intranges.py
│ │ +drwxr-xr-x   0 hboutemy   (501) staff       (20)        0 2022-11-02 14:58:11.193847 idna-3.2/
│ │ +-rw-r--r--   0 hboutemy   (501) staff       (20)     5112 2022-11-02 14:45:17.000000 idna-3.2/HISTORY.rst
│ │ +-rw-r--r--   0 hboutemy   (501) staff       (20)     1523 2022-11-02 14:45:17.000000 idna-3.2/LICENSE.md
...
│ │ +-rwxr-xr-x   0 hboutemy   (501) staff       (20)    24140 2022-11-02 14:45:17.000000 idna-3.2/tools/idna-data
│ │ +-rw-r--r--   0 hboutemy   (501) staff       (20)     1933 2022-11-02 14:45:17.000000 idna-3.2/tools/intranges.py
│ ├── idna-3.2/PKG-INFO
│ │ @@ -1,210 +1,15 @@
│ │ -Metadata-Version: 1.2
│ │ +Metadata-Version: 2.1
│ │  Name: idna
│ │  Version: 3.2
│ │  Summary: Internationalized Domain Names in Applications (IDNA)
│ │  Home-page: https://github.com/kjd/idna
│ │  Author: Kim Davies
│ │  Author-email: kim@cynosure.com.au
│ │  License: BSD-3-Clause
│ │ -Description: Internationalized Domain Names in Applications (IDNA)
...
│ │ -        `Unicode IDNA Compatibility Processing <https://unicode.org/reports/tr46/>`_.
│ │ -
│ │  Platform: UNKNOWN
│ │  Classifier: Development Status :: 5 - Production/Stable
│ │  Classifier: Intended Audience :: Developers
│ │  Classifier: Intended Audience :: System Administrators
│ │  Classifier: License :: OSI Approved :: BSD License
│ │  Classifier: Operating System :: OS Independent
│ │  Classifier: Programming Language :: Python
│ │ @@ -217,7 +22,205 @@
│ │  Classifier: Programming Language :: Python :: 3.9
│ │  Classifier: Programming Language :: Python :: Implementation :: CPython
│ │  Classifier: Programming Language :: Python :: Implementation :: PyPy
│ │  Classifier: Topic :: Internet :: Name Service (DNS)
│ │  Classifier: Topic :: Software Development :: Libraries :: Python Modules
│ │  Classifier: Topic :: Utilities
│ │  Requires-Python: >=3.5
│ │ +License-File: LICENSE.md
...
│ │ +`Unicode IDNA Compatibility Processing <https://unicode.org/reports/tr46/>`_.
│ │ +
│ │ +
│ ├── idna-3.2/idna.egg-info/PKG-INFO
│ │ @@ -1,210 +1,15 @@
│ │ -Metadata-Version: 1.2
│ │ +Metadata-Version: 2.1
│ │  Name: idna
│ │  Version: 3.2
│ │  Summary: Internationalized Domain Names in Applications (IDNA)
│ │  Home-page: https://github.com/kjd/idna
│ │  Author: Kim Davies
│ │  Author-email: kim@cynosure.com.au
│ │  License: BSD-3-Clause
│ │ -Description: Internationalized Domain Names in Applications (IDNA)
...
│ │ -        `Unicode IDNA Compatibility Processing <https://unicode.org/reports/tr46/>`_.
│ │ -
│ │  Platform: UNKNOWN
│ │  Classifier: Development Status :: 5 - Production/Stable
│ │  Classifier: Intended Audience :: Developers
│ │  Classifier: Intended Audience :: System Administrators
│ │  Classifier: License :: OSI Approved :: BSD License
│ │  Classifier: Operating System :: OS Independent
│ │  Classifier: Programming Language :: Python
│ │ @@ -217,7 +22,205 @@
│ │  Classifier: Programming Language :: Python :: 3.9
│ │  Classifier: Programming Language :: Python :: Implementation :: CPython
│ │  Classifier: Programming Language :: Python :: Implementation :: PyPy
│ │  Classifier: Topic :: Internet :: Name Service (DNS)
│ │  Classifier: Topic :: Software Development :: Libraries :: Python Modules
│ │  Classifier: Topic :: Utilities
│ │  Requires-Python: >=3.5
│ │ +License-File: LICENSE.md
...
│ │ +`Unicode IDNA Compatibility Processing <https://unicode.org/reports/tr46/>`_.
│ │ +
│ │ +
│ ├── idna-3.2/idna.egg-info/SOURCES.txt
│ │ @@ -20,11 +20,9 @@
│ │  tests/__init__.py
│ │  tests/test_idna.py
│ │  tests/test_idna_codec.py
│ │  tests/test_idna_compat.py
│ │  tests/test_idna_other.py
│ │  tests/test_idna_uts46.py
│ │  tests/test_intranges.py
│ │ -tools/12.txt
│ │ -tools/13.txt
│ │  tools/idna-data
│ │  tools/intranges.py
```

differences explanation:
- tar.gz uid/gid + timestamp
- metadata generated by setupy.py: probably a prerequisite on a precise version of a packaging library
- 2 extra files in reference release source that are not in Git...

```
--- idna-3.2-py3-none-any.whl
+++ dist/idna-3.2-py3-none-any.whl
├── zipinfo {}
│ @@ -1,16 +1,16 @@
│ -Zip file size: 59633 bytes, number of entries: 14
│ --rw-r--r--  2.0 unx      849 b- defN 21-Mar-08 17:06 idna/__init__.py
...
│ -?rw-rw-r--  2.0 unx     1011 b- defN 21-May-29 16:50 idna-3.2.dist-info/RECORD
│ -14 files, 274910 bytes uncompressed, 57997 bytes compressed:  78.9%
│ +Zip file size: 59651 bytes, number of entries: 14
│ +-rw-r--r--  2.0 unx      849 b- defN 22-Nov-02 14:43 idna/__init__.py
...
│ +?rw-rw-r--  2.0 unx     1011 b- defN 22-Nov-02 14:58 idna-3.2.dist-info/RECORD
│ +14 files, 274935 bytes uncompressed, 58015 bytes compressed:  78.9%
├── idna-3.2.dist-info/METADATA
│ @@ -22,14 +22,15 @@
│  Classifier: Programming Language :: Python :: 3.9
│  Classifier: Programming Language :: Python :: Implementation :: CPython
│  Classifier: Programming Language :: Python :: Implementation :: PyPy
│  Classifier: Topic :: Internet :: Name Service (DNS)
│  Classifier: Topic :: Software Development :: Libraries :: Python Modules
│  Classifier: Topic :: Utilities
│  Requires-Python: >=3.5
│ +License-File: LICENSE.md
│
│  Internationalized Domain Names in Applications (IDNA)
│  =====================================================
│
│  Support for the Internationalised Domain Names in Applications
│  (IDNA) protocol as specified in `RFC 5891 <https://tools.ietf.org/html/rfc5891>`_.
│  This is the latest version of the protocol and is sometimes referred to as
├── idna-3.2.dist-info/WHEEL
│ @@ -1,5 +1,5 @@
│  Wheel-Version: 1.0
│ -Generator: bdist_wheel (0.36.2)
│ +Generator: bdist_wheel (0.37.0)
│  Root-Is-Purelib: true
│  Tag: py3-none-any
├── idna-3.2.dist-info/RECORD
│ @@ -4,11 +4,11 @@
│  idna/core.py,sha256=icq2P13S6JMjoXgKhhd6ihhby7QsnZlNfniH6fLyf6U,12826
│  idna/idnadata.py,sha256=cl4x9RLdw1ZMtEEbvKwAsX-Id3AdIjO5U3HaoKM6VGs,42350
│  idna/intranges.py,sha256=EqgXwyATAn-CTACInqH9tYsYAitGB2VcQ50RZt_Cpjs,1933
│  idna/package_data.py,sha256=_028B4fvadRIaXMwMYjhuQPP3AxTIt1IRE7X6RDR4Mk,21
│  idna/py.typed,sha256=47DEQpj8HBSa-_TImW-5JCeuQeRkm5NMpJWZG3hSuFU,0
│  idna/uts46data.py,sha256=DGzwDQv8JijY17I_7ondo3stjFjNnjvVAbA-z0k1XOE,201849
│  idna-3.2.dist-info/LICENSE.md,sha256=otbk2UC9JNvnuWRc3hmpeSzFHbeuDVrNMBrIYMqj6DY,1523
│ -idna-3.2.dist-info/METADATA,sha256=L6eIrqdmpRK2oKwBFd8CcID4FQ8h2SYKf2fg7KEQLG0,8638
│ -idna-3.2.dist-info/WHEEL,sha256=OqRkF0eY5GHssMorFjlbTIq072vpHpF60fIQA6lS9xA,92
│ +idna-3.2.dist-info/METADATA,sha256=lzAHR9geyHs-m4fSuqNgrFq5s6CVWVNrusk4QKYWu1k,8663
│ +idna-3.2.dist-info/WHEEL,sha256=ewwEueio1C2XeHTvT17n8dZUJgOvyCWCt0WVNLClP9o,92
│  idna-3.2.dist-info/top_level.txt,sha256=jSag9sEDqvSPftxOQy-ABfGV_RSy7oFh4zZJpODV8k0,5
│  idna-3.2.dist-info/RECORD,,
```

differences explanation:
- zip timestamp
- bdist_wheel package version difference used during package build
