## Go Dili Kurulum
Eğer Go'nun eski versiyonundan yükseltme yapıyorsanız, öncelikle var olan sürümün silinmesi gerekmektedir.

#### Linux,Mac OSX  ve FreeBSD tarball lar
<code> /usr/local </code> dizinin içerisine <code> root </code> yada <code> sudo </code> olarak dosyaların çıkartılması gerekmektedir. Direkt olarak <code> /usr/local </code> dizini içerisinde go alt dizini oluşacak, dosyalar arşivden çıkartıldıktan sonra. [Arşivi indirmek için](https://golang.org/dl/)
```
tar -C /usr/local -xzf go1.10.2.linux-amd64.tar.gz
```
Daha sonra <code> /usr/local/bin </code> <code> PATH </code> ortam değişkenine eklenmesi gerekmektedir. Bunu eklemeyi <code> /etc/profile </code> dosyasının içine yolu ekleyerekte yapabilirsiniz(bu tamamıyla global yapar yada <code> $HOME/.profile </code> içerisine de ekleme yaparak kullanabilirsiniz.

```
export PATH=$PATH:/usr/local/go/bin
```  

#### Özel Lokasyona Yükleme
Go dilinin derlenmiş araçları genellikle <code> /usr/local/go </code> windowsta <code>c:\Go</code> olur fakat farklı bir lokasyon da yükleme yapmak mümkündür.  Bu nedenle farklı bir lokasyona yükleme yapmak için <code> GOROOT </code> ortam değişkenini , go dilinin derlenmiş araçlarının bulunduğu dizinini göstermesi gerekmektedir.
Örneği go'yu ev dizinine yükleme yaptıysan eğer, <code> $HOME/.profile </code>  dosyasına şu şekilde ekleme yapman gerekmektedir.
```
export GOROOT=$HOME/go1.X
export PATH=$PATH:$GOROOT/bin
```
Not: <code>GOROOT</code> sadece özel lokasyona yükleme yapıldığında kullanılır. Haricin de kullanılmasına gerek yoktur.

#### Yüklemenin Test Edilmesi
Go'nun düzgün yüklenip yüklenmediğini test etmek için çalışma dizininde basit bir program yapıcağız.
Şimdi çalışma dizinin de, ki burası <code> $HOME/go </code> oluyor.Eğer farklı bir çalışma alanı kullanmak istersen bunu <code> GOPATH</code> ortam değişkeninde göstermen gerekiyor.
Şimdi bu çalışma alanın içerisin de <code> src/hello </code>  dizinin oluştur ve bu dizinin içerisinde ise <code> hello.go </code> adlı bir dosya oluştur.

```
package main

import "fmt"

func main() {
    fmt.Printf("merhaba dünya\n")
}
```
Daha sonra ise <code> go ile </code> derleme yap
```
$ cd $HOME/go/src/hello
$ go build
```
Bu komutlar çalışma dizini içerinde ki test programında derlenmiş <code> hello </code> adında bir dosya oluşturucak. Onu çalıştırmak için ise
```
$ ./hello
merhaba dünya
```
Eğer 'merhaba dünya' mesajını gördüysen, go tam olarak yüklenmiş demektir. <code> go install </code> komutunu çalıştırarak, çalışma dizinin bin klasörü içerine derlenmiş programının yüklenmesini sağlar ve <code> go clean </code> komutu ise temizler.

Go ile kod yazmaya başlamadan önce, [Go Kodu Nasıl Yazılır ?](./Go_kodu_nasil_yazilir.md) makalesini okuman go dili hakkında ki genel konseptlerin,araçların ve kuralların iyice oturmasını sağlayacaktır.

#### Go'nun Sistemden Kaldırılması
Var olan Go yüklemesini kaldırmak için <code> /usr/local/ </code> dizini içerisinde ki <code> go </code> dizinin silinmesi , eğer farklı bir lokasyona yükleme yaptıysanız oranın silinmesi gerekmektedir. Ayrıca Go bin dizinin <code> PATH </code> ortam değişkeninden de kaldırılması gerekmektedir. Daha önce ortam değişkenini nereye eklediyseniz oradan komutlar silinmeli eğer <code> /etc/profile </code> üzerinden <code>PATH</code> değişkeni eklenmişse orası <code>~/.bashrc </code> üzerinden ekleme yapıldıysa orada ki yazılan go derlenmiş araçlarını gösteren komut kaldırılmalıdır. Eğer Go'yu Mac OS X  paketi olarak yükleme yaptıysanız <code> /etc/paths.d/go dosyası silinmelidir. Windows kullanıcıları ayrıca bu dökümantasyonu okumalı.
[Ortam Değişkenlerinin Windowsta Eklenmesi](https://github.com/golang/go/wiki/SettingGOPATH)
