# yagcil-server: Data Crawling
This document describes how data crawling from Melange API is done in **yagcil-server**.

## Recrawling
The data is recrawled:

* for the **active year**: every hour (**TODO(poxip):** Set up CRON on OpenShift)
* for **others (archive)**: only once

### Recrawling procedure
#### For every year
1. Get all the orgs available for the year which is crawled (https://www.google-melange.com/gci/org/list/public/google/gciYEAR?fmt=json).
2. Get all closed tasks for every org from the point no. 1 (http://www.google-melange.com/gci/org/google/gciYEAR/ORGNAME?fmt=json&limit=1000&idx=1).
3. Store every task as a **Task** MongoEngine model.
