Mr-Robot:1 — Pentest Report- Nuriyev Xudaverdi
📌 Layihə Haqqında

Bu repository üzərində hazırlanmış VulnHub — Mr-Robot:1 maşını üçün tam Boot-to-Root tipli penetration testing hesabatını əhatə edir. Layihə zamanı hədəf sistem üzərində kəşfiyyat, zəiflik analizi, istismar (exploitation), privilege escalation və post-exploitation mərhələləri həyata keçirilmişdir.

Məqsəd:

WordPress əsaslı sistemdə zəifliklərin aşkarlanması
Reverse shell əldə edilməsi
User və root səviyyəsində sistemə tam giriş
Bütün flag-ların əldə olunması
🛠 İstifadə Olunan Texnologiyalar və Alətlər
Alət	Məqsəd
nmap	Port və servis aşkarlanması
wpscan	WordPress enumeration
hydra / wpscan	Brute-force hücumu
john	MD5 hash qırılması
msfvenom	Reverse shell payload yaradılması
netcat	Reverse shell listener
linpeas	Privilege escalation enumeration
Parrot Security OS	Hücumçu sistemi
🎯 Hədəf Mühit
Parametr	Dəyər
Platforma	VulnHub
VM Adı	Mr-Robot:1
Şəbəkə	Host-Only
Hədəf IP	10.10.14.23
Hücumçu IP	10.10.14.5
OS	Ubuntu 14.04.2 LTS
🔍 Pentest Mərhələləri
1. Reconnaissance (Kəşfiyyat)
arp-scan ilə host aşkarlanması
nmap ilə tam TCP port scan
HTTP/HTTPS servis analizi
robots.txt enumeration
Açıq portlar
80/tcp → HTTP
443/tcp → HTTPS
2. Enumeration

robots.txt faylı içərisində:

fsocity.dic
key-1-of-3.txt

faylları aşkarlanmışdır.

WordPress istifadəçisi:

elliot
3. Exploitation
WordPress Brute Force

fsocity.dic wordlist istifadə edilərək administrator parolu tapılmışdır:

elliot : ER28-0652
Reverse Shell

Theme Editor vasitəsilə 404.php faylına PHP reverse shell yerləşdirilmiş və sistemdə shell əldə edilmişdir.

4. Privilege Escalation
MD5 Hash Crack

password.raw-md5 faylı aşkar edilmişdir:

robot:c3fcd3d76192e4007dfb496cca67e13b

John the Ripper ilə qırılmışdır:

abcdefghijklmnopqrstuvwxyz
SUID Nmap Exploit

Legacy nmap 3.81 binary SUID root hüquqları ilə işlədiyi üçün interactive mode vasitəsilə root shell əldə edilmişdir.

nmap --interactive
!sh
🚨 Aşkarlanmış Zəifliklər
ID	Zəiflik	Risk
Z-01	Sensitive Information Disclosure	Medium
Z-02	WordPress Brute Force	High
Z-03	Authenticated RCE	Critical
Z-04	Weak MD5 Hash Storage	High
Z-05	SUID Nmap Privilege Escalation	Critical
🏴 Əldə Olunan Flag-lar
Key 1
073403c8a58a1f80d943455fb30724b9
Key 2
822c73956184f694993bede3eb39f959
Key 3
04787ddef27c3dee1ee161b21670b4e4
📈 Nəticə

Bu laboratoriya klassik Boot-to-Root penetration testing zəncirini uğurla nümayiş etdirir:

robots.txt disclosure
        ↓
WordPress enumeration
        ↓
Brute-force attack
        ↓
Admin panel access
        ↓
Reverse shell
        ↓
Hash cracking
        ↓
Privilege escalation
        ↓
Root access

Layihə aşağıdakı bacarıqların inkişafına kömək edir:

Web Pentesting
Enumeration
WordPress exploitation
Reverse shell
Linux privilege escalation
Password cracking
Post exploitation
📚 Təhsil Məqsədi

Bu repository yalnız:

təhsil,
laboratoriya,
və etik penetration testing

məqsədləri üçün hazırlanmışdır.

👨‍💻 Müəllif

Xudaverdi Nuriyev
Pentest / Cyber Security Student

⭐ Repository Status

✔ Completed
✔ Root Access Achieved
✔ All Flags Captured