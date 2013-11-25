## Needed extensions

* xsl for php
* curl for php
* mysql(i) for php
* gd for php
* mod_rewrite for apache

## Install the files

* Down the .tgz we sent you a link to
* un"zip" it.
* Untar the content of *.files.tar to an empty directory (locally or on the server)
* Move the content of that directory into your DOCOUMENT_ROOT on your server (or upload it, if you have it locally)
* Don't forget the .htaccess, as well.
* make sure tmp/ is writeable for the webserver (and later also files/ dynimages/ and data/

## Setup the database

* Create a new database in mysql (you can also use an existing one, since all tables are prefixed)
* Import the sql into MySQL in the *.tgz you downloaded and extracted. It's usually called something like xyz.freeflux.net.sql
* Open _conf/config.xml_ and edit the following section:

````
    <connections>
        <db type="dsn">
            <phptype>mysql</phptype>
            <username>exportcms</username>
            <password>exportcms</password>
            <hostspec>localhost</hostspec>  
            <database>exportcms</database>
            <tableprefix>exportcms_</tableprefix>         
        </db>
````

Replace _username_, _passwort__, _database_ and _tableprefix_ with your values.

_tableprefix_ is a little bit special, but easy to find out. Just look into that xyz.freeflux.net.sql file and search for the first line starting with 

    -- Table structure for table `xyz_freeflux_net__sequences_seq`

Your tableprefix would be in the case:

    xyz_freeflux_net_

## Call the site

Now you should be able to call the site and your freeflux blog. If something goes wrong, try deleting everything in tmp/* or just a 2nd reload (sometimes the config file is not generated correctly in the first run)


## Compatibility

* All this was tested with the latest PHP and MySQL from Ubuntu  13.10. PHP 5.5.3 and MySQL 5.5.34. Since freeflux.net ran on much older versions (PHP 5.3 and MySQL 5.0), it should run in everything between, too.