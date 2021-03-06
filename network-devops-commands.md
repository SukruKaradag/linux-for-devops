## lsof command
lsof(***List Of Open File***) sistemdeki tüm çalışan dosyaları listeler.

> lsof -u "kullanıcı adı" > Belirtilen user tarafından açık olan dosyaları listeler.

![lsof command screenshot](/assets/lsof.png "lsof -u user")

## Groups and Users

> sudo useradd "username"                 >> Yeni bir User ekler.

> sudo passwd "username"                  >> Yeni User'ın şifresini oluşturur.

> sudo userdel "username"                 >> Belirtilen User'ı siler.

> sudo groupadd "groupname"               >> Yeni bir grup oluşturur.
 
> sudo groupdel "groupname"               >> Belirtilen grubu siler.

> sudo usermod -g "groupname" "username"  >> Belirtilen gruba belirtilen User'ı ekler.

## id command 
***User*** ve ***Grup*** numarik id'lerini listeler

> id -g >> Mevcut grup id.

> id -G >> Tüm grupların id'leri.

> id -u >> Mevcut user id.

![id command screenshot](/assets/id.PNG "id, id -g, id -G, ve id -u ")

## cat command
Bu komut ile  belgeleri okuyabilir, değiştirirebilir ve birleştirebiliriz.

> cat "test-1.txt"  "test-2.txt"    >> test-1.txt ve test-2.txt belgelerini birleştirerek çıktısını verir.

> cat -b                         >> Seçilen belgenenin tüm satırlarını numaralandırır.

> cat -n                         >> Seçilen belgenin ***boş olmayan***  satırlarını da numaralandırır.

![cat command screenshot](/assets/cat.PNG "cat, cat -b ve cat -n")

## diff command
Bu komut iki dosya arasındaki farkları listeler.

> diff "test-1.txt" "test-2.txt"

![diff command screenshot](/assets/diff.png "diff test-1.txt test-2.txt")

## dd command
Bu komut belirtilen belge ve ya dizini belirtilen hedefe kopyalar. *cp*den farklı olarak ***byte-to-byte*** kopyalama işlemi yapar. Örneğin bir diskin başka bir diske kopyalamasını yaparken diskin tam bir replikasını oluşturur.(AWS ***snapshot*** gibi) Backup almakta kullanışlıdır. !!DUMMY FILES!!

> dd if = /dev/mp1 of = /dev/mp2 >> Mountpoint1 diskini olduğu gibi Mountpoint2 diskine kopyalar

- if "input file", of "output file"

Eğer kopyalama işlemindeki  hatalar gözardı edilmek isteniyorsa ***conv=noerror*** parametresi verilir:

> dd conv=noerror if = /dev/mp1 of = /dev/mp2

Sometimes you need to create dummy files with specified size and count:

- bs=output file size
- count=output files count

> dd if=/dev/urandom of=output-file-name bs=5MB count=1

## route command
Route table bilgilerini listeler.

> route

![route command screenshot](/assets/route.PNG "route")

## traceroute command
***ICMP*** protokolünü kullanarak belirtilen hedefe gönderilen paketin kaç atlamada hedefe ulaştığını gösterir.

>traceroute google.com

![traceroute command screenshot](/assets/traceroute.PNG "traceroute google.com")

## mtr command
mtr komutu ***ping*** ve ***traceroute*** komutlarını kombine eder. Gerçek zamanlı olarak gönderilen pakette gerçekleşen veri kayıplarını ve geçikme sürelerini detaylı olarak listeler.

> mtr google.com             >> Gerçek zamanlı olarak listeler

![mtr command screenshot](/assets/mtr.PNG "mtr google.com")

> mtr -n --report google.com  >> Hedefe sadece 10 paket atarak sonucu rapor halinde listeler.

![mtr -n --report command screenshot](/assets/mtr-2.PNG "mtr -n --report google.com")

- -n parametresi DNS çözümlemesini engeller.

## nslookup ve dig commands
Belirtilen adresin ***NS*** ve ***SOA*** kayıtlarını listeler.

> nslookup google.com

![nslookup command screenshot](/assets/nslookup.PNG "nslookup sukrukaradag.com")


> dig google.com

![dig command screenshot](/assets/dig.PNG "dig sukrukaradag.com")

## tcpdump command
Makinada bulunan tüm ***network interface***'lerin durumunu sorgular ve ***interface***lerden gönderilen paketleri yakalar.



> sudo tcpdump --list-interfaces >> Tüm arayüzleri listeler.

![tcpdump --list-interfaces command screenshot](/assets/tcpdump-list.PNG "sudo tcpdump --list-interfaces")

> sudo tcpdump                  >> Tüm arayüzlerin paket iletimini dinler

> sudo tcpdump -i eth0          >> Belirtilen arayüzün paket iletimini dinler.

> sudo tcpdump -i eth0 -c 10    >> Paket dinleme işlemini 10 ile sınırlar.

![tcpdump command screenshot](/assets/tcpdump.PNG "sudo tcpdump -i eth0 -c 10")

## sudo !! command
Bu komut, komut satırında kendinden önce girilen komutu ***root*** izni ile tekrarlar

>sudo !!

![sudo !! command screenshot](/assets/sudo-!!.PNG "sudo !!")


## wget command
***wget*** komutu ile belirtilen web sayfası indirilir.

> wget https://github.com/SukruKaradag/linux-for-devops/blob/main/linux-commands.md

![wget command screenshot](/assets/wget.PNG "wget https://github.com/SukruKaradag/linux-for-devops/blob/main/linux-commands.md")


