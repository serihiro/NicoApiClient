# NicoApiClient

## 概要
[ニコニコ動画 『スナップショット検索API v2』](https://site.nicovideo.jp/search-api-docs/snapshot) などの API について、仕様をなるべく意識せずに利用できるクライアントを提供する。

## install

PyPIリポジトリ: https://pypi.org/project/nicovideo-api-client/

```shell
pip install nicovideo-api-client
```

### installed

[![Downloads](https://pepy.tech/badge/nicovideo-api-client)](https://pepy.tech/project/nicovideo-api-client) [![Downloads](https://pepy.tech/badge/nicovideo-api-client/month)](https://pepy.tech/project/nicovideo-api-client) [![Downloads](https://pepy.tech/badge/nicovideo-api-client/week)](https://pepy.tech/project/nicovideo-api-client)

### documentation

```bash
sphinx-apidoc -f -e -o ./docs ./nicovideo_api_client
cd docs
make html
```

で `docs/_build/html` にファイルが生成される。

```bash
python3 -m http.server
```

などで適宜サーバーを立てて読むとよい。

## example

```python
from nicovideo_api_client.api.v2.snapshot_search_api_v2 import SnapshotSearchAPIV2
from nicovideo_api_client.constants import FieldType

json = SnapshotSearchAPIV2() \
    .tags_exact() \
    .query("VOCALOID") \
    .field({FieldType.TITLE, FieldType.CONTENT_ID}) \
    .sort(FieldType.VIEW_COUNTER) \
    .simple_filter().filter() \
    .limit(100) \
    .request() \
    .json()
```

## 利用規約

https://site.nicovideo.jp/search-api-docs/snapshot#api%E5%88%A9%E7%94%A8%E8%A6%8F%E7%B4%84
