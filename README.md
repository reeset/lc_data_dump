# Library of Congress Open Data Dump

This data is derived from the U.S. Library of Congress's open data dump.  You can read about the data dump here: [Library offers largest release of digital catalog records in history](https://loc.gov/item/prn-17-068/ ).  

The data released by the Library of Congress has been made available in a number of formats.  For the purpose of these files, I've created a set of data files that make use of the UTF8 data files.  I've tried to note the process used for each set of data files.

# Bibliographic data:

MARC Records (~3.5 GB): Compressed: [Download all bibliographic records (compressed file)](https://osu.box.com/s/ra8403wcr85j5lq6ekmpa4zdoqvyljuu); (~12 GB): Uncompressed: [Download all bibliographic records (uncompressed file)](https://osu.box.com/s/5zhgjxq7wrceznsm87camhry4vjxlcf8)

This data set includes ~12 million bibliographic records using the UTF8 character encoding.  This includes *only* the bibliographic data, but includes records from all available material types.  This file explicitly excludes authority data, specifically the classification, name, and subject authority data.  Additionally, this data set excludes one MAP record that was found to be invalid in the original LC dataset downloaded on 5/17/2017.  This data set was downloaded and processed on 05/17/2017.  You can download the excluded file (one record), here: https://osu.box.com/s/6l1zknju517picragw0v35u9iuuzptrk.  

MARCXML Data (~3.5 GB compressed; ~38 GB uncompressed): [Download all bibliographic records](https://osu.box.com/s/sj2xyccw2ncrxqwcsl3rtyhl1ey3jy9b)

This data set includes ~12 million bibliographic records in MARC21XML format. This includes *only* the bibliographic data, but includes records from all available material types.  This file explicitly excludes authority data, specifically the classification, name, and subject authority data.  Additionally, this data set excludes one MAP record that was found to be invalid in the original LC dataset downloaded on 5/17/2017.  This data set was downloaded and processed on 05/17/2017.

SQLite Database (~8.9 GB compressed; ~32 GB uncompressed): [Download all bibliographic records](https://osu.box.com/s/zmmojfl3k2iv4jbulna43d4irjrnn26z)

This data set includes ~12 million bibliographic records broken into 10 database tables. This includes *only* the bibliographic data, but includes records from all available material types.  This file explicitly excludes authority data, specifically the classification, name, and subject authority data.  Additionally, this data set excludes one MAP record that was found to be invalid in the original LC dataset downloaded on 5/17/2017.  The data in this database has not been optimized.  Users will want to create indexes on specific database columns if they want to query against the data. FYI -- this is the internal database format used by MarcEdit's local ILS option.  Users can attach this file to MarcEdit and then run queries directly against it.  But again, I'd first optimize the database.  This data set was downloaded and processed on 05/17/2017.

# Authority Data:

MARC Records (~1.3 GB compressed; ~5.5 GB uncompressed): [Download all authority records](https://osu.box.com/s/yzrw5jzqjcksynggusyflam5j75hma95)

This data set includes ~10 million authority records (its actually a shade under 10 million) in MARC format using the UTF8 character encoding.  This includes *only* the authority data, specifically all data found in the classification, name, and subject authority files.  This file explicitly excludes bibliographic data.  This data set was downloaded and processed on 05/17/2017.

MARCXML Records (~1.3 GB compressed; ~14.6 GB uncompressed): [Download all authority records](https://osu.box.com/s/jkf04k1hwlfw3mhgncehldwpdhged6kj)

This data set includes ~10 million authority records (its actually a shade under 10 million) in MARC21XML format using the UTF8 character encoding.  This includes *only* the authority data, specifically all data found in the classification, name, and subject authority files.  This file explicitly excludes bibliographic data.  This data set was downloaded and processed on 05/17/2017.


SQLite Database (~3.5 GB compreesed; ~12.8 GB uncompressed): [Download all authority records](https://osu.box.com/s/qh76cxphux369obll4r0bhhpmkqml0pe)

This data set includes ~10 million authority records (its actually a shade under 10 million) broken into 10 database tables. This includes *only* the authority data, specifically all data found in the classification, name, and subject authority files.  This file explicitly excludes bibliographic data.  The data in this database has not been optimized.  Users will want to create indexes on specific database columns if they want to query against the data. FYI -- this is the internal database format used by MarcEdit's local ILS option.  Users can attach this file to MarcEdit and then run queries directly against it.  But again, I'd first optimize the database. This data set was downloaded and processed on 05/17/2017.


# Data Processing
Data was processed using the following method:
* A MarcEdit plugin was created.  This plugin specifically reads the (http://www.loc.gov/cds/products/marcDist.php) website, downloading all data marked as UTF8.  The plugin separates data into two buckets:
1. bibliographic data
2. authority data
* Using the MARCJoin tool in MarcEdit, data files in each bucket were merged together.  This process takes ~1/2 minute per set.
* Using the MARCValidator, data was validated.  This tests only for structural issues that would prevent MARC tools from working with the data.  This process takes ~8 minutes per set.
* Data file creation:
1. Using the MARC SQL Explorer in MarcEdit, the SQLite database was created.  This process takes ~18 minutes
2. Using the MARC21=>MARCXML converter, the MARC data is created into MARCXML.  This process takes ~2 hours per file.
* Data is being hosted in my personal Ohio State University Box.net account.  All data should be downloadable via the specified links.

I'll plan on refreshing the data when it is updated.  Likewise, I'll likely use this page to provide links to other data outputs created from these datasets. 

# About the Data

This data is being made available by the U.S. Library of Congress for research purposes.  Data can be collected directly from the U.S. Library of Congress's Distribution Services site at: (http://www.loc.gov/cds/products/marcDist.php).  In fact, they have a lot more data than I've posted here -- they include data in MARC8 and MARCXML, and, for those that don't want to work with the large files, they do have each material type and set in 250,000 record segments.  I created these files mostly because I wanted a complete data dump.  

Also, please note, all data is being made available from the Library of Congress as Open-Access.  What does that mean, well, no specific license has been made available with the recordsets.  However, as a U.S. Federal Institution, data released by the Library of Congress, unless otherwise noted, typically falls into the Public Domain. This data is being shared under the same intent.

# Questions

If you have questions about the data -- you can ask, but I didn't do anything to the information outside of packaging it up and quickly validating it.  If there are data problems, you should probably contact LC.  If you have specific questions related to the collection and processes, feel free to let me know.

