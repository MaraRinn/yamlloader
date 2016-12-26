A data loader, to bring in the YAML version of the SDE

Loads data back into approximately the same structure.

# Installation

## Support files

Copy the provided invVolumes1.csv and invVolumes2.csv into the sde folder.

## macOS

Remember to install libyaml first, and adjust the include path for clang:

    sudo port install libyaml
    export C_INCLUDE_PATH=/opt/local/include

or

    brew install libyaml
    export C_INCLUDE_PATH=/usr/local/include

## PostgreSQL

For PostgreSQL, you will also need to install `psycopg2`.

# Operation

Run

    python Load.py «engine»

Where «engine» is one of:

 - postgres
 - postgresschema
 - mysql
 - mssql
 - oracle
 - sqlite3

See the [SQL Alchemy docs](http://docs.sqlalchemy.org/en/latest/core/engines.html#supported-databases) for more details.

# Database Engines

## PostgreSQL

When using the pgsql command line remember to quote table names, since they are CamelCase instead of lowercase:

    eve_sde=> select * from "invTypes" where lower("typeName") like '%datacore%';

## PostgresSQL with Schema

You must create the "evesde" schema before using the loader.