## find command
Belirtilen dizin ve ya dosyayı bulur.

> find "aranmak istenen dizin" "dosya"

![find command screenshot](/assets/find.PNG "find /home linux-commands.md")

## free, df ve du commands
diskin kullanım durumunu listeler.

> free

![free command screenshot](/assets/free.PNG "free")

- -b, ya da –-bytes: ***bytes*** olarak listeler.
- -k, ya da –-kilo: ***kilobytes*** olarak listeler (default).
- -m, ya da –-mega: ***megabytes*** olarak listeler.
- -g, ya da –-giga: ***gigabytes*** olarak listeler.

> du -h -d 1 /home/

![du command screenshot](/assets/du.PNG "du -h -d 1 /home/")

> df -h

![df command screenshot](/assets/df.PNG "df -h")

## tr command
tr komutu ile belirtilen dosyanın içinde manipülasyonlar yapılabilir. Pipeler | kullanılarak daha karmaşık scriptler yazılabilir.

> cat deneme.txt | tr "e" "a"           >> deneme.txt içindeki tüm ***e***'ler ***a*** olur.

![tr command screenshot](/assets/tr-1.PNG "cat deneme.txt | tr e a")

> cat deneme.txt | tr "[a-z]" "[A-Z]"   >> deneme.txt içindeki tüm ***küçük*** harfler  ***BÜYÜK*** olur.

![tr command screenshot](/assets/tr-2.PNG "cat deneme.txt | tr [a-z] [A-Z]")

> cat deneme.txt | tr -d "a"            >> deneme.txt içindeki tüm ***a***'lar silinir.

![tr command screenshot](/assets/tr-3.PNG "cat deneme.txt | tr -d i")


## htop, ps ve kill commands
***htop*** gerçek zamanlı olarak cpu ve memory kullanımını gösterir. ***ps*** komutunun aksine mouse ile etkileşimlidir. **ps** komutu da aynı işlemleri yapmakla beraber, ***htop*** komutunundan farklı olarak çıktıyı rapor haline sunar. Aynı zamanda her işlemin ***unique ID***'sini verir. ***kill*** komutu ile de bu ***ID***'ler kullanılarak işlem sonlandırılır.

> htop

![htop command screenshot](/assets/htop.PNG "htop")

> ps aux

![ps command screenshot](/assets/ps.PNG "ps")

- -a = Tüm kullanıcıların işlemlerini gösterir.
- -u = İşlemin sahibini gösterir.
- -x = Terminale bağlı olmayan işlemleri gösterir.

> kill "ID"

## head and tail commands

> head "dosya.txt" >> Belgenin ***ilk on satır***ını çıkarır.

![head command screenshot](/assets/head.PNG "head sayılar.txt")

> tail "dosya.txt" >> Belgenin ***son on satır***ını çıkarır.

![tail command screenshot](/assets/tail.PNG "tail.txt")

## man command
***man*** komutu diğer tüm komutların detaylı kullanımını açıklar.

> man whoami

![man command screenshot](/assets/man.PNG "man whoami")

## sort command
Bu komut ile hem alfabetik hem de numerik sıralama yapılır. Dosyaları, dosya içeriklerini ve dizinleri sıralar. Sıralamayı ***case sensitive*** olarak yapar.

![sort command screenshot](/assets/sort.PNG "sort sort-example.txt")

> sort -r  >> Çıktıyı ***ters*** olarak sıralar.

![sort -r command screenshot](/assets/sortr.PNG "sort -r sort-example.txt")

> sort -f  >> Çıktıyı **case *insensitive*** olarak sıralar.  

![sort -f command screenshot](/assets/sortf.PNG "sort -f sort-example.txt")

> sort -n  >> Çıktıyı ***numerik*** olarak sıralar.

![sort -n command screenshot](/assets/sortn.PNG "sort -n sort-example.txt")


## chown command
Dosyaların sahipliğini değiştirir.

> sudo chown "kullanıcı_veya_grup_adı" "dosya_adı"

![chown command screenshot](/assets/chown.PNG "sudo chown karadag  sort-example.txt")

## chmod command
Bu komut, dosya ve dizinlerin erişim izinlerini değiştirmek için kullanılır. Her bir basamak user, group ve others kullanıcılılarını temsil eder.

> chmod 754 "dosya.txt"
>
- **4 – read(**r**) permission**

- **2 – write(**w**) permission**

- **1 – execute(**x**) permission**

- **0 – no permission**


# SONRA DÜZENLENECEK!!!

- hostnamectl set-hostname "verilecek_ad" && bash
- curl wttr.in/"sehir_adı"
- curl cheat.sh
- Kalıcı alias eklemek için:
```bash
sudo nano ~/.bash_aliases
yada 
sudo nano ~/.bashrc # bu iki dosyadan birine girilir.
# Son satıra:
alias "alias_name='command'" # kalıcı olması istenilen komut yazılır ve kaydedilir.
source ~/.bashrc #değişikliklerin kaydedilmesi için.
```
- ``` > /dev/null 2>&1``` işlemin çıktısını null'a atar.
- ``` | (pipe)``` ilk komutun çıktısının ikinci komutun girdisine yönlendirir.
- ``` ;``` satıra birden fazla komut yazmak için.
- ``` && ``` ilk komut hatasız dönerse ikinci komutu da çalıştırır.
- ``` || ``` ilk komut hatalı dönerse ikinci komutu da çalıştırır.
- watch "docker service ps websrc" # arkaplanda çalışan komutu izler.
