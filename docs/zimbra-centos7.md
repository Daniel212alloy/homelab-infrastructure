1.nano /etc/named.conf


options {
        listen-on port 53 { 127.0.0.1; };
        listen-on-v6 port 53 { ::1; };
        directory       "/var/named";
        dump-file       "/var/named/data/cache_dump.db";
        statistics-file "/var/named/data/named_stats.txt";
        memstatistics-file "/var/named/data/named_mem_stats.txt";
        allow-query     { localhost; };

Menjadi

options {
        listen-on port 53 { any; };
        listen-on-v6 port 53 { ::1; };
        directory       "/var/named";
        dump-file       "/var/named/data/cache_dump.db";
        statistics-file "/var/named/data/named_stats.txt";
        memstatistics-file "/var/named/data/named_mem_stats.txt";
        allow-query     { any; };






forwarders {
                8.8.8.8;
                8.8.4.4;
        };


2
3
4
        
zone "adminjalanan.local" {
    type master;
    file "/var/named/adminjalanan.local.hosts";
};


nano /var/named/adminjalanan.local.hosts


$TTL 38400
adminjalanan.local.   IN  SOA  mail.adminjalanan.local. admin.adminjalanan.local. (
                        1520401033 ;
                        10800
                        3600
                        604800
                        38400 )
adminjalanan.local.   IN  NS   mail.adminjalanan.local.
mail.adminjalanan.local. IN  A IP VM ZIMBRANYA
adminjalanan.local.   IN  A  IP VM ZIMBRANYA     
adminjalanan.local.   IN  MX 10 mail.adminjalanan.local.

systemctl restart named
rndc reload adminjalanan.local

dig aloy.adminkopi.local
nslookup adminjalanan.local 10.101.175.50

wget https://files.zimbra.com/downloads/8.8.15_GA/zcs-8.8.15_GA_3869.RHEL7_64.20190918004220.tgz
sudo  ./install.sh
