xivo-sugarcrm
=============

This is a demonstration to connecting xivo and sugarcrm with a customer sheet.

You need to add a sub routine on xivo, this agi and you need to configure your xivo.

More information about customer sheet : http://documentation.xivo.fr/production/administration/customerinfo/sheetconfiguration.html#variables

Installation on XiVO
--------------------

1. apt-get install git
2. mkdir /usr/share/asterisk/agi-bin
3. cd /usr/share/asterisk/agi-bin
4. git config --global http.sslverify false
5. git clone https://github.com/sboily/xivo-sugarcrm.git
6. cd xivo-sugarcrm
7. cp sugarcrm.conf /etc/asterisk/extensions_extra.d
8. chown www-data.www-data /etc/asterisk/extensions_extra.d/sugarcrm.conf

Edit the sugarcrm.conf to set the good information via vim or webi.

1. asterisk -r
 * xivo*CLI> dialplan reload
 * xivo*CLI> dialplan show sub-sugarcrm

You need to add this subroutine in your DID for exemple on the webi.

CTI config
----------

Adding on your sheet model the variables :

- {dp-sugarcrm-lastname}
- {dp-sugarcrm-firstname}

Adding on sheet model action the value :

- http://crm/index.php?action=ajaxui#ajaxUILoc=index.php?module=Contacts&action=DDetailView&record={dp-sugarcrm-id}

And authorize the popup url in xivo client.

Library
-------

Taken from : https://github.com/luisbarrueco/python_webservices_library/
