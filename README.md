# StreamingTool-Splits: RTA区間（.lss）公式リポジトリ

配信・RTA支援ツール「StreamingTool」向けの公式スプリット（`.lss`）配信用リポジトリです。
本リポジトリに `.lss` ファイルを追加すると、StreamingTool のオートスプリッター画面から自動でゲームごとのルール（カテゴリ）一覧が読み込まれ、「プリセット読込」からワンクリックで区間リストを設定できるようになります。

---

## 📁 ディレクトリ構成

```text
├── README.md
├── index.json                    ← 全ゲーム・カテゴリの一覧インデックス
└── splits/
      ├── Super Meat Boy/
      │     ├── Any%.lss
      │     ├── All Light Worlds.lss
      │     └── 106%.lss
      ├── Celeste/
      │     ├── Any%.lss
      │     └── All Chapters.lss
      └── [ゲーム名]/
            └── [ルール名].lss
```

---

## 🚀 新しいゲームやルールの追加方法

### 方法A: Webブラウザ（GitHub画面）から追加する（一番簡単）
1. 本リポジトリの `splits/` フォルダを開きます。
2. 右上の「Add file」>「Create new file」で `[ゲーム名]/[ルール名].lss` と入力し、LiveSplit 等から保存した `.lss` ファイルの中身（XMLテキスト）を貼り付けて保存します。
   - または「Add file」>「Upload files」で `.lss` ファイルをドラッグ＆ドロップします。
3. ルートの `index.json` にそのゲームとカテゴリの情報を追加します（※`index.json` に未記載でも、アプリのフォールバック検索により自動検出されます）。

### 方法B: Git コマンドで追加する
```bash
# クローン
git clone https://github.com/nan222/StreamingTool-Splits.git
cd StreamingTool-Splits

# splits/ 配下にゲーム名フォルダを作成して .lss を配置
mkdir -p "splits/Super Mario 64"
cp ~/Downloads/16_Star.lss "splits/Super Mario 64/16 Star.lss"

# index.json を更新（任意）
# コミット＆プッシュ
git add .
git commit -m "Add Super Mario 64 16 Star splits"
git push origin main
```

---

## ⚡ StreamingTool 側での自動読み込み
1. StreamingTool の「オートスプリッター設定」でゲームを選択。
2. 本リポジトリに存在するカテゴリ（Any% 等）がドロップダウンに自動表示されます。
3. 「プリセット読込」を押すと、本リポジトリから該当の `.lss` がダウンロードされ、一瞬でスプリット設定が完了します。
