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
$ git clone https://github.com/enginakdeniz/fortunes.git
$ sudo mv fortunes/* /usr/share/games/fortunes/

# Mac
$ git clone https://github.com/enginakdeniz/fortunes.git
$ strfile fortunes/data/aforizma
$ mv fortunes/* /usr/local/share/games/fortunes/
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
"Microsoft'ta sayısız parlak fikir var, ancak bunların hepsinin yukarıdan geldiği düşünülüyor - korkarım bu pek doğru değil."
  ~Bill Gates
```
Example of `-f`
```bash
$ fortune -f
```

```
100,00% /usr/share/games/fortunes
    100,00% aforizma
```
Example of `-e`
```bash
$ fortune -e aforizma art-of-war
#  is equivalent to
$ fortune 50% aforizma 50% art-of-war

$ fortune -e aforizma art-of-war hayyam-rubai
#  is equivalent to
$ fortune 33% aforizma 33% art-of-war 33% hayyam-rubai
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
