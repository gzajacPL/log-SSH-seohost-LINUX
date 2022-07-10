# log-SSH-seohost-LINUX
Logowanie na serwer poprzez SSH na przykładzie SeoHost.pl (system Linux).

https://gzajac.pl/logowanie-na-serwer-poprzez-ssh-na-przykladzie-seohost-pl-system-linux/

Logowanie na serwer poprzez SSH na przykładzie SeoHost.pl (system Linux).
ByGZ	
10/07/2022

Jeśli nie ma dostępu do SSH – poproś o niego obsługę seohost emailem.

Tworzenie klucza publicznego i prywatnego:

w katalogu HOME musi być katalog ukryty .ssh. Trzeba go utworzyć jeśli nie ma:

mkdir ~/.ssh

Tworzenie kluczy w konsoli:

ssh-keygen -t rsa -b 4096 -f .ssh/s_seohost -C "serwer123"

    ssh-keygen – generator kluczy,
    -t rsa  – wybór szyfrowania ( RSA),
    -b 4096 – moc szyfrowania ( zalecane 4096),
    -f .ssh/s_seohost – nazwa, pod którą maja być pliki
    -C „serwer123” – komentarz- wpisanie w tym miejscu nazwy serwera pomoże w identyfikacji kluczy

Następnie 3x enter, zostanie wyświetlone podsumowanie.

w katalogu .ssh będą dwa pliki: s_seohost i s_seohost.pub

Plik z rozszerzeniem .pub musimy wrzucić na serwer seohost do folderu .ssh i pliku

authorized_keys

jeśli go nie ma to trzeba utworzyć. W tym pliku wkleja zawartość z .pub :

cat ~/.ssh/s_seohost.pub

skopiować zawartość z konsoli do pliku authorized_keys.

Stworzyć plik config w folderze .ssh u siebie na kompie.

w tym pliku wklejamy:

Host home h22.seohost.pl
  HostName h22.seohost.pl
  Port 12345
  IdentityFile ./.ssh/s_seohost
  User srv123456 

tam gdzie port i user wpisujemy swoje dane z profilu użytkownika seohost

możemy sobie już wpisać w konsoli

ssh home

i nawiązać połączenie z serwerem poprzez ssh 🙂

Linki które mogą się przydać:

https://pomoc.home.pl/baza-wiedzy/logowanie-ssh-gdzie-znalezc-klucze-rsa-do-polaczenia

https://bezpiecznafirma.com.pl/blog/jak-generowac-klucz-ssh/

https://docs.ovh.com/pl/dedicated/tworzenie-klucze-ssh-dedykowane/
