---
layout: post
title:  "MySQL CLI: user and DB creation, plus some links"
date:   2014-04-30 17:33:00
tags: mysql mariadb cli database links
---

Recently I've made a decision to use mysql/mariadb command-line interface, because...

* I've not found any good, fast, free and opensource GUI client,
* I think, that CLI is more agile, stable and gets alot more support

So, I've started to use CLI and read manuals/google when I need something particular.

And here is some useful links:

* [Create UTF8 table][create-utf8-table]
* [How To Create a New User and Grant Permissions in MySQL][create-user-and-grant-permissions] @ DigitalOcean community help
* [ArchLinux Wiki MariaDB page][archlinux-wiki-mariadb-page]

Also, while migrating to CLI, I've found some minor problem with long passwords.
I've described it here:

* [Question on DBA@StackExchange][dba-stackexchange-question]
* ["Cannot login through CLI, but phpmyadmin works well" @ ArchLinux Wiki MariaDb page][archlinux-wiki-mariadb-page-cannot-login-trough-cli]

I hope, my contribution will be helpful for other guys who pefer long passwords.

[create-utf8-table]: http://pario.no/2008/01/27/mysql-create-utf8-database/
[create-user-and-grant-permissions]: https://www.digitalocean.com/community/articles/how-to-create-a-new-user-and-grant-permissions-in-mysql
[archlinux-wiki-mariadb-page]: https://wiki.archlinux.org/index.php/MariaDB
[dba-stackexchange-question]: https://dba.stackexchange.com/questions/62200/mysql-mariadb-cli-limits-max-password
[archlinux-wiki-mariadb-page-cannot-login-trough-cli]: https://wiki.archlinux.org/index.php/MariaDB#Cannot_login_through_CLI.2C_but_phpmyadmin_works_well