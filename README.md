# VRChat グループバナー プレビュー

VRChat のグループバナー画像が、各 UI（メニュー・ネームプレート・ウェブサイト）でどのように見えるかを**目安として**確認できる非公式ツールです。

画像・入力テキストはすべてブラウザ内でのみ処理され、サーバーには送信・保存されません。

## 使い方

1. 左サイドバーの「バナー画像」にバナー画像（PNG / JPG、16:9 推奨）をクリックまたはドラッグ＆ドロップで読み込む
2. 「表示設定」でグループ名・ユーザー名を入力すると、各プレビューに反映される
3. 必要に応じて以下を切り替える
   - **ネームプレート横幅**: ユーザー名の長さから自動推定。スライダーで手動調整も可能
   - **VRC+**: ON にするとプロフィール画像の丸アイコン付きのネームプレートになる（画像も指定可能）
   - **クイックメニュー展開中**: 通常表示／QM 展開時のどちらのカードを強調するか切り替え

## プレビューできる表示

- **メニュー内**: グループ一覧・グループ詳細・クイックメニュー・エクスプレッションメニュー
- **ネームプレート（ワールド内）**: 通常表示・クイックメニュー展開時・名前の長さ比較
- **ウェブサイト（VRChat Home）**: グループページヘッダー・グループ一覧サムネイル

## ネームプレート表示の仕組み

ネームプレートのクロップ位置は [Gorialis (Devon R) さんの実測ガイド](https://x.com/Gorialis/status/1602801061470912513)、全体のゾーンの考え方は [Reava さんのグループバナーガイド](https://github.com/Reava/Resources/releases/tag/JPGuide)を参考にしています。

![グループバナーガイド](https://github.com/Reava/Resources/releases/download/JPGuide/JP_BannerGuide.png)

- バナーは名前ピルの背後に表示され、ピルの上にはみ出した**横帯だけが見えます**。画像はバナー枠の**幅いっぱい**に表示され、**上下がトリミング**されます
- 表示されるのは画像の上寄り〜中央の帯で、**名前が短いほど上まで広く**（高さの約 17%〜54%）、**長いほど狭く**（約 38%〜54%）見えます
- クイックメニュー展開時は下側も約 64〜71% まで広がり、グループ名とショートコードのピルも上に表示されます
- ページ内の「実機での見え方の例」から、Gorialis さんの実機スクリーンショット集（[assets/gorialis-guide-examples.jpg](assets/gorialis-guide-examples.jpg)）も確認できます

## ローカル実行・デプロイ

静的な HTML のみで動作します。`index.html` をブラウザで開くだけで利用できます。

Cloudflare Workers（静的アセット）へのデプロイ:

```bash
npx wrangler deploy
```

## Submodule（Reava/Resources）

参考資料の元リポジトリ [Reava/Resources](https://github.com/Reava/Resources) を `external/reava-resources` に submodule として追加しています（`JPGuide` タグで固定）。バナー用 PSD テンプレートなどが含まれます。

```bash
git submodule update --init
```

- 約 20MB の PSD を含むため、必要な場合のみ初期化してください
- 本ツールの動作・デプロイには不要です
- ガイド画像（`JP_BannerGuide.png`）はリリース添付ファイルのため submodule のツリーには含まれません。上記リリースページから取得できます

## クレジット・免責事項

- グループバナーガイド: [Reava/Resources](https://github.com/Reava/Resources)（[JPGuide リリース](https://github.com/Reava/Resources/releases/tag/JPGuide)）
- 実測クロップガイド・実機スクリーンショット集: [Devon R (@Gorialis) さんのポスト](https://x.com/Gorialis/status/1602801061470912513)（作者により自由利用が許可されています）
- 本ツールの表示はあくまで目安であり、VRChat の UI 更新やユーザー環境により実際の表示と異なることがあります
- VRChat は VRChat Ltd. の商標です。本ツールは VRChat 公式とは無関係の非公式ツールです
- プライバシーについては [privacy.html](privacy.html) を参照してください
