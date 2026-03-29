<div align="center">
    <p>
        <img src="figures/banner-draw.png">
    </p>

[![Licence](https://img.shields.io/pypi/l/ultralytics)](https://github.com/HichTala/draw2/blob/main/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/HichTala/draw2?logoColor=%23181717)](https://github.com/HichTala/draw2)
[![Twitter](https://img.shields.io/badge/-twitter-000?logo=x&labelColor=555)](https://twitter.com/hichtala)
[![HuggingFace Downloads](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fhuggingface.co%2Fapi%2Fmodels%2FHichTala%2Fdraw2&query=%24.downloads&logo=huggingface&label=downloads&color=%23FFD21E)](https://huggingface.co/HichTala/draw2)
[![Plugin](https://img.shields.io/badge/-plugin_for_obs-302E31?logo=obsstudio&labelColor=555&color=%23302E31)](https://github.com/HichTala/draw2-plugin)
[![WandB](https://img.shields.io/badge/visualize_in-W%26B-yellow?logo=weightsandbiases&color=%23FFBE00)](https://wandb.ai/hich_/draw)
[![Medium](https://img.shields.io/badge/-Medium-12100E?style=flat&logo=medium&labelColor=555)](https://medium.com/@hich.tala.phd/how-i-trained-again-my-model-to-detect-and-recognise-a-wide-range-of-yu-gi-oh-cards-5c567a320b0a)

[🇫🇷 Français](https://github.com/HichTala/draw2/blob/main/README_fr.md)

</div>

遊戯王のカードを画像やデュエル映像から自動で見つけて認識するAIツールです。前のバージョンから精度や安定性、使いやすさを大幅にパワーアップさせました！さらに、OBSプラグインにも対応しているので、プログラミングの知識がなくても簡単にライブ配信や動画編集に組み込むことができます。
リアルタイムでカードを検出して画面に表示することも可能です。

（OBS Studio用のサードパーティプラグインで、OBSプロジェクトとは関係ありません）

似たようなプロジェクトもありますが（[関連プロジェクト](#-関連するプロジェクト)を参照）、デュエル中のカードをリアルタイムで認識できるのはDRAW 2だけです。

このプロジェクトは[GNU AGPL v3.0](https://github.com/HichTala/draw2/blob/main/LICENCE)ライセンスで公開されています。
皆さんのアイデアやフィードバックをお待ちしています！

---

## 📄 ドキュメント

**プラグインだけ使いたい方**
→ [プラグインページ](https://github.com/HichTala/draw2-plugin)を参照ください。このリポジトリからのインストールは必要ありません。

**開発者向け：OBS以外で検出器を使う方法**
以下の手順でセットアップできます。Pythonの基本知識が必要です。

### 🛠️ インストール

1. Pythonをインストールしてください（[公式サイト](https://www.python.org/)を参照）
2. パッケージ管理には[miniconda](https://docs.conda.io/projects/miniconda/en/latest/)を推奨します（[ドキュメント](https://docs.conda.io/projects/miniconda/en/latest/)を参照）
3. リポジトリをクローンして必要なパッケージをインストール

```bash
git clone https://github.com/HichTala/draw2
cd draw2
python -m pip install .
```

クローンせずに直接インストールする場合

```bash
python -m pip install git+https://github.com/HichTala/draw2.git
```

### 🚀 使い方

インストール後、次のコマンドで起動できます

```bash
python -m draw
```

主なオプション

| オプション | 説明 | 初期設定 |
|---|---|---|
| `--source` | 入力元（画像/動画/カメラ番号） | 0（カメラ） |
| `--save` | 出力ファイルの保存先 | 未設定 |
| `--save-images` | 検出されたカード画像を保存 | オフ |
| `--show` | 結果をウィンドウに表示 | オフ |
| `--display-card` | 検出カードを画面に表示 | オフ |
| `--deck-list` | 認識精度向上用のデッキリストファイル（.ydk） | 未設定 |
| `--fps` | 動画保存時のFPS | 60 |

全てのオプションは `python -m draw --help` で確認できます。

---

## 💡 開発の経緯

このプロジェクトは、[SuperZouloux](https://www.youtube.com/watch?v=64-LfbggqKI)さんが考案した「ホログラムで遊戯王カードを再現」という面白いアイデアからヒントを得て開発しました。元の方法ではカードスリーブにチップを埋め込んでプレイマットで読み取る必要があり、手間がかかる上に伏せカードと表カードの区別ができないという問題がありました。DRAW 2はこれらの問題を解決し、デュエル中にリアルタイムでカードを認識できるようになりました。

著作権を尊重しつつ、*KONAMI* ® とは公式な連携はしていませんが、ライブ配信などで視聴者にカード情報を表示するツールとして、多くのコンテンツクリエイターに役立っています。

---

## 🔗 関連するプロジェクト

| プロジェクト名 | 特長 | 制限事項 |
|---|---|---|
| [遊戯王 NEURON](https://www.konami.com/games/eu/fr/products/yugioh_neuron/) | コナミ公式アプリ。最大20枚同時認識 | 画質に敏感。デュエル中には不向き |
| [yugioh one shot learning](https://github.com/vanstorm9/yugioh-one-shot-learning) | 高精度なカード分類が可能 | 低解像度に弱い。位置検出不可 |
| [Yolov11](https://github.com/ultralytics/ultralytics) | 最新の物体検出モデル | 遊戯王専用ではない |
| [ViT](https://arxiv.org/pdf/2010.11929.pdf) | 13,000枚以上のカードに対応 | 位置検出機能なし |
| [SpellTable](https://spelltable.wizards.com/) | Magic: The Gathering用遠隔プレイアプリ | 遊戯王非対応 |

---

## 🔍 技術的な詳細

データ収集から実際の認識までのプロセスについては、[Mediumの記事](https://medium.com/@hich.tala.phd/how-i-trained-again-my-model-to-detect-and-recognise-a-wide-range-of-yu-gi-oh-cards-5c567a320b0a)で詳しく解説しています。アルゴリズムや数学的な背景についても説明しています。質問があれば気軽にIssueを立ててください。

---

## 💬 連絡先

- Twitter: [@hichtala](https://twitter.com/hichtala)
- メール: [hich.tala.phd@gmail.com](mailto:hich.tala.phd@gmail.com)

質問やアイデアがあれば、IssueまたはSNSまでお気軽にご連絡ください！
