# handson-j-heatmap

**GitHub Copilot CLI の使い方を学ぶ**ハンズオンワークショップです。

## 📚 概要

このワークショップでは、**GitHub Copilot CLI を `/plan` から実装まで活用する方法**を、日本地図のヒートマップ可視化を題材として学びます。

**重要：このハンズオンの目的は、ヒートマップの実装方法を学ぶことではなく、GitHub Copilot CLI の効果的な使い方を習得することです。**

ヒートマップ可視化は、Copilot CLI の実践的な使い方を学ぶための題材として選んでいます。`/plan` でタスクを分解し、各ステップで Copilot CLI を活用しながら実装を進めるプロセスを体験します。

## 🎯 学習目標

このハンズオンを通じて、以下のスキルを習得できます：

### 主目標：GitHub Copilot CLI の習得

1. **`/plan` コマンドの活用** - プロジェクトをタスクに分解する方法
2. **適切なプロンプティング** - Copilot CLI に指示を出して望む実装を得る方法
3. **生成されたコードの評価と改善** - AIが生成したコードをレビュー・改良する能力
4. **Copilot CLI のワークフロー** - 計画 → 実装 → テスト → 改善のサイクルを回す方法
5. **効率的な開発プロセス** - AIを活用した実装スピードの向上

### 副次的な習得内容（題材として）

- D3.jsによるデータビジュアライゼーション
- GeoJSONを使った地図描画
- JSONデータの読み込みと処理
- SVGの基本操作

## 🛠️ 使用技術

### 開発ツール

- **GitHub Copilot CLI** - AIによるコード生成支援ツール（必須）

### ライブラリ・技術

- **D3.js v7** - データビジュアライゼーションライブラリ
- **GeoJSON** - 日本地図の地理データ形式
- **Vanilla JavaScript** - フレームワークを使わないピュアなJavaScript
- **SVG** - スケーラブルベクターグラフィックス
- **HTML5/CSS3** - 標準的なWeb技術

## 📁 プロジェクト構成

```
handson-j-heatmap/
├── README.md             # このファイル
├── index.html            # 【課題】あなたが作成するファイル
├── data/
│   └── population.json   # 都道府県別人口データ（1970-2023年）
└── src/                  # 補助リソース（必要に応じて使用）
```

## 🚀 始め方

### 1. 環境準備

#### 必須ツール

**GitHub Copilot CLI のインストール**

このハンズオンでは GitHub Copilot CLI を使用してコードを生成します。事前にインストールしてください：

```bash
# GitHub CLI がインストール済みの場合
gh extension install github/gh-copilot

# または、GitHub CLI のインストールから
# https://cli.github.com/
```

使い方の確認：
```bash
# コード生成の例
gh copilot suggest "D3.jsでJSONファイルを読み込むコード"

# シェルコマンドの提案
gh copilot explain "このコマンドの説明を教えて"
```

