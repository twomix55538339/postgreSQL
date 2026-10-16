# コマンドプロンプトでDB接続

## ローカル環境のデフォルト設定（ユーザー名: `postgres`、データベース名: `postgres`）に接続する場合：

```
psql -U postgres -d postgres
```

## リモートサーバーやポート番号を指定する場合

```
psql -h localhost -p 5432 -U postgres -d postgres
```

「'psql' は内部コマンドまたは外部コマンド...として認識されていません」と出る場合、環境変数 PATH に追加する。

## フルパスで直接実行する（手動で即座に繋ぐ場合）

```
"C:\\Program Files\\PostgreSQL\\16\\bin\\psql.exe" -U postgres -d postgres
```

# 切断・終了方法

```
\\q
```

# データベース接続切り替え

```
database1=# \c database2
```

# コマンド一覧

# PostgreSQL psql メタコマンド一覧

psql には `\i` 以外にも便利な「メタコマンド」がたくさんあります。

メタコマンドはすべて **バックスラッシュ (`\`) で始まる** のが特徴です。

## よく使うメタコマンド

| コマンド | 説明 |
|----------|------|
| `\?` | メタコマンド一覧を表示 |
| `\h` | SQLコマンドのヘルプ |
| `\q` | psql終了 |
| `\l` | データベース一覧 |
| `\c DB名` | データベース接続切替 |
| `\conninfo` | 接続情報表示 |
| `\dt` | テーブル一覧 |
| `\dv` | ビュー一覧 |
| `\df` | 関数一覧 |
| `\dn` | スキーマ一覧 |
| `\d テーブル名` | テーブル定義表示 |
| `\d+ テーブル名` | 詳細なテーブル定義表示 |
| `\i ファイル名` | SQLファイル実行 |
| `\o ファイル名` | 実行結果をファイル出力 |
| `\timing` | 実行時間の表示 ON/OFF |
| `\x` | 縦表示 ON/OFF |
| `\pwd` or `\! cd` | 現在の作業ディレクトリ表示 |
| `\!` | OSコマンド実行 |

---

## テーブル一覧を確認

```sql
database1=# \dt
```

実行例

```text
List of relations
 Schema |  Name   | Type  |  Owner
--------+---------+-------+----------
 public | Table1 | table | postgres
 public | Table2 | table | postgres
```

---

## テーブル定義を確認

```sql
database1=# \d "Table2"
```

---

## SQLファイルを実行

```sql
database1=# \i insert_Table2.sql
```

別フォルダにある場合

```sql
database1=# \i C:/work/sql/insert_Table2.sql
```

---

## 接続先を確認

```sql
database1=# \conninfo
```

実行例

```text
You are connected to database "database1"
as user "postgres"
```

---

## データベースを切り替え

```sql
database1=# \c postgres
```

切替後

```text
postgres=#
```

---

## Windowsコマンドを実行

現在のフォルダを確認

```sql
database1=# \! cd
```

ファイル一覧を表示

```sql
database1=# \! dir
```

---

## 現在の作業ディレクトリを確認

```sql
database1=# \pwd
```

---

## PostgreSQL学習時によく使うコマンド ベスト5

```sql
\dt
\d "Table2"
\conninfo
\i ファイル名.sql
\q
```

この5つだけでも以下の作業ができます。

- テーブル一覧確認
- テーブル定義確認
- 接続先確認
- SQLファイル実行
- psql終了

