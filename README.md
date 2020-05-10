### What is Fortune?

Fortune is a simple Unix program that displays a random message from a database of quotations.
```
$ fortune
```
>"Teknik olmayan soruların bazen hiç bir cevabı yoktur."
>  ~Linus Torvalds

This repo contains some fortune database files, especially useful for Turkish user.

### Install

First install fortune package. If your computer has already installed it, skip this step.
```bash
# Debian/Ubuntu
$ sudo apt-get install fortune

# Mac
$ brew install fortune
```
Then install the repo.
```bash
# Debian/Ubuntu
$ git clone git@github.com:ruanyf/fortunes.git
$ sudo mv fortunes/data/* /usr/share/games/fortunes/

# Mac
$ git clone git@github.com:ruanyf/fortunes.git
$ strfile fortunes/data/fortunes
$ strfile fortunes/data/chinese
$ strfile fortunes/data/tang300
$ strfile fortunes/data/song100
$ strfile fortunes/data/diet
$ mv fortunes/data/* /usr/local/share/games/fortunes/
```
### Usage
```bash
$ fortune [OPTIONS] [/path/to/fortunes]
```
Options
```
- -c     Show the cookie file from which the fortune came.
- -f     Print out the list of files which would be searched, but don't print a fortune.
- -e     Consider all fortune files to be of equal size.
```
Example of `-c`
```bash
$ fortune -c
```

```
(fortunes)
%
"Don't waste life in doubts and fears."
  ~Ralph Waldo Emerson
```
Example of `-f`
```bash
$ fortune -f
```

```
100.00% /usr/share/games/fortunes
    17.21% fortunes
    81.51% chinese
     0.98% tang300
     0.30% song100
```
Example of `-e`
```bash
$ fortune -e chinese fortunes
#  is equivalent to
$ fortune 50% chinese 50% fortunes

$ fortune -e chinese fortunes tang300 song100
#  is equivalent to
$ fortune 25% chinese 25% fortunes 25% tang300  25% song100
```
### How to automatically launch fortune when opening a shell window

Depending on which shell you use, at the end of your ~/.bashrc or ~/.zshrc file, copy the following lines into it.
```bash
echo
echo "=============== Quote Of The Day ==============="
echo
fortune
echo
echo "================================================"
echo
```
### How to make your own fortune database file

(1) Write your fortune items into a file.

(2) Append a percent sign (%) after each item. The percent sign should take a new line. The following is an example.
```
Herhangi bir program sadece yararı kadar iyidir. ~Linus Torvalds
%
Yazılım seks gibidir: ücretsiz olunca daha iyi olur. ~Linus Torvalds
%
Sizleri neden diye sorarken duyabiliyorum. Hurd bir yıl içerisinde (ya da iki, ya da öteki ay, kim bilir) yok olup gidecek ve ben çok Minix'e sahibim. ~Linus Torvalds
%
En mutsuz müşterileriniz, öğrenmeniz için en büyük kaynağınızdır.
  ~Bill Gates
%
General Motors, tekonlojisini bilgisayarlar gibi geliştirseydi, 1.000 MPG kapasitesinde 25 dolarlık arabalar sürüyor olurduk.
  ~Bill Gates
```
(3) Generate the index file.
```bash
strfile -c % your-fortune-file your-fortune-file.dat
```
(4) Move the fortune file and its index file into */usr/share/games/fortunes/*.
