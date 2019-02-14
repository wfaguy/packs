# datasource

This pack has a datasource example to import excel files (just clone an change the scheme)

# workflows

- Setup workflow
- Export workflow (export any scheme to excel)

# requirements

- Run the setup workflow first (to install psexcel module)
- The datasource uses the hostname for the excel path (excel filename must match the schemename)
- Your excel must have a sheet for each table (matching names)
- Each sheet must have a table with the all the table fields (id not mandatory, unless you have foreign keys)

# important

The datasource handles relations too (primary / foreign key). It will assume every field ending with \_id is a foreign key.
Id & \_id fiels can be strings (useful to use formula's), the code will hash them to integers.

Watch the log files, a log with the name of your scheme is created. Enable debugging by setting port-number in datasource to value 1.
