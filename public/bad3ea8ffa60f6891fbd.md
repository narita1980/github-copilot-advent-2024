---
title: 【小ネタ】Streamlitのシークレットマネージャー機能を使ってみる
tags:
  - Python
  - SecretsManager
  - Streamlit
private: false
updated_at: '2021-04-15T08:43:13+09:00'
id: bad3ea8ffa60f6891fbd
organization_url_name: null
slide: false
ignorePublish: false
---
# はじめに
Streamlitからのお知らせの中にこんなのを見つけて、試しに使ってみたのでメモがてら投稿します。

> Try out Secrets
> Secrets Management is now available in sharing [just make sure to upgrade to the > 0.80.0 release]. Read more [here](https://blog.streamlit.io/secrets-in-sharing-apps/?utm_source=Streamlit&utm_campaign=a2e1bccf19-EMAIL_CAMPAIGN_2020_11_11_08_14_COPY_01&utm_medium=email&utm_term=0_e7877ed028-a2e1bccf19-395960071) and check out the [docs](https://www.notion.so/Secrets-Management-730c82af2fc048d383d668c4049fb9bf?utm_source=Streamlit&utm_campaign=a2e1bccf19-EMAIL_CAMPAIGN_2020_11_11_08_14_COPY_01&utm_medium=email&utm_term=0_e7877ed028-a2e1bccf19-395960071) to get started.

意訳）
シークレットを試してみる
シークレットマネージメントが0.80.0リリース版で使えるようになったよ。
詳細はドキュメントみてね！

# Secrets Management（シークレットマネージャー）機能について
パスワード情報を直接ソースに書かずに外部から渡すことができる機能。

## サンプルプログラム
```python:streamlit_app.py
import streamlit as st

st.write("DB username:", st.secrets["db_username"])
st.write("DB password:", st.secrets["db_password"])
st.write("My cool secrets:", st.secrets["my_cool_secrets"]["things_i_like"])
```

ローカル環境では、こんな感じでファイルを用意しておくことで利用可能です。

設定ファイル例）

```toml:.streamlit/secrets.toml
db_username = "Jane"
db_password = "12345qwerty"

[my_cool_secrets]
things_i_like = ["Streamlit", "Python"]
```

■実行結果
![スクリーンショット 2021-04-15 8.42.27.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/b5465860-f40f-f457-89b0-caf2d994fd2e.png)


※ また以下のように環境変数としてもアクセス可能です。

```python
import os
st.write("DB username:", os.environ["db_username"])
st.write("DB password:", os.environ["db_password"])
```

# Appendix
## 参考サイト
- [Add secrets to your Streamlit apps](https://blog.streamlit.io/secrets-in-sharing-apps/?utm_source=Streamlit&utm_campaign=a2e1bccf19-EMAIL_CAMPAIGN_2020_11_11_08_14_COPY_01&utm_medium=email&utm_term=0_e7877ed028-a2e1bccf19-395960071)
- [Secrets Management](https://www.notion.so/Secrets-Management-730c82af2fc048d383d668c4049fb9bf)

# ご意見・ご感想をお待ちしております
今回の記事はいかがでしたか？
・こういう記事が読みたい
・こういうところが良かった
・こうした方が良いのではないか
などなど、率直なご意見を募集しております。
頂いたお声は、今後の記事の質向上に役立たせて頂きますので、お気軽に
コメント欄にてご投稿ください。[Twitter](https://twitter.com/narinarita1980)でもご意見を受け付けております。
皆様のメッセージをお待ちしております。
