[< К содержанию](./README.md)

## Установка из исходников

Многие предпочитают устанавливать `Git` из исходников, поскольку такой способ позволяет получить самую свежую версию. Обновление бинарных инсталляторов, как правило, немного отстаёт, хотя в последнее время разница не столь существенна.

Если вы действительно хотите установить `Git` из исходников, у вас должны быть установлены следующие библиотеки, от которых он зависит: `autotools, curl, zlib, openssl, expat и libiconv`. Например, если в вашей системе используется `dnf` (Fedora) или `apt-get` (системы на базе Debian), вы можете использовать одну из следующих команд для установки всех зависимостей, используемых для сборки и установки бинарных файлов `Git`:
```
$ sudo dnf install dh-autoreconf curl-devel expat-devel gettext-devel \
  openssl-devel perl-devel zlib-devel
$ sudo apt-get install dh-autoreconf libcurl4-gnutls-dev libexpat1-dev \
  gettext libz-dev libssl-dev
```
Для того, чтобы собрать документацию в различных форматах (doc, html, info), понадобится установить дополнительные зависимости:
```
$ sudo dnf install asciidoc xmlto docbook2X
$ sudo apt-get install asciidoc xmlto docbook2x
```
Если вы используете систему на базе Debian (Debian/Ubuntu/Ubuntu-производные), вам так же понадобится установить пакет install-info:
```
$ sudo apt-get install install-info
```
Если вы используете систему на базе RPM (Fedora/RHEL/RHEL-производные), вам так же понадобится установить пакет getopt, который уже установлен в системах на базе Debian:
```
$ sudo dnf install getopt
```
К тому же из-за различий имён бинарных файлов вам понадобится сделать следующее:
```
$ sudo ln -s /usr/bin/db2x_docbook2texi /usr/bin/docbook2x-texi
```
Когда все необходимые зависимости установлены, вы можете пойти дальше и скачать самый свежий архив с исходниками из следующих мест: с сайта Kernel.org https://www.kernel.org/pub/software/scm/git, или зеркала на сайте GitHub https://github.com/git/git/releases. Конечно, немного проще скачать последнюю версию с сайта GitHub, но на странице kernel.org релизы имеют подписи, если вы хотите проверить, что скачиваете.

Затем скомпилируйте и установите:
```
$ tar -zxf git-2.8.0.tar.gz
$ cd git-2.8.0
$ make configure
$ ./configure --prefix=/usr
$ make all doc info
$ sudo make install install-doc install-html install-info
```
После этого вы можете получать обновления `Git` посредством самого `Git`:
```
$ git clone git://git.kernel.org/pub/scm/git/git.git
```
---
[< К содержанию](./README.md)