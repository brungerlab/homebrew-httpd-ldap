# homebrew-httpd-ldap
ldap-ldap.br and apr-util-ldap.br formulas for httpd with ldap support

----------------------------------------------------------------------

The httpd-ldap.br is meant as a replacement for the standard homebrew httpd.br formula.

To install on your system, first stop apache and brew services if you have them running:

sudo apachectl stop
brew services stop httpd

Move your httpd.conf and any other customized subdirectories from /usr/local/etc/httpd/ to another location (e.g. Desktop).

Uninstall existing httpd:

brew uninstall httpd
rm -rf /usr/local/etc/httpd

Note: do not uninstall apr-util since other services such as php depend on it.

Install formulas:

brew tap axelbrunger/homebrew-httpd-ldap

Check they are there:

ls /usr/local/Homebrew/Library/Taps/axelbrunger/homebrew-httpd-ldap

Install apr-util-ldap and httpd-ldap

brew reinstall -s apr-util-ldap
brew reinstall -s httpd-ldap

Move back/replace the httpd.conf and other customized subdirectories back to /usr/local/etc/httpd/

brew services start axelbrunger/httpd-ldap/httpd-ldap

sudo apachectl configtest
sudo apachectl start


