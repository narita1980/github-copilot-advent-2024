---
title: 【小ネタ】Streamlit でクエリパラメータはexperimental_get_query_paramsで取得できる
tags:
  - Python
  - Streamlit
private: false
updated_at: '2021-04-13T23:49:03+09:00'
id: 6d7aa2b6cbebafedc123
organization_url_name: null
slide: false
ignorePublish: false
---
# はじめに
公式ドキュメントを検索しても使い方が見つからなかったのですが、Streamlit Version 0.65.0で追加されてるのを発見し使い方について調査したものを記事にまとめました。

# クエリパラメータの取得方法
タイトルに記載の通り、`experimental_get_query_params()`メソッドにて取得可能です。

## サンプルプログラム
```python:streamlit_app.py
import streamlit as st
params = st.experimental_get_query_params()

#
# 例： http://localhost:8501?name=abc&name2=5 の場合
# paramsには以下のように格納される
# {
#   "name": [
#     "abc"
#   ],
#   "name2": [
#     "5"
#   ]
# }
```

## お試しサイト
こちらのサイトに検証用のサイトを構築しましたのでテストされたい方はアクセスしてみてください。

### 検証用サイトのソース
#### サンプルプログラム
```python:streamlit_app.py
import streamlit as st

st.title('Streamlitでクエリパラメータを取得するサンプル')

params = st.experimental_get_query_params()
st.write('experimental_get_query_params() の実行結果')
st.write(params)
```

### 検証用サイトのURL
https://share.streamlit.io/narita1980/streamlit-query-params/main

# Appendix
## 参考サイト
- [Changelog - Streamlit 0.65.0 documentation](https://docs.streamlit.io/en/stable/changelog.html?highlight=query%20param#version-0-65-0)

# ご意見・ご感想をお待ちしております
今回の記事はいかがでしたか？
・こういう記事が読みたい
・こういうところが良かった
・こうした方が良いのではないか
などなど、率直なご意見を募集しております。
頂いたお声は、今後の記事の質向上に役立たせて頂きますので、お気軽に
コメント欄にてご投稿ください。[Twitter](https://twitter.com/narinarita1980)でもご意見を受け付けております。
皆様のメッセージをお待ちしております。
