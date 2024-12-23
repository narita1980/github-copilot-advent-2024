---
title: GraphAI実行時に発生したpunycodeモジュールの警告とその対処法 (Node.js v21以降の変更)
tags:
  - JavaScript
  - Node.js
  - punycode
  - GraphAI
  - AIAgent
private: false
updated_at: '2024-11-28T02:19:35+09:00'
id: 1e84be57f0ac209ffbaf
organization_url_name: null
slide: false
ignorePublish: false
---
# はじめに

今回は、GraphAI で発生した警告メッセージに関して対処法をまとめます。

# 問題

GraphAI を実行した際に以下のエラーが発生しました。

```bash
$ graphai hello_world.yaml
(node:5336) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
(Use `node --trace-deprecation ...` to show where the warning was created)
{
  "node1": {
    "message": "hello"
  }
}
```

```yaml:hello_world.yaml
version: 0.5
nodes:
  node1:  
    params:
      message: hello
    agent: echoAgent
    isResult: true
```

私の環境は以下の通りです。

- OS: macOS Sonoma 14.5
- npm バージョン: 10.9.0
- Node.js バージョン: v22.11.0
- GraphAI バージョン: 0.5.23

# 解決方法

Node.js の公式ドキュメントに記載されている DEP0040 の履歴セクションによると、`punycode` モジュールは 2016年10月にリリースされた Node.js v7.0.0 以降で非推奨となっており、Node.js v21.0.0 からランタイム非推奨に変更されました  
（詳細は [nodejs/node#47202](https://github.com/nodejs/node/issues/47202) 参照）。  

このランタイム非推奨によって、この警告が現在は目に見える形で表示されるようになったようです。

取り急ぎの対応としては、この警告を無視するか、Node.js のバージョンを v20 系にダウングレードすると解消されるようなので試してみました。

```bash
## v20系にダウングレード
$ node -v
v20.18.1
$ graphai hello_world.yaml 
{
  "node1": {
    "message": "hello"
  }
}
```

# おわりに

今回、GraphAIの検証時に発生した警告メッセージについて気になったので詳細調べてみたら、その関連でyarnのissueをみることになり、とても勉強になりました。

# 参考

以下は、今回の問題解決のために参考にしたリンクです。

- ["[DEP0040] The punycode module is deprecated" with Node.js 21.x](https://github.com/yarnpkg/yarn/issues/9005)
- ["[DEP0040] The punycode module is deprecated" with Node.js 21.x (Rev 2)](https://github.com/yarnpkg/yarn/issues/9013)
