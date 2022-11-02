# Initial tests to rebuild npm or pip packages

## PyPI idna

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

TODO: compare with reference PyPI content...
