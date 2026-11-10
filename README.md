# ロボコン Git テンプレート

先輩チーム（Sugano Robocon 2024 A班）のGitHub organizationでの経験をもとに、
**「Gitをこう使うと後で困らない」** という型だけを示すテンプレートです。

> ⚠️ このテンプレートには **写真・CAD・コード・ピン配置などの設計情報は一切含まれていません**。
> 入っているのはディレクトリ構造と、各ファイルに「何を書くか」の説明だけです。
> 機構・回路・制御は自分たちで考えてください。

---

## 全体像：organization に作るリポジトリは5つだけ

```
<your-organization>/            ← GitHub organization（チームで1つ作る）
├── .github/        … organizationのトップページ＋全リポ共通のIssue/PRテンプレート
├── firmware/       … 本番で使う制御コード（1リポにまとめる）
├── experiments/    … 動作確認・お試しコード（1リポにまとめる）
├── pcb/            … 基板データ（KiCadなど）
└── cad/            … 機構設計データ（SolidWorksなど）
```

`repos/` 以下に、それぞれのリポジトリの中身の雛形が入っています。

```
repos/
├── .github/
│   ├── profile/README.md          ← organizationトップに表示される（チーム紹介・組織図・カレンダー）
│   ├── ISSUE_TEMPLATE/            ← 全リポジトリ共通のIssueテンプレート
│   └── PULL_REQUEST_TEMPLATE.md   ← 全リポジトリ共通のPRテンプレート
│
├── firmware/
│   ├── README.md                  ← 使用マイコン・ライブラリのバージョン・書き込み手順
│   ├── .gitignore
│   ├── LICENSE
│   ├── drive/                     ← 足回り用マイコンのスケッチ
│   ├── upper/                     ← 上物用マイコンのスケッチ
│   ├── common/                    ← 複数マイコンで共有する定義（通信の取り決めなど）
│   └── docs/                      ← ピン配置表・システム図
│
├── experiments/
│   ├── README.md                  ← 実験一覧（どれが何を確かめたか）
│   └── YYYYMMDD_topic_name/       ← 1実験 = 1フォルダ
│
├── pcb/
│   ├── README.md                  ← 基板のバージョン履歴・発注方法
│   ├── .gitignore                 ← KiCadのバックアップ・ロックファイルを除外
│   ├── main_board/                ← KiCadプロジェクト一式
│   │   └── production/            ← 発注用データ（最終版だけ）
│   └── images/                    ← README用のスクショ
│
└── cad/
    ├── README.md                  ← どのファイルを開けば全体が見えるか
    ├── .gitignore                 ← SolidWorksの一時ファイル(~$)を除外
    ├── .gitattributes             ← バイナリ扱い・Git LFS設定
    ├── assembly/                  ← 全体アセンブリ
    ├── parts/{drive,upper,frame}/ ← 自作部品（ユニットごと）
    ├── purchased/                 ← 市販品のモデル（ネジ・ベアリング・モータ等）
    ├── export/{stl,step,dxf}/     ← 3Dプリント・加工用の出力ファイル
    ├── drawings/                  ← 図面
    └── images/                    ← README用のスクショ
```

## まず読むもの

| ドキュメント | 内容 |
|---|---|
| [docs/git_guide.md](docs/git_guide.md) | Gitの使い方ルール（ブランチ・コミット・PR）。**全員必読** |
| [docs/repository_design.md](docs/repository_design.md) | なぜこの5リポ構成なのか（先輩チームの反省点） |
| [docs/naming_rules.md](docs/naming_rules.md) | ファイル・フォルダ・ブランチの命名規則 |

## 使い方

1. GitHubで organization を作る（チーム名など）
2. `repos/` 以下のフォルダごとに、同じ名前のリポジトリを organization 内に作る
   - `.github` だけは **リポジトリ名を `.github` にする**（organizationトップページになる）
3. 各フォルダの中身をコピーして最初のコミットをする
   ```bash
   cd repos/firmware
   git init
   git add .
   git commit -m "init: テンプレートから作成"
   git branch -M main
   git remote add origin https://github.com/<your-organization>/firmware.git
   git push -u origin main
   ```
4. `<...>` で囲まれた部分を自分たちの情報に書き換える
5. `.gitkeep` はフォルダを残すための空ファイル。中にファイルが入ったら消してOK
# enpra_robocon_template
