# 命名規則

## 共通

- **半角英数字・`_`・`-` だけ**を使う（日本語・全角・スペースは使わない）
  - 日本語ファイル名はOSや環境によって文字化けし、コマンドでも扱いにくい
- 小文字の `snake_case` を基本にする：`drive_unit`, `upper_frame`
- 名前を見れば **何の・どこの部品か** が分かるようにする
- ❌ `Part1`, `新しいフォルダー`, `WORK`, `test2`, `hako`
- ❌ `xxx_ver1`, `xxx_final`, `xxx_final2` ← バージョンはGitで管理

## ローマ字か英語か

チームでどちらかに統一すること。混ぜると検索できません。

| 英語 | ローマ字（統一するなら） |
|---|---|
| `drive` | `ashimawari` |
| `upper` | `uwamono` |
| `communication` | `tsushin` |

## firmware

- Arduinoはスケッチのフォルダ名と `.ino` ファイル名を一致させる必要がある
  - `drive/drive.ino`, `upper/upper.ino`
- 機能ごとにファイルを分ける：`<機能>.cpp` + `<機能>.h`
- 拡張子は `.h` か `.hpp` のどちらかに統一

## CAD

- `<ユニット>_<部品名>` ：`drive_motor_mount`, `upper_arm_base`
- アセンブリは `asm_` を先頭に：`asm_robot`, `asm_drive_unit`
- 市販品は型番をそのまま使ってよい（`purchased/` に入れる）
- 出力ファイル（STL等）は元のCADファイルと同じ名前にする

## PCB

- `<役割>_board` ：`main_board`, `power_board`
- 基板のバージョンはファイル名ではなく **Gitのタグ** で：`pcb-v1`, `pcb-v2`

## experiments

- `YYYYMMDD_<内容>_<名前>` ：`20251101_motor_driver_test_tanaka`
- 日付を先頭にすると時系列順に並ぶ

## ブランチ

- `feature/<内容>`, `fix/<内容>`, `exp/<内容>`
- 内容は英小文字とハイフン：`feature/drive-control`
