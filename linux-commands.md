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

![id command screenshot](/assets/id.png "id, id -g, id -G, ve id -u ")

## diff command
Bu komut iki dosya arasındaki farkları listeler.

> diff "test-1.txt" "test-2.txt"

![diff command screenshot](/assets/diff.png "diff test-1.txt test-2.txt")

## cat command
Bu komut ile  belgeleri okuyabilir, değiştirirebilir ve birleştirebiliriz.

> cat "test-1.txt"  "test-2.txt"    >> test-1.txt ve test-2.txt belgelerini birleştirerek çıktısını verir.

> cat -b                         >> Seçilen belgenenin tüm satırlarını numaralandırır.

> cat -n                         >> Seçilen belgenin ***boş olmayan***  satırlarını da numaralandırır.

![cat command screenshot](/assets/cat.png "cat, cat -b ve cat -n")

## dd command
Bu komut belirtilen belge ve ya dizini belirtilen hedefe kopyalar. *cp*den farklı olarak ***byte-to-byte*** kopyalama işlemi yapar. Örneğin bir diskin başka bir diske kopyalamasını yaparken diskin tam bir replikasını oluşturur.(AWS ***snapshot*** gibi) Backup almakta kullanışlıdır.

> dd if = /dev/mp1 of = /dev/mp2 >> Mountpoint1 diskini olduğu gibi Mountpoint2 diskine kopyalar

- if "input file", of "output file"

Eğer kopyalama işlemindeki  hatalar gözardı edilmek isteniyorsa ***conv=noerror*** parametresi verilir:

> dd conv=noerror if = /dev/mp1 of = /dev/mp2

## route command
Route table bilgilerini listeler.

> route

![route command screenshot](/assets/route.png "route")

## traceroute command
***ICMP*** protokolünü kullanarak belirtilen hedefe gönderilen paketin kaç atlamada hedefe ulaştığını gösterir.

>traceroute google.com

![traceroute command screenshot](/assets/traceroute.png "traceroute google.com")

## mtr command
mtr komutu ***ping*** ve ***traceroute*** komutlarını kombine eder. Gerçek zamanlı olarak gönderilen pakette gerçekleşen veri kayıplarını ve geçikme sürelerini detaylı olarak listeler.

> mtr google.com             >> Gerçek zamanlı olarak listeler

![mtr command screenshot](/assets/mtr.png "mtr google.com")

> mtr -n --report google.com  >> Hedefe sadece 10 paket atarak sonucu rapor halinde listeler.

![mtr -n --report command screenshot](/assets/mtr-2.png "mtr -n --report google.com")

- -n parametresi DNS çözümlemesini engeller.

## nslookup ve dig commands
Belirtilen adresin ***NS*** ve ***SOA***  lerini sıralar.

> nslookup google.com

![nslookup command screenshot](/assets/nslookup.png "nslookup sukrukaradag.com")


> dig google.com

![dig command screenshot](/assets/dig.png "dig sukrukaradag.com")

## tcpdump command
Makinada bulunan tüm ***network interface***'lerin durumunu sorgular ve ***interface***lerden gönderilen paketleri yakalar.



> sudo tcpdump --list-interfaces >> Tüm arayüzleri listeler.

![tcpdump --list-interfaces command screenshot](/assets/tcpdump-list.png "sudo tcpdump --list-interfaces")

> sudo tcpdump                  >> Tüm arayüzlerin paket iletimini dinler

> sudo tcpdump -i eth0          >> Belirtilen arayüzün paket iletimini dinler.

> sudo tcpdump -i eth0 -c 10    >> Paket dinleme işlemini 10 ile sınırlar.

![tcpdump command screenshot](/assets/tcpdump-list.png "sudo tcpdump -i eth0 -c 10")

## sudo !! command
Bu komut, komut satırında kendinden önce girilen komutu ***root*** izni ile tekrarlar

>sudo !!

![sudo !! command screenshot](/assets/sudo-!!.png "sudo !!")


## wget command
***wget*** komutu ile belirtilen web sayfası indirilir.

> wget https://github.com/SukruKaradag/linux-for-devops/blob/main/linux-commands.md

![wget command screenshot](/assets/wget.png "wget https://github.com/SukruKaradag/linux-for-devops/blob/main/linux-commands.md")


## find command
Belirtilen dizin ve ya dosyayı bulur.

> find "aranmak istenen dizin" "dosya"

![find command screenshot](/assets/find.png "find /home linux-commands.md")

## free, df ve du commands
diskin kullanım durumunu listeler.

> free

![free command screenshot](/assets/free.png "free")

- -b, ya da –-bytes: ***bytes*** olarak listeler.
- -k, ya da –-kilo: ***kilobytes*** olarak listeler (default).
- -m, ya da –-mega: ***megabytes*** olarak listeler.
- -g, ya da –-giga: ***gigabytes*** olarak listeler.

> du -h -d 1 /var/

![du command screenshot](/assest/du.png "du -h -d 1 /home/")

> df -h

![df command screenshot](/assest/df.png "df -h")

## tr command
tr komutu ile belirtilen dosyanın içinde manipülasyonlar yapılabilir. Pipeler | kullanılarak daha karmaşık scriptler yazılabilir.

> cat deneme.txt | tr "e" "a"           >> deneme.txt içindeki tüm ***e***'ler ***a*** olur.

> cat deneme.txt | tr "[a-z]" "[A-Z]"   >> deneme.txt içindeki tüm ***küçük*** harfler  ***BÜYÜK*** olur.

> cat deneme.txt | tr -d "a"            >> deneme.txt içindeki tüm ***a***'lar silinir.


## htop, ps ve kill commands
***htop*** gerçek zamanlı olarak cpu ve memory kullanımını gösterir. ***ps*** komutunun aksine mouse ile etkileşimlidir. **ps** komutu da aynı işlemleri yapmakla beraber, ***htop*** komutunundan farklı olarak çıktıyı rapor haline sunar. Aynı zamanda her işlemin ***unique ID***'sini verir. ***kill*** komutu ile de bu ***ID***'ler kullanılarak işlem sonlandırılır.

> htop

> ps 

- -a = Tüm kullanıcıların işlemlerini gösterir.
- -u = İşlemin sahibini gösterir.
- -x = Terminale bağlı olmayan işlemleri gösterir.

> ps aux

> kill "ID"

## head and tail commands

> head "dosya.txt" >> Belgenin ***ilk on satır***ını çıkarır.

> tail "dosya.txt" >> Belgenin ***son on satır***ını çıkarır.

## man command
***man*** komutu diğer tüm komutların detaylı kullanımını açıklar.

> man ls 

## sort command
Bu komut ile hem alfabetik hem de numerik sıralama yapılır. Dosyaları, dosya içeriklerini ve dizinleri sıralar. Sıralamayı ***case sensitive*** olarak yapar.

> sort -r  >> Çıktıyı ***ters*** olarak sıralar.

> sort -f  >> Çıktıyı **case *insensitive*** olarak sıralar.  

> sort -n  >> Çıktıyı ***numerik*** olarak sıralar.

<BURAYA İLGİLİ RESİMLER!!!>

## chown command
Dosyaların sahipliğini değiştirir.

> chown "kullanıcı_veya_grup_adı" "dosya_adı"

## chmod command
Bu komut, dosya ve dizinlerin erişim izinlerini değiştirmek için kullanılır.

**4 – read(**r**) permission**

**2 – write(**w**) permission**

**1 – execute(**x**) permission**

**0 – no permission**

> chmod "user,group,others" dosya.txt