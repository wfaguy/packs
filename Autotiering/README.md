# Autotiering with WFA

This pack will allow you to move volumes around within the same cluster.
The move will be triggered based on performance and busy indicators.

The performance and busy indicators are calculated values.
* The performance indicator will tell you whether something is "slow" (higher value = slower)
* The busy indicator will tell you whether something is "busy" (higher value = busier)

# Tiers

Tiers are defined with numbers.  Lower means faster.  Higher means slower.

Example :
* An AFF would be a tier 0
* A high-end FAS would be a tier 1
* A low-end FAS would be a tier 2

# Promotion / Demotion

* A volume can be promoted to a faster tier (lower number) if it is too slow.
* A volume can be demoted to a slower tier (higher number) if it is doing nothing (not busy & not slow)

# Pack Content

**Datasources :**
* import performance data from OCUM
* import volume move information from OCUM
* import an excel configuration file

**Workflows :**
* setup
    * will install excel module
    * will copy sample configuration file to c:\temp
* move volume - trigger manually
    * will make suggestions for volume move
    * operator must choose manually
    * operator can manipulate threshold and tuning settings
	* a list of all volumes is shown with help columns why volume are or are not candidates
* move volume - trigger automatically
    * no input, can be scheduled
* clear performance data
* export performance data to excel
* export autotiering history to excel

# Setup steps

* Import the dar file
* run the setup workflow
* complete configuration excel file (sample in c:\temp)
* implement the 3 datasources
* using manual workflow, tune settings to have required result
* use clean performance workflow, to re-apply some settings
* once the settings are ok, schedule the auto workflow

# Formula's indicators

The indicators are calculated based on formula's

* **performance indicator** : avg_latency/latency_threshold*avg_latency_weight + highest_peak_in_hour/latency_threshold*peak_weight + peak_count_in_hour*peak_count_weight
* **busy indicator** : IOPS/GB*busy_weight

# Performance import

Performance (latency & IOPS) and capacity information is imported from OCUM (OnCommand Unified Manager).

The indicators are calculated on the fly during import.  Threshold & weight values are coming from configuration excel file (defaults), but can be overridden by custom values, using annotations in OCUM

Performance information is imported incrementally and is aggregated on the fly.  Data comes in as hourly statistics and gets aggregated to daily and finally weekly statistics.
If the default and/or custom values (threshold & weights) need tuning/changes.  You need to re-import performance data to view effect immediatly.

# Aggregate selection

Target aggregates are selected based on tiering numbers, coming from excel file (config file).  Aggregate capacity thresholds are also config file.


