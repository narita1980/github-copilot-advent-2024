---
title: Simple.cssチートシート
tags:
  - CSS
  - チートシート
  - cssフレームワーク
  - Simple.css
private: false
updated_at: '2022-02-22T03:13:08+09:00'
id: fd2ccf0e91944aab9fd5
organization_url_name: null
slide: false
ignorePublish: false
---
ちょっと前にリリースされたKomesan[^Komesan]や、まとも検索[^まとも検索]をみてシンプルで良いなと思ったら、Simple.cssを使ってこの画面イメージを作成していることがわかったのでメモがてら記事をまとめてみました。

- Komesanの画面ショット
![スクリーンショット 2022-02-21 16.12.09.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/580b48b9-a3cc-86fb-61a8-514c205df74f.png)

# Simple.css とは

> Simple.css is a classless CSS template that allows you to make a good looking website really quickly.

直訳）Simple.cssはクラスレスのCSSフレームワークで、セマンティックなHTMLを素早く見栄え良くすることができます。

公式サイトにある例のように通常のHTMLファイルにCSSを適用するだけで良い感じのサイトにすることが可能です。

例
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My New Website</title>
</head>
<body>
  <header>
    <h1>Hello, world</h1>
    <p>Welcome to my website!</p>
  </header>

  <main>
    <p>This is my new website and it's using Simple.css. It's really cool. If you want to use it too, you can <a href="https://simplecss.org">visit their site</a>.</p>
  </main>

  <footer>
    <p>Jane Smith's website.</p>
  </footer>
</body>
</html>
```

![unformatted-html.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/01876fdd-e0b2-b1eb-85f1-c8a97e60964c.png)

これがSimple.cssを適用するとこんな感じの画面になります。

![simple-css-formatted-html.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/04493b6b-ae3d-df0a-38e1-147b0647205a.png)

# 要素一覧
## Links - リンク

```
<a href="https://example.com">I'm a hyperlink</a>
```

**結果**
![スクリーンショット 2022-02-21 21.01.10.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/361423f0-584b-5d8c-d10d-8df29e79eedc.png)

## Buttons - ボタン

```
<button>I'm a button</button>
```

**結果**
![スクリーンショット 2022-02-21 21.04.41.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/0ec881f2-2ff1-c884-ec2f-14f13a376705.png)

以下のようにリンクとボタンの組み合わせも可能
```
<a href="https://example.com"><button>I'm a button with a link</button></a>
```

**結果**
![スクリーンショット 2022-02-21 21.06.21.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/e6c6937f-8211-f381-9532-32727ba0fd6d.png)

## Bold text - 太字

```
<b>Bold text</b>
```

**結果**
![スクリーンショット 2022-02-22 2.40.27.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/a1d83eab-12ca-efbe-a4f4-204de2106e3c.png)


## Italic text - イタリック体

```
<i>Italic text</i>
```

**結果**
![スクリーンショット 2022-02-22 2.41.34.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/c28ce009-ea3e-f732-9900-f369056b26f8.png)

## Underlined text - 下線

```
<u>Underlined text</u>
```

**結果**
![スクリーンショット 2022-02-22 2.47.23.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/5661c4d9-bdcb-3116-81dd-10ea9be8b05c.png)

## Highlighted text - ハイライトテキスト

```
<mark>Highlighted text</mark>
```

**結果**
![スクリーンショット 2022-02-22 2.48.06.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/c24f51df-b51c-3bf6-4987-38fcefc29199.png)



## Inline code - インラインコード

```
<code>Inline code</code>
```

**結果**
![スクリーンショット 2022-02-22 2.49.08.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/72567529-b56f-d74f-df32-26d971c29f30.png)

## kbd - キーボードコマンド

```
<kbd>Alt+F4</kbd>
```

**結果**
![スクリーンショット 2022-02-22 2.50.10.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/40a84358-d436-d4e0-07ee-9190cbd72b15.png)

## Lists - リスト
### 順序なしリスト

```
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```

**結果**
![スクリーンショット 2022-02-22 2.53.12.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/885eb8d1-69e2-40c3-9ed6-c61d369bde5a.png)

### 順序ありリスト

```
<ol>
  <li>Do this thing</li>
  <li>Do that thing</li>
  <li>Do the other thing</li>
</ol>
```

**結果**
![スクリーンショット 2022-02-22 2.55.13.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/bfdee645-9b34-7919-3186-5e81a01cf622.png)

## Blockquotes　- 引用

```
<blockquote>
  <p>Friends don’t spy; true friendship is about privacy, too.</p>
  <p><cite>– Stephen King</cite></p>
