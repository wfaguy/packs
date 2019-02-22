# Aggregate Performance Filter

**Version 1.0.0**

# Filter "Filter aggregates by available capacity and available ops"

A new aggregate filter that allows you to filter on performance & capacity
Use the filter, the filter is the same as “by availabled capacity”, but also asks the added IOPS.
in the return values there are the fields (where you can filter on optionally)

- available ops
- used_head_room_pct
- number of volumes

# Datasource Type "Aggregate Performance Summary"

You need to implement this included datasource to grab the aggregate performance data.
To grab this data you need to connect to your OCUM server and use credentials for the "Report Scheme".

This means you should login into OCUM and create a new database user for "Report scheme" (or re-use an existing user of course)
