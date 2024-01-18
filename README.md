# NAME

Apache::Session::MariaDB - An implementation of Apache::Session using MariaDB

# SYNOPSIS

    use Apache::Session::MariaDB;

    #if you want Apache::Session to open new DB handles:

    tie %hash, 'Apache::Session::MariaDB', $id, {
       DataSource => 'dbi:MariaDB:sessions',
       UserName   => $db_user,
       Password   => $db_pass,
       LockDataSource => 'dbi:MariaDB:sessions',
       LockUserName   => $db_user,
       LockPassword   => $db_pass
    };

    #or, if your handles are already opened:

    tie %hash, 'Apache::Session::MariaDB', $id, {
       Handle     => $dbh,
       LockHandle => $dbh
    };

# DESCRIPTION

This module is an implementation of Apache::Session. It uses the
MariaDB backing store and the MariaDB locking scheme. See the example,
and the documentation for Apache::Session::Store::MariaDB and
Apache::Session::Lock::MariaDB for more details.

It's based on [Apache::Session::MySQL](https://metacpan.org/pod/Apache%3A%3ASession%3A%3AMySQL) but uses [DBD::MariaDB](https://metacpan.org/pod/DBD%3A%3AMariaDB) instead
of [DBD::mysql](https://metacpan.org/pod/DBD%3A%3Amysql). The initial reason to create this new module is that
[DBD::MariaDB](https://metacpan.org/pod/DBD%3A%3AMariaDB) requires to explicitly indicate `a_session` column as
binary in [DBI](https://metacpan.org/pod/DBI)'s bind\_param calls, which is different from [DBD::mysql](https://metacpan.org/pod/DBD%3A%3Amysql)
and thus [Apache::Session::MySQL](https://metacpan.org/pod/Apache%3A%3ASession%3A%3AMySQL) doesn't support it.

# AUTHOR

Best Practical Solutions, LLC <modules@bestpractical.com>

Jeffrey William Baker <jwbaker@acm.org>

Tomas Doran &lt;bobtfish@bobtfish.net&lt;gt>

# LICENSE AND COPYRIGHT

Copyright (C) 2024, Best Practical Solutions LLC.

This library is free software; you can redistribute it and/or modify it
under the same terms as Perl itself.

# SEE ALSO

[Apache::Session::MySQL](https://metacpan.org/pod/Apache%3A%3ASession%3A%3AMySQL), [Apache::Session::File](https://metacpan.org/pod/Apache%3A%3ASession%3A%3AFile), [Apache::Session::Flex](https://metacpan.org/pod/Apache%3A%3ASession%3A%3AFlex),
[Apache::Session::DB\_File](https://metacpan.org/pod/Apache%3A%3ASession%3A%3ADB_File), [Apache::Session::Postgres](https://metacpan.org/pod/Apache%3A%3ASession%3A%3APostgres), [Apache::Session](https://metacpan.org/pod/Apache%3A%3ASession)
