# Google Search Console 登録手順書

> 第八終活リーガルクリニック（directfuneral.github.io/dai8legalclinic）をGoogle検索に表示させるための設定手順

---

## 全体の流れ

```
①Search ConsoleでURLを登録
    ↓
②所有権の確認（metaタグをHTMLに追記）
    ↓
③GitHubにアップロード・確認ボタンを押す
    ↓
④サイトマップを送信
    ↓
⑤完了（数日〜1週間でGoogle検索に表示）
```

---

## STEP 1｜Search Consoleにアクセスしてサイトを追加

1. **[Google Search Console](https://search.google.com/search-console/)** を開く
2. Googleアカウントでログイン
3. 「**プロパティを追加**」をクリック
4. プロパティタイプの選択画面で **「URLプレフィックス」** を選ぶ
5. URLを入力する

   ```
   https://directfuneral.github.io/dai8legalclinic/
   ```
   ※ 末尾のスラッシュまで含めて正確に入力してください

6. 「続行」をクリック

---

## STEP 2｜所有権の確認方法を選ぶ

確認方法の一覧が表示されます。  
**「HTMLタグ」** を選んでください（index.htmlを直接編集できるため最も簡単です）。

```
「その他の確認方法」→「HTMLタグ」をクリック
```

以下のようなmetaタグが表示されます（内容は毎回異なります）：

```html
<meta name="google-site-verification" content="ここにあなた専用のコードが表示されます" />
```

**このタグをコピーしてください。**  
（まだ「確認」ボタンは押さないでください）

---

## STEP 3｜index.html にmetaタグを追加する

`index.html` を開いてテキストエディタで編集します。

### ファイル内の変更箇所

`<head>` タグの中（`<style>` タグの直前）に、コピーしたmetaタグを貼り付けます。

**変更前：**
```html
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>第八終活リーガルクリニック</title>
<style>
```

**変更後：**
```html
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>第八終活リーガルクリニック</title>
<meta name="google-site-verification" content="★ここにコピーしたコードを貼り付け★" />
<style>
```

---

## STEP 4｜GitHubにアップロードする

編集した `index.html` をGitHubのリポジトリに上書きアップロードします。

### GitHub上での操作手順

1. GitHub でリポジトリを開く
2. `index.html` をクリック
3. 右上の鉛筆アイコン（Edit）をクリック  
   **または** `index.html` をドラッグ＆ドロップで上書きアップロード
4. 「Commit changes」をクリックして保存

### アップロード完了の確認

ブラウザで以下のURLを開いてページが表示されることを確認：
```
https://directfuneral.github.io/dai8legalclinic/
```

---

## STEP 5｜Search Consoleで「確認」ボタンを押す

1. Search Consoleの画面に戻る
2. 「**確認**」ボタンをクリック
3. 「所有権を確認しました」と表示されれば登録完了

> ⚠️ エラーが出る場合：GitHubへのアップロード後、反映まで数分かかることがあります。  
> 2〜3分待ってから再度「確認」ボタンを押してください。

---

## STEP 6｜サイトマップを送信する

所有権の確認後、サイトマップを登録するとGoogleのクロールが効率的になります。

1. Search Consoleの左メニューから「**インデックス作成 → サイトマップ**」を開く
2. 「新しいサイトマップの追加」欄に以下を入力：

   ```
   sitemap.xml
   ```

3. 「**送信**」をクリック
4. ステータスが「成功しました」になれば完了

---

## STEP 7｜完了・確認

登録完了後、以下の状態になるまで数日〜1週間ほど待ちます。

| 確認方法 | 内容 |
|---|---|
| Google検索 | `site:directfuneral.github.io/dai8legalclinic` で検索してページが表示されるか確認 |
| Search Console | 「カバレッジ」でページがインデックスされているか確認 |

---

## トラブルシューティング

### 「確認できませんでした」と表示される場合

- metaタグが `<head>` タグ内に正しく貼り付けられているか確認
- GitHubへのアップロードが完了しているか確認（デプロイに数分かかる）
- ブラウザのシークレットウィンドウで `https://directfuneral.github.io/dai8legalclinic/` を開き、ページのソースコードにmetaタグが含まれているか確認

### ページがなかなかインデックスされない場合

Search Consoleの「URL検査」ツールで `https://directfuneral.github.io/dai8legalclinic/` を入力し、  
「**インデックス登録をリクエスト**」をクリックすると登録を促すことができます。

---

## 今回のリポジトリに含まれているSEO関連ファイル

| ファイル | 役割 |
|---|---|
| `index.html` | アプリ本体（metaタグ追加後にアップロード） |
| `sitemap.xml` | サイトの構成をGoogleに伝えるファイル |
| `robots.txt` | 検索エンジンへのクロール許可設定 |

---

*設定完了後、Google検索で「第八終活リーガルクリニック」などのキーワードで表示されるようになります。*  
*表示順位の改善はSEO対策（タイトル・説明文の最適化など）により向上させることができます。*