</blockquote>
```

**結果**
![スクリーンショット 2022-02-22 2.56.32.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/828e0004-b6e3-e711-1091-dc935c0b9dd8.png)

## Code blocks - コードブロック

```
<pre>
  <code>
    body {
      color: var(--text);
      background: var(--bg);
      font-size: 1.15rem;
      line-height: 1.5;
      margin: 0;
    }
  </code>
</pre>
```

**結果**
![スクリーンショット 2022-02-22 2.59.40.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/0d7d86f3-69c4-c1f2-8ead-234094c6799f.png)

## Navigation - ナビゲーション

```
<nav>
  <a href="/">Home</a>
  <a href="/about">About</a>
  <a href="/blog">Blog</a>
  <a href="/notes">Notes</a>
  <a href="/guestbook">Guestbook</a>
  <a href="/contact">Contact</a>
</nav>
```

**結果**
![スクリーンショット 2022-02-22 3.01.24.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/204e133b-297c-aa2a-e2e6-51a265eaaa85.png)

## Images

### 標準

```
<img alt="A dog on an iPad" src="https://4.bp.blogspot.com/-eNF2ObT1jT0/XNE_zbjGRZI/AAAAAAABS0c/XBva9hjS4xgmxIqowmOPE0xatvNi0vLLQCLcBGAs/s800/watch_face_arm_woman.png" />
```

**結果**
![スクリーンショット 2022-02-22 3.04.06.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/168e50fb-cf20-5865-52fe-5ec92bdb5e1d.png)

### キャプション付き

```
<figure>
  <img alt="This is a black swan" src="https://4.bp.blogspot.com/-eNF2ObT1jT0/XNE_zbjGRZI/AAAAAAABS0c/XBva9hjS4xgmxIqowmOPE0xatvNi0vLLQCLcBGAs/s800/watch_face_arm_woman.png" />
  <figcaption>This is a black swan</figcaption>
</figure>
```

**結果**
![スクリーンショット 2022-02-22 3.06.29.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/8e31c4d6-fa1b-5dfb-0703-3a82d67a3656.png)

## Accordions - アコーディオン

```
<details>
  <summary>Spoiler alert!</summary>
  <p>You smell. 🙂</p>
</details>
```

**結果**
閉じてる状態
![スクリーンショット 2022-02-22 3.07.18.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/4c6336d5-f574-f7cf-36ad-dc734c432fd9.png)

開いた状態
![スクリーンショット 2022-02-22 3.07.24.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/f979e929-d88e-4c4d-8fba-9c0490bdaad2.png)

## Tables - テーブル

```
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Number</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Jackie</td>
      <td>012345</td>
    </tr>
    <tr>
      <td>Lucy</td>
      <td>112346</td>
    </tr>
  </tbody>
</table>
```

**結果**
![スクリーンショット 2022-02-22 3.08.42.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/575fe2be-88d6-de07-d9f4-463bcc03aaf1.png)


## Forms - フォーム

```
<form>
  <p><strong>This is just a test form. It doesn't do anything.</strong></p>

  <p><select>
    <option selected="selected" value="1">Title</option>
    <option value="2">Mr</option>
    <option value="3">Miss</option>
    <option value="4">Mrs</option>
    <option value="5">Other</option>
  </select></p>

  <p>
  <label>First name</label><br>
  <input type="text" name="first_name">
  </p>

  <p>
  <label>Surname</label><br>
  <input type="text" name="surname">
  </p>

  <p>
  <label>Email</label><br>
  <input type="email" name="email" required="">
  </p>

  <p>
  <label>Enquiry type:</label><br>
  <label><input checked="checked" name="type" type="radio" value="sales" /> Sales</label> <br />
  <label><input name="type" type="radio" value="support" /> Support</label> <br />
  <label><input name="type" type="radio" value="billing" /> Billing</label>
  </p>

  <p>
  <label>Message</label><br>
  <textarea rows="6"></textarea>
  </p>

  <p>
  <label>
  <input type="checkbox" id="checkbox" value="terms">
  I agree to the <a href="#">terms and conditions</a>
  </label>
  </p>

  <button>Send</button>
  <button type="reset">Reset</button>
  <button disabled="disabled">Disabled</button>
</form>
```

**結果**
![スクリーンショット 2022-02-22 3.09.36.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/d42ec67d-6146-357b-370d-9ea2c1f5ed6d.png)
![スクリーンショット 2022-02-22 3.09.46.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/6280/e740b7c2-616e-fcc7-2e6b-8e581344d427.png)

# 参考サイト
https://simplecss.org/

# 脚注
[^Komesan]:https://komesan.pages.dev/
[^まとも検索]:https://fukuyuki.github.io/mtm.html
