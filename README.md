# postfix-ldap-schema
Simple LDAP schema for Postfix which provides the types required by http://www.postfix.org/LDAP_README.html

It features:
- attributetype *mailacceptinggeneralid* to list typical aliases for the local part of the address
- attributetype *maildrop* for the final mail box destination used by Postfix
- objectclass *postfixUser* to identify users who receive mail by Postfix

An example LDAP entry for a user *mmu@example.net* could look like:
````
dn: uid=mmu,ou=accounts,dc=example,dc=net
objectclass: top
objectclass: person
objectclass: posixAccount
objectclass: postfixUser
cn: Max Mustermann
sn: Mustermann
uid: mmu
uidNumber: 5001
gidNumber: 5000
homeDirectory: /home/vmail
mailacceptinggeneralid: mmu
mailacceptinggeneralid: max.mustermann
mailacceptinggeneralid: m.mustermann
mailacceptinggeneralid: bugs
maildrop: mmu
````
Please note that the OID used in the schema here is an OID of the type *Experimental OpenLDAP*, see also http://www.oid-info.com/get/1.3.6.1.4.1.4203.666 .


The schema can be found on various sources on the internet. The current version was copied from http://fossies.org/linux/group-e/doc/examples/LDAP/schema/postfix.schema and has been slightly modified.
