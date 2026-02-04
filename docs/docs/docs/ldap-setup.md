sudo yum -y install openldap compat-openldap openldap-clients openldap-servers openldap-servers-sql openldap-devel

sudo systemctl start slapd.service
sudo systemctl enable slapd.service
sudo systemctl status slapd.service

   Konfigurasi Server LDAP 
cd /etc/openldap/slapd.d
nano ldaprootpasswd.ldif
dn: olcDatabase={2}hdb,cn=config
changetype: modify
replace: olcRootPW
olcRootPW:{SSHA}XlygHH6CzOJgkSTfcHlo5qr+ayp2Z9aM  |rahasia123  |IP 77 admin123 

nano ldapdomain.ldif
dn: olcDatabase={1}monitor,cn=config
changetype: modify
replace: olcAccess
olcAccess: {0}to * by dn.base="gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth" read by dn.base="cn=infra,dc=adminjalan,dc=com" read by *$

dn: olcDatabase={2}hdb,cn=config
changetype: modify
replace: olcSuffix
olcSuffix: dc=adminjalan,dc=com
-
replace: olcRootDN
olcRootDN: cn=infra,dc=adminjalan,dc=com
-
replace: olcRootPW
olcRootPW: {SSHA}X/mjBPnl5/TCb9e0Z/dDdIhKADdQ02ff
-
replace: olcAccess
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=infra,dc=adminjalan,dc=com" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=infra,dc=adminjalan,dc=com" write by * read


CARA EXPORT 
ldapmodify -Y EXTERNAL -H ldapi:/// -f ldapdomain.ldif

CARA CEK CONECT
ldapsearch -x -D "cn=infra,dc=adminjalan,dc=com" -W -b "dc=adminjalan,dc=com"

  Konfigurasi Database LDAP  
cp /usr/share/openldap-servers/DB_CONFIG.example /var/lib/ldap/DB_CONFIG
chown -R ldap:ldap /var/lib/ldap/DB_CONFIG
systemctl restart slapd

BUAT USER DAB GROP LDAP
mkdir -p /opt/ldap
nano base.ldif
dn: dc=adminjalan,dc=com
objectClass: top
objectClass: dcObject
objectClass: organization
o: adminjalan
dc: adminjalan

dn: ou=People,dc=adminjalan,dc=com
objectClass: organizationalUnit
ou: People

dn: ou=Group,dc=adminjalan,dc=com
objectClass: organizationalUnit
ou: Group

-------------------
nano groups.ldif
dn: cn=sysadmin,ou=Group,dc=adminjalan,dc=com
objectClass: posixGroup
objectClass: top
cn: sysadmin
gidNumber: 10000
memberUid: sys.daniel

ldapadd -c -x -D "cn=infra,dc=adminjalan,dc=com" -W -f /opt/ldap/opr.ldif
