# typst管理するくん
自分の学校とかその他もろもろでtypstの練習で書いたものを保存するRepo

## Environment Setup
必要なパッケージ
- `dialog`
- `typst-cli`
    - `cargo install typst-cli`のみ動作確認済み

1. レポジトリをクローン
```sh
gh repo clone raiga0310/archive-typ
```
2. [オライリー風テンプレート](https://github.com/shun-shobon/typst-oreilly-template)を適当なディレクトリにClone
```sh
# 中身のbook.typのシンボリックリンクを後で生成するのでクローンするディレクトリは気にしなくて良い
gh repo clone shun-shobon/typst-oreilly-template
```
3. 以下のコマンドを実行
```sh
cd /path/to/archive-typ
chmod +x new-typ
# ローカルユーザーのbin（推奨）
mkdir -p ~/.local/bin
ln -s "$(pwd)/new-typ" ~/.local/bin/new-typ

# ~/.local/bin がPATHに含まれていない場合は追加
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## help message
```
使い方: new-typ [オプション]
オプション:
  -p, --project 名前    プロジェクト名を指定
  -t, --template ファイル名  使用するテンプレートファイルを指定
  -h, --help           このヘルプを表示
```

## Trouble Shooting
`typst-cli`のインストール時にOpenSSL関連のエラーが出る場合があります。
```
OpenSSL include directory does not exist: /usr/lib/x86_64-linux-gnu/include
```

以下のようにインストールを試してください
```sh
# Debian/Ubuntu
sudo apt-get install libssl-dev

# Fedora/RHEL/CentOS
sudo dnf install openssl-devel
```
インストールされた後、`typst-cli`のインストールを以下のコマンドで実行してください。
```sh
export OPENSSL_LIB_DIR=/usr/lib/x86_64-linux-gnu
export OPENSSL_INCLUDE_DIR=/usr/include/openssl
cargo install typst-cli
```

## Licence
このプロジェクトはMITライセンスの下で公開されています。

### 使用している外部プロジェクト
- [shun-shobon/typst-oreilly-template](https://github.com/shun-shobon/typst-oreilly-template) - MITライセンス

このプロジェクトはMITライセンスの下で提供されている[shun-shobon/typst-oreilly-template](https://github.com/shun-shobon/typst-oreilly-template)を利用しています。詳細は各リポジトリのLICENSEファイルをご確認ください。