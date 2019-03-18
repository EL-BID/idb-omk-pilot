Visit the [Publication Guide](el-bid.github.io/guia-de-publicacion/) (currently available in Spanish) for more information about how to publish digital tools.
To learn more about the Code for Development initiative, visit: www.code.iadb.org

### IDB OMK Pilot
### Description and Context
---

OpenMapKit pilot implementation for IDB

### User Guide

#### Server
An OMK server has been setup using a HOT OSM Fork:
* https://github.com/hotosm/OpenMapKitServer/

Additional changes had to be made to get it operating successfully on our EC2 instance
* https://github.com/hotosm/OpenMapKitServer/compare/master...rbreslow:feature/jrb/add-compose-project

Administrators can access the site at
* http://idb-omk.azavea.com/omk/pages/#/

The page show surveys that were created
![screenshot from 2018-12-17 16 59 08](https://user-images.githubusercontent.com/1014341/50119006-6ef06200-021f-11e9-8e7f-f8f1b0c9032c.png)

And registered administrators can view submissions
![screenshot from 2018-12-17 17 09 52](https://user-images.githubusercontent.com/1014341/50119005-6ef06200-021f-11e9-96e1-16ae6b9334f6.png)

#### Client App
Two Android apps must be installed
* OpenMapKit: https://play.google.com/store/apps/details?id=org.redcross.openmapkit&hl=en_US
* OpenDataKit Collect: https://play.google.com/store/apps/details?id=org.odk.collect.android

The client app must be configured to point to the IDB OMK server
![screenshot_20181217-165213](https://user-images.githubusercontent.com/1014341/50118987-639d3680-021f-11e9-910d-a0509d9b4f76.png)

When filling out the survey, any geospatial questions will launch OMK and be able to add nodes with attributes
![screenshot_20181217-165324](https://user-images.githubusercontent.com/1014341/50118981-6304a000-021f-11e9-9dbe-50393f6b5d03.png)

Finally, the forms are submitted to the server and the administrator can review and download the submissions
![screenshot from 2018-12-17 17 09 52](https://user-images.githubusercontent.com/1014341/50119005-6ef06200-021f-11e9-96e1-16ae6b9334f6.png)

This dashboard allows downloading in both GeoJSON and CSV formats.

#### Documentation
* OMK https://docs.opendatakit.org/
* XLSForm (Survey Format) http://xlsform.org/en/

### Installation Guide
---

#### Dependencies

### How to Contribute
---

### Code of Conduct
---

### Authors
---

### Additional Information
---

### License
---

[AM-331-A3 Licencia de Software](LICENSE.md)

### Limitation of responsibilities
---

The IDB is not responsible, under any circumstance, for damage or compensation, moral or patrimonial; direct or indirect; accessory or special; or by way of consequence, foreseen or unforeseen, that could arise:

I. Under any concept of intellectual property, negligence or detriment of another part theory; I

ii. Following the use of the Digital Tool, including, but not limited to defects in the Digital Tool, or the loss or inaccuracy of data of any kind. The foregoing includes expenses or damages associated with communication failures and / or malfunctions of computers, linked to the use of the Digital Tool.
