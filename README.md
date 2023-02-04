# homebrew-httpd-ldap
ldap-ldap.rb and apr-util-ldap.rb formulas for httpd with ldap support

----------------------------------------------------------------------

The httpd-ldap.rb is meant as a replacement for the standard homebrew httpd.rb formula.

Current versions:

httpd 2.4.55

apr-util 1.6.3

To install on your system, first stop apache and brew services if you have them running:

`sudo apachectl stop`

`brew services stop httpd`

Move your httpd.conf and any other customized subdirectories from /usr/local/etc/httpd/ to another location (e.g. Desktop).

Uninstall existing httpd: 

`brew uninstall httpd`

`rm -rf /usr/local/etc/httpd`

Note: do not uninstall apr-util since other services such as php depend on it.

Install formulas:

`brew tap axelbrunger/homebrew-httpd-ldap`

Check the two .rb files are there:

`ls /usr/local/Homebrew/Library/Taps/axelbrunger/homebrew-httpd-ldap`

Install apr-util-ldap and httpd-ldap

`brew reinstall -s apr-util-ldap`

`brew reinstall -s httpd-ldap`

Move back/replace the httpd.conf and other customized subdirectories back to /usr/local/etc/httpd/

Check that ldap modules are installed:

`/usr/local/opt/httpd-ldap/lib/httpd/modules/mod_authnz_ldap.so`
`/usr/local/opt/httpd-ldap/lib/httpd/modules/mod_ldap.so`

Start httpd-ldap

`sudo brew services start httpd-ldap`

Do a configuration test

`sudo apachectl configtest`

Start apache

`sudo apachectl start`

To enable user/password for a spefic directory use these statements in httpd.conf

        <Directory "directory-pathname">
                AuthType Basic
                AuthBasicProvider ldap
		AuthLDAPURL ldap://ldap-server/dc=...,dc=...
		AuthName "use your mac account"
		require valid-user
        </Directory>



