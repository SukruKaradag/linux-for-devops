## lsof command
lsof(***List Of Open File***) sistemdeki tüm çalışan dosyaları listeler.

> lsof -u "kullanıcı adı" > Belirtilen user tarafından açık olan dosyaları listeler.


## Groups and Users

> sudo useradd "username"                 >> Yeni bir User ekler.

> sudo passwd "username"                  >> Yeni User'ın şifresini oluşturur.

> sudo userdel "username"                 >> Belirtilen User'ı siler.

> sudo groupadd "groupname"               >> Yeni bir grup oluşturur.

> sudo groupdel "groupname"               >> Belirtilen grubu siler.

> sudo usermod -g "groupname" "username"  >> Belirtilen gruba belirtilen User'ı ekler.

<BURAYA İLGİLİ RESİMLER!!!>


## id command 
***User*** ve ***Grup*** numarik id'lerini listeler

> id -g >> Mevcut grup id.

> id -G >> Tüm grupların id'leri.

> id -u >> Mevcut user id.

## diff command
Bu komut iki dosya arasındaki farkları listeler.

> diff "test-1.txt" "test-2.txt"

## cat command
Bu komut ile  belgeleri okuyabilir, değiştirirebilir ve birleştirebiliriz.

> cat "test1.txt"  "test2.txt"    >> test1.txt ve test2.txt belgelerini birleştirerek çıktı verir.

> cat -b                         >> Seçilen belgenin ***boş olmayan***  satırlarını da numaralandırır.

> cat -n                         >> Seçilen belgenenin tüm satırlarını numaralandırır.

<BURAYA İLGİLİ RESİMLER!!!>

## dd command
Bu komut belirtilen belge ve ya dizini belirtilen hedefe kopyalar. *cp*den farklı olarak ***byte-to-byte*** kopyalama işlemi yapar. Örneğin bir diskin başka bir diske kopyalamasını yaparken diskin tam bir replikasını oluşturur.(AWS ***snapshot*** gibi) Backup almakta kullanışlıdır.

> dd if = /dev/mp1 of = /dev/mp2 >> Mountpoint1 diskini olduğu gibi Mountpoint2 diskine kopyalar

- if "input file", of "output file"

Eğer kopyalama işlemindeki  hatalar gözardı edilmek isteniyorsa ***conv=noerror*** parametresi verilir:

> dd conv=noerror if = /dev/mp1 of = /dev/mp2

## route command
Route table bilgilerini listeler.

> route

## traceroute command
***ICMP*** protokolünü kullanarak belirtilen hedefe gönderilen paketin kaç atlamada hedefe ulaştığını gösterir.

>traceroute google.com

## mtr command
mtr komutu ***ping*** ve ***traceroute*** komutlarını kombine eder. Gerçek zamanlı olarak gönderilen pakette gerçekleşen veri kayıplarını ve geçikme sürelerini detaylı olarak listeler.

> mtr google.com             >> Gerçek zamanlı olarak listeler

> mtr -n --report google.com  >> Hedefe sadece 10 paket atarak sonucu rapor halinde listeler.

## nslookup ve dig commands
Belirtilen adresin ***NS*** ve ***SOA***  lerini sıralar.

> nslookup google.com

> dig google.com

## tcpdump command
Makinada bulunan tüm ***network interface***'lerin durumunu sorgular ve ***interface***lerden gönderilen paketleri yakalar.

> sudo  tcpdump --list-interfaces

> sudo tcpdump -i eth0        >> Belirtilen arayüzün paket iletimini dinler.

> sudo tcpdump -i eth0 -c 10  >> Paket dinleme işlemini 10 ile sınırlar.

## sudo !! command
Bu komut, komut satırında kendinden önce girilen komutu ***root*** izni ile tekrarlar

>sudo !!


## wget command
***wget*** komutu ile belirtilen web sayfası indirilir.

> wget https://github.com/SukruKaradag/linux-for-devops/blob/main/hands-on.md

## find command
Belirtilen dizin ve ya dosyayı bulur.

> find "aranmak istenen dizin" "dosya"

## free, df ve du commands
diskin kullanım durumunu listeler.

> free

- -b, ya da –-bytes: ***bytes*** olarak listeler.
- -k, ya da –-kilo: ***kilobytes*** olarak listeler (default).
- -m, ya da –-mega: ***megabytes*** olarak listeler.
- -g, ya da –-giga: ***gigabytes*** olarak listeler.

> du -h -d 1 /var/

> df -h

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