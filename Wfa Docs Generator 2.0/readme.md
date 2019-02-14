# WFA Docs Generator 2.0

**Version 1.0.2**

A new WFA Doc generator with most features you'll want :

* No need for installing Word
* Creates documents for :
    * Workflows
    * Commands
    * Scheme's, dictionaries & datasources
    * Exports Dar files

# Content

* a datasource to import WFA data like categories, workflows, datasource.  This make it possible to visually select a workflow.
* a setup workflow to install the template a PSWord (and PSExcel) powershell modules
* a workflow to generate the documentation

# Installation

* run the setup workflow (see category "Documentation")
* add a datasource to import the WFA information (the workflow will show you a list of everything)
* run the document workflow

**Note** : don't try to document EVERYTHING at the same time, the workflow (at least on my laptop) never finished validating.  
**Note 2** : I've tested intensively, even found a few new WFA bugs along the way.  Let me know if you have issues and if you want extra's

# Template

A template is included, but you can make your own.

**The template must contain these styles :**
* Heading 1
* Heading 2
* Heading 3
* Console (for powershell and sql queries)

**Following variables are getting replaced**
* #version#
* #date#
* #title#

**Tables use this style**
* Light List - Accent 5

# Export to dar-file
You will notice that the commands to document the different objects have an additional option to export to dar-files.
This requires a loop-back credentials to invoke this export, as it will then invoke rest to itself (localhost).  It now defaults to https://localhost, but can be overwritten in the commands.  It assumes a loop-back credentials "localhost", and can again be overridden in the commands.

# Version Control
A hidden feature perhaps.  In you description fields in wfa (for workflow & command), you can enable version control.
Just add below your description (in wfa) :

   # version control
   1.0.0 Initial version
   1.0.1 Next version
   ... add more versions

The doc generator will parse those and add a version control table in the document