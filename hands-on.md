## Groups and Users
> sudo useradd "username"                 >> Yeni bir User ekler.

> sudo passwd "username"                  >> Yeni User'ın şifresini oluşturur.

> sudo userdel "username"                 >> Belirtilen User'ı siler.

> sudo groupadd "groupname"               >> Yeni bir grup oluşturur.

> sudo groupdel "groupname"               >> Belirtilen grubu siler.

> sudo usermod -g "groupname" "username"  >> Belirtilen gruba belirtilen User'ı ekler.

<BURAYA İLGİLİ RESİMLER!!!>

## cat command
Bu komut ile  belgeleri okuyabilir, değiştirirebilir ve birleştirebiliriz.

>cat "test1.txt"  "test2.txt"    >> test1.txt ve test2.txt belgelerini birleştirerek çıktı verir.

> cat -b                         >> Seçilen belgenin **boş olmayan**  satırlarını numaralandırır.

> cat -n                         >> Seçilen belgenenin tüm satırlarını numaralandırır.

<BURAYA İLGİLİ RESİMLER!!!>

## sort command
Bu komut ile hem alfabetik hem de numrerik sıralama yapılır. Dosyaları, dosya içeriklerini ve dizinleri sıralar. Sıralamayı **case sensitive** olarak yapar.

> sort -r  >> Çıktıyı **ters** olarak sıralar.

> sort -f  >> Çıktıyı **case insensitive** olarak sıralar.  

> sort -n  >> Çıktıyı **numerik** olarak sıralar.

<BURAYA İLGİLİ RESİMLER!!!>

## head and tail commands
> head "dosya.txt" >> Belgenin **ilk on satır**ını çıkarır.

> tail "dosya.txt" >> Belgenin **son on satır**ını çıkarır.

## chown command
Dosyaların sahipliği değiştirir.

> chown "kullanıcı_veya_grup_adı" "dosya_adı"

## chmod command
Bu komut, dosya ve dizinlerin erişim izinlerini değiştirmek için kullanılır.
**4 – read(**r**) permission**

**2 – write(**w**) permission**

**1 – execute(**x**) permission**

**0 – no permission**

> chmod "user,group,others" dosya.txt

## lsof command
lsof(**List Of Open File**) sistemdeki tüm çalışan dosyaları listeler.

> lsof -u "kullanıcı adı" > Belirtilen user tarafından açık olan dosyaları listeler.


## id command 
User ve Grup numarik id'lerini listeler

> id -g >> Mevcut grup id.

> id -G >> Tüm grupların id'leri.

> id -u >> Mevcut user id.

## diff command
Bu komut iki dosya arasındaki farkları listeler.

## dd command
Bu komut dosyaların byte-to-byte kopyalama yapar. cp den en büyük farkı cp sadece belirtilen dosyaları kopyalar, dd ise belirtilen dosyadaki boş alanları da dahil ederek kopyalar. Mesela kopyalanan bir diskise o diskin tam bir replikasını çıkarır.(snapshot gibi)

> dd if = /dev/mp1 of = /dev/mp2 >> Mountpoint1 diskini olduğu gibi Mountpoint2 diskine kopyalar

if "input file", of "output file"

Eğer kopyalama işlemindeki  hatalar gözardı edilmek isteniyorsa **conv=noerror** parametresi verilir:

> dd conv=noerror if = /dev/mp1 of = /dev/mp2 >> Eğer kopyalama işlemindeki  hatalar gözardı edilmek isteniyorsa **conv=noerror** parametresi verilir.

## route command
Route table bilgilerini listeler.

> route

## traceroute command
**ICMP** protokolünü kullanarak belirtilen hedefe gönderilen paketin kaç atlamada hedefe ulaştığını gösterir.

>trace route google.com

## mtr command
mtr komutu **ping** ve **traceroute** komutlarını kombine eder. Gerçek zamanlı olarak gönderilen pakette gerçekleşen veri kayıplarını ve geçikme sürelerini detaylı olarak listeler.

> mtr google.com             >> Gerçek zamanlı olarak listeler

>mtr -n --report google.com  >> <!-- Hedefe sadece 10 paket atarak sonucu rapor halinde listeler. -->
