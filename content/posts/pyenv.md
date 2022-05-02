---
title: "Pyenv"
date: 2022-04-27T09:21:58+09:00
draft: false 
---

[参考](https://qiita.com/suisuina/items/02644576ab4d048ffa5e)  
[参考](https://qiita.com/acecrc/items/bb133abfca07a3a7a9c4)
### 現在のバージョン確認
```
pyenv version
```
### インストール済みのバージョンを表示 
```
pyenv versions
```
### インストール可能な一覧の表示 
```
pyenv install -l
```
### ローカル環境に適用 
```
pyenv local [version]
```
### グローバル環境に適用 
```
pyenv global [version]
```
### hogeという名前で開発環境を作成 
```
python -m venv hoge
```
### hogeをアクティブにする 
```
source hobe/bin/activate
```
### アクティブになっている開発環境を修了する
```
deactivate
```