詳しい使い方は [GitHub Copilot CLI ドキュメント](https://docs.github.com/en/copilot/github-copilot-in-the-cli) を参照してください。

#### その他のツール

- モダンなWebブラウザ（Chrome、Firefox、Safari、Edgeなど）
- テキストエディタ（VS Code推奨）

### 2. index.htmlを作成

**ここからが本番です！GitHub Copilot CLI を使って実装していきます。**

まず、プロジェクト全体を計画します：
```bash
gh copilot suggest "このプロジェクトでindex.htmlを作成するための実装計画を立てて"
```

または、より具体的に：
```bash
# /planコマンド相当の指示
gh copilot suggest "D3.jsで日本のヒートマップを作るindex.htmlの実装を、以下の機能ごとに分解して計画を立てて：
1. 基本HTML構造
2. 地図の描画
3. 人口データの読み込みと色分け
4. 年代選択UI"
```

### 3. 動作確認

- 基本版: 作成した `index.html` をダブルクリックしてブラウザで開きます。
- 拡張版: 新規追加した `index-advanced.html` も同様にダブルクリックで開けます（ローカルサーバー不要）。

#### 拡張版UIのポイント

- タブで表示を切り替えできます（例: 人口 / 男女比）。
- 「男女比」タブは `data/gender-ratio.json` がある場合に拡張可能な設計です。
- 対応データがない場合は「データ未提供」と表示されます。

## 📝 課題：何を作るか

**繰り返しますが、ゴールは「ヒートマップを完成させること」ではなく「Copilot CLI を使いこなせるようになること」です。**

題材として、以下の機能を持つヒートマップ可視化ページを Copilot CLI を使って作成します：

### 必須機能

1. **日本地図の表示**
   - GeoJSONデータから日本の都道府県地図を描画
   - SVG形式で表示

2. **人口データの可視化**
   - `data/population.json` から人口データを読み込み
   - 人口の多さに応じて都道府県を色分け
   - カラースケールを使用（例：人口が多いほど濃い色）

3. **年代選択機能**
   - 1970年〜2023年の国勢調査データを切り替え表示
   - ドロップダウンまたはその他のUI要素で選択可能

### 推奨機能（チャレンジ）

- 都道府県にマウスオーバーで詳細情報を表示（ツールチップ）
- 凡例の表示（色と人口の対応）
- レスポンシブデザイン

## 📊 データ構造

### population.json

都道府県別の人口データ（1970-2023年の国勢調査データ）

```json
{
  "2023": [
    {
      "id": "01",
      "name": "北海道",
      "population": 5140000
    },
    {
      "id": "13",
      "name": "東京都",
      "population": 14047000
    }
    // ... 47都道府県分
  ],
  "2020": [ /* ... */ ],
  // ... 各年代のデータ
}
```

- **year** (キー): 国勢調査の年（文字列）
- **id**: 都道府県コード（2桁、01-47）
- **name**: 都道府県名
- **population**: 人口（人）

データソース: [e-Stat 政府統計の総合窓口](https://www.e-stat.go.jp/) - 国勢調査

### GeoJSON（日本地図）

日本の都道府県境界データ。CDNから読み込むことを推奨：

```
https://raw.githubusercontent.com/dataofjapan/land/master/japan.geojson
```

## 💡 実装のヒント

### D3.jsの読み込み

CDNから最新のD3.js v7を読み込みます：

```html
<script src="https://d3js.org/d3.v7.min.js"></script>
```

### データの読み込み

```javascript
// JSONデータの読み込み（Promiseを返す）
d3.json("data/population.json").then(data => {
  // dataを使った処理
});
```

### カラースケールの作成

```javascript
// 人口数に応じた色スケールを作成
const colorScale = d3.scaleLinear()
  .domain([最小値, 最大値])
  .range(["薄い色", "濃い色"]);
```

### 地図の描画

```javascript
// GeoJSONから地図パスを生成
const path = d3.geoPath();

svg.selectAll("path")
  .data(geojson.features)
  .enter()
  .append("path")
  .attr("d", path);
```

## 🔍 参考リソース

### 公式ドキュメント

- [D3.js 公式サイト](https://d3js.org/)
- [D3.js API リファレンス](https://github.com/d3/d3/blob/main/API.md)

### 参考になる機能

- `d3.json()` - JSONファイルの読み込み
- `d3.select()` / `d3.selectAll()` - 要素の選択
- `d3.scaleLinear()` - 線形スケールの作成
- `d3.geoPath()` - 地理データからSVGパスを生成
- `d3.extent()` / `d3.min()` / `d3.max()` - データの範囲を取得

### GeoJSON関連

- [GeoJSON 仕様](https://geojson.org/)
- [日本の地理データ (dataofjapan/land)](https://github.com/dataofjapan/land)

## 🎓 ワークショップの進め方

**このワークショップの核心：GitHub Copilot CLI の使い方を体得する**

### 基本的なワークフロー

1. **プロジェクト全体を計画する (`/plan` 相当)**
   - 何を作るか明確にする
   - タスクを分解する
   - 実装順序を決める

2. **各タスクで Copilot CLI を活用**
   - 自然言語で指示を出す
   - 生成されたコードを確認・理解する
   - 必要に応じて改善を指示する

3. **動作確認とフィードバック**
   - ブラウザで確認
   - 問題があれば Copilot CLI に改善を依頼

4. **次のタスクへ**
   - 小さく作って確認、を繰り返す

### ステップバイステップガイド

#### フェーズ0: プロジェクト計画

**最初に `/plan` 的な使い方で全体を把握**

```bash
gh copilot suggest "D3.jsで日本の都道府県別人口データのヒートマップを作りたい。data/population.jsonにデータがある。実装手順を段階的に教えて"
```

Copilot CLI が提案する計画をもとに、実装を進めていきます。

#### フェーズ1: HTML基本構造

Copilot CLI に聞いてみましょう：
```bash
gh copilot suggest "D3.jsを使ったHTMLファイルの基本構造を作成して"
```

実装する内容：
- DOCTYPE、head、bodyの設定
- D3.js v7のCDN読み込み
- SVG要素を配置する領域

#### フェーズ2: 地図の描画

```bash
gh copilot suggest "D3.jsで日本のGeoJSONデータを読み込んで地図を表示するコード"
```

実装する内容：
- GeoJSONデータの読み込み
- SVGパスの生成と描画
- 地図のスケーリングと配置

#### フェーズ3: 人口データの読み込みと可視化

```bash
gh copilot suggest "JSONファイルから人口データを読み込んで、都道府県ごとに色分けするD3.jsコード"
```

実装する内容：
- `data/population.json`の読み込み
- カラースケールの作成
- データと地図の紐付け
- 色の適用

#### フェーズ4: インタラクティブ機能

```bash
gh copilot suggest "年代を選択するドロップダウンメニューを追加して、選択された年のデータで地図を更新するコード"
```

実装する内容：
- 年代選択のUI要素
- イベントハンドラの設定
- データ更新処理

### 💡 Copilot CLI 活用のコツ

#### 1. 計画から始める

いきなり実装せず、まず全体像を把握：
```bash
gh copilot suggest "このタスクを実装するための手順を教えて"
```

#### 2. 具体的に指示する
   - ❌ 「地図を描いて」
   - ✅ 「D3.jsでGeoJSONから日本地図をSVGで描画して、幅800px、高さ600pxで」

#### 3. 段階的に進める
   - 一度に全部実装しようとせず、機能ごとに分けて指示
   - 小さく作って動作確認してから次へ

#### 4. 生成されたコードを理解する
   - コピペで終わらせない
   - わからない部分は `gh copilot explain` で説明を聞く

#### 5. 改善を繰り返す
   - 「このコードをもっと効率的にして」
   - 「エラーハンドリングを追加して」
   - 「コメントを追加して」

## ⚠️ よくある問題と解決方法

### データが読み込めない

- ファイルパスを確認：`data/population.json` が正しいか
- ブラウザのデベロッパーツール（F12）のコンソールでエラーを確認

### 地図が表示されない

- SVGの幅・高さが設定されているか確認
- GeoJSONのURLが正しいか確認
- `d3.geoPath()` を使用しているか確認

### 色が正しく表示されない

- カラースケールのドメイン（範囲）が正しく設定されているか
- データとGeoJSONの都道府県IDが一致しているか（ゼロ埋めの確認）

## 📞 サポート

わからないことがあれば：

1. **GitHub Copilot CLI に聞く** - `gh copilot explain` でコードの説明を聞ける
2. **ブラウザの開発者ツールを確認** - コンソールにエラーメッセージが表示されます
3. **データ構造を確認** - `console.log()` でデータの中身を出力
4. **公式ドキュメントを参照** - D3.jsの公式APIリファレンスが充実しています

## 📄 ライセンス

このハンズオン教材は自由に使用できます。

---

**GitHub Copilot CLI と一緒に楽しくデータビジュアライゼーションを学びましょう！ 🤖🗾📊**
