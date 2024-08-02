# security-your-server-minecraft
Secure your Minecraft server
PL: Sekcje:
1. Odwrotny serwer proxy
TCP 1.1. Wybór najlepszego odwrotnego serwera proxy
2. Podszywanie
się pod UUID 2.1. Co to jest spoofing UUID?
2.2. Jakie są konsekwencje zignorowania tego problemu
2.3. Na jakich serwerach działa
ta wada konstrukcyjna 2.4. Jak go
zablokować 2.4.1. Zewnętrzne: IPWhitelist
2.4.2. Zewnętrzny: BungeeGuard
2.4.3. Korzystanie z ochrony
prędkości 2.4.4. Zapora sieciowa 🟥
3. Ukryj Bungeecord 🟥
4. Ukryj panel pterodaktyla | Dowolny widelec 🟥 pterodaktyla
4.1. Blokowanie skanerów 🟥
IOT 4.2. Konfiguracja CloudFlare 🟥
4.3. Konfiguracja serwera WWW 🟥
4.4. Zapora sieciowa 🟥
5. Blokuj sondy 🟥
ICMP 5.1. Zapora sieciowa 🟥
5.2. Edytowanie parametrów 🟥 jądra 6. Usuń wrażliwe wtyczki \

1. Odwrotny serwer proxy TCP:
1.1 Wybór najlepszego odwrotnego serwera proxy
W Internecie dostępnych jest wiele odwrotnych serwerów proxy, najpopularniejsze z nich to: TCPSHIELD, Infininity Filter i MC SHIELD.

Polecam stosowanie NeoProtect, jest bardzo potężny. Ma również wiele funkcji, takich jak AntiBot, AntiVPN i nieograniczony ruch! To prawdopodobnie najlepsza opcja, jaką możesz wybrać. Sprawdź ich witrynę, aby uzyskać więcej informacji.

2. Podszywanie się pod UUID:
2.1. Co to jest spoofing UUID?
Podszywanie się pod UUID zostało po raz pierwszy wykryte na początku 2013 roku i jest obecnie dobrze znaną wadą konstrukcyjną Bungeecord - wykorzystywaną głównie do nękania serwerów. Ten exploit jest jedną z najczęściej używanych metod uzyskiwania uprawnień administratora na podatnych na ataki serwerach Minecraft.

2.2. Jakie są konsekwencje zignorowania tego problemu?
Ignorowanie podszywania się pod UUID sprawi, że Twój serwer będzie podatny na ataki i ujawniony dla wszystkich. Może to spowodować wyciek wszystkich adresów IP gracza, całkowite zniszczenie sieci, a nawet usunięcie serwera! Więc lepiej sprawdź, czy Twój serwer jest podatny na ataki JAK NAJSZYBCIEJ.

2.3. Na jakich serwerach działa ta wada konstrukcyjna
Ta luka działa na każdej instancji bungeecord (w tym na forkach, takich jak flamecord, waterfall), które są podłączone do serwerów Java Edition.

2.4. Jak to zablokować?
2.4.1 Zewnętrzne: IPWhitelist
IPWhitelist pozwala odfiltrować połączenia na określonym serwerze spigot dla określonych adresów IP https://www.spigotmc.org/resources/ipwhitelist.61/
Konfiguracja jest dość prosta, sprawdź stronę z czopem, aby uzyskać więcej informacji.

2.4.2 Zewnętrzne: Bungeeguard
Bungeeguard pozwala na dodanie systemu "tokenów" do serwera króćców i bungee.
https://github.com/lucko/BungeeGuard Konfiguracja jest dość prosta, sprawdź stronę z króćcem, aby uzyskać więcej informacji.

2.4.3 Zewnętrzne: Ochrona przed prędkością
Działa tak samo jak BungeeGuard, dostarczony w konfiguracji prędkości.
https://docs.papermc.io/velocity/player-information-forwarding Konfiguracja jest dość prosta, sprawdź podaną stronę, aby uzyskać więcej informacji.

2.4.3 Wewnętrzny: Zapora sieciowa
Zapora ogniowa jest możliwa za pomocą narzędzia takiego jak iptables/ufw na serwerach
linux To jest dla bardziej zaawansowanych osób - jeśli nie znasz podstawowych poleceń linuxa, polecam trzymać się wtyczek, wtyczki są dobre, ale nie zapewniają maksymalnego bezpieczeństwa.
Mamy 2 narzędzia, z których możemy skorzystać: IPTables | Kroki UFW
UFW:
1. Zainstaluj ufw za pomocą
2. Zezwalaj na połączenia ssh z
3. Zezwalaj na połączenia proxy za pomocą opcji Zmień port proxy! sudo apt-get update && sudo apt-get install ufwsudo ufw allow 22sudo ufw allow 2556525565⚠️OSTRZEŻENIE⚠️: Nie rób tego, jeśli używasz odwrotnego serwera proxy, spójrz na punkt 3.
IPTables jest bardziej zaawansowany (ten artykuł byłby zbyt długi, aby go wyjaśnić, zarządzam iptables z łatwością), więc zamiast wyjaśniać każdy krok, podlinkuję świetny artykuł
o spigotmc https://www.spigotmc.org/wiki/firewall-guide/#firewalling-with-iptables

3. Ukryj Bungeecord:
Ukrywanie bungeecord można wykonać za pomocą odwrotnego proxy z punktu 1. i zapora sieciowa serwera proxy do ich adresów IP
Jak zainstalować zaporę ogniową za pomocą UFW:
1. Zainstaluj ufw za pomocą
2. Zezwalaj na połączenia proxy za pomocą opcji Zmień port proxy i $IP na adres IP serwera proxy (jest to różne dla każdego dostawcy, skontaktuj się z nim w sprawie ich adresów IP!)
3. Powtórz krok 2 dla każdego adresu IP odwrotnego serwera proxy, adresy ip tcpshield: https://tcpshield.com/v4/ (Upewnij się, że używasz również podsieci aka / i liczb po nim)
Jak zapora ogniowa za pomocą IPTables:
SoonTMsudo apt-get update && sudo apt-get install ufwsudo ufw allow from $IP proto tcp to any port 2556525565
