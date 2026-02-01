# LinuC 101 1.02：Linuxのインストールとパッケージ管理のコマンドまとめ

■1. Debianパッケージ管理 (Debian, Ubuntuなど)

### apt-get
```bash
# パッケージのインストール、更新、削除を行う
# apt-get [サブコマンド] {パッケージ名}
sudo apt-get update
sudo apt-get install vim
# (備考) updateはパッケージリストの更新、installは導入
```

### apt-cache
```bash
# パッケージ情報の検索を行う
# apt-cache [サブコマンド] {キーワード}
apt-cache search webserver
# (備考) インストール前にパッケージを探す際に使用
```

### dpkg
```bash
# .debファイルを直接操作する（低レベルツール）
# dpkg [オプション] {ファイル名/パッケージ名}
dpkg -i package.deb
dpkg -l
# (備考) -iはインストール、-lはインストール済み一覧表示
```


■2. Red Hatパッケージ管理 (AlmaLinux, CentOS, Fedoraなど)

### dnf (yum)
```bash
# パッケージのインストール、更新、削除を行う
# dnf [サブコマンド] {パッケージ名}
sudo dnf install httpd
sudo dnf check-update
# (備考) yumの後継。LinuCではdnf/yum両方の理解が必要
```

### rpm
```bash
# .rpmファイルを直接操作する（低レベルツール）
# rpm [オプション] {ファイル名/パッケージ名}
rpm -ivh package.rpm
rpm -qa
# (備考) -i:install, -v:verbose, -h:hash(進行状況), -qa:全表示
```


■3. 共有ライブラリの管理

### ldd
```bash
# プログラムが必要としている共有ライブラリを表示する
# ldd {実行ファイルパス}
ldd /bin/ls
# (備考) 依存している .so ファイルのパスを確認できる
```

### ldconfig
```bash
# 共有ライブラリのキャッシュを更新する
# ldconfig
sudo ldconfig
# (備考) /etc/ld.so.conf 等を編集した後に実行が必要
```


■4. ブートローダ

### grub-install
```bash
# GRUBブートローダをデバイスにインストールする
# grub-install {デバイス名}
sudo grub-install /dev/sda
# (備考) BIOS/UEFI環境によって挙動が異なる
```

### grub-mkconfig
```bash
# GRUBの設定ファイル(grub.cfg)を生成する
# grub-mkconfig -o {出力先パス}
sudo grub-mkconfig -o /boot/grub/grub.cfg
# (備考) /etc/default/grub の変更を反映させる際に使用
```
