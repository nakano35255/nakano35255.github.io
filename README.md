# The URL of my website

https://nakano35255.github.io


## M1 Mac での開発環境構築

M1 Mac で Jekyll を実行するには、以下の手順に従ってください。

1. プロジェクトの依存関係をインストール

```sh
bundle install
```

2. 古いffi gem をアンインストール

```sh
sudo gem uninstall ffi
```

3. ffi gem を再インストール

```sh
sudo arch -x86_64 gem install ffi
```

4. Jekyll サーバーを起動

```sh
bundle exec jekyll serve
```