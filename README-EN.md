Visit the [Publication Guide](el-bid.github.io/guia-de-publicacion/) (currently available in Spanish) for more information about how to publish digital tools.
To learn more about the Code for Development initiative, visit: www.code.iadb.org

### IDB OpenMapKit Pilot
### Description and Context
---

OpenMapKit (OMK) allows users to complete data collection surveys in the field that contain geospatial information. In addition to an Android device, there are three software components that makes this possible:

- OMK Server
- OMK Survey App
- OpenDataKit (ODK) Collect App

### User Guide

#### Creating a survey

* XLSForm (Survey Format) http://xlsform.org/en/

#### Filling out a survey

* https://docs.opendatakit.org/

The client app must be configured to point to the IDB OMK server
<img src="https://user-images.githubusercontent.com/1014341/50118987-639d3680-021f-11e9-910d-a0509d9b4f76.png" width="250px">

When filling out the survey, any geospatial questions will launch OMK and be able to add nodes with attributes
<img src="https://user-images.githubusercontent.com/1014341/50118981-6304a000-021f-11e9-9dbe-50393f6b5d03.png" width="250px">

#### Survey administration

The page show surveys that were created
![screenshot from 2018-12-17 16 59 08](https://user-images.githubusercontent.com/1014341/50119006-6ef06200-021f-11e9-8e7f-f8f1b0c9032c.png)

And registered administrators can view submissions
![screenshot from 2018-12-17 17 09 52](https://user-images.githubusercontent.com/1014341/50119005-6ef06200-021f-11e9-96e1-16ae6b9334f6.png)

Finally, the forms are submitted to the server and the administrator can review and download the submissions
![screenshot from 2018-12-17 17 09 52](https://user-images.githubusercontent.com/1014341/50119005-6ef06200-021f-11e9-96e1-16ae6b9334f6.png)

This dashboard allows downloading in both GeoJSON and CSV formats.

### Installation Guide
---

Collecting data using OMK requires a running instance of OMK Server, as well as the OMK survey app and ODK Collect app Android apps.

#### OMK Server

The [HOT OSM fork](https://github.com/hotosm/OpenMapKitServer/) of the OMK Server is actively maintained and is recommended for use in collecting surveys outside of the POSM ecosystem.

OMK Server used a docker-based deployment, which limits the number of dependecies on the host machine, and can make the server easier to deploy.

To deploy it on an AWS EC2 instance, Azavea had to make changes to the Docker files, which are captured on [this branch](https://github.com/hotosm/OpenMapKitServer/compare/master...rbreslow:feature/jrb/add-compose-project). However, since these changes were made, the project maintainers have modified the project to be deployable with AWS Cloud Formation. They have also made functionality changes to the project. When attempting to deploy the project, it may make sense to use the `master` branch.

Once the server is setup and running, you should be able to access the OMK Server admin dashboard at `http://{host-url}/omk/pages/`.

#### Dependencies

OMK Server requires that Docker is available on the host machine. However, within the Docker container, the project depends on Node, Python, and Java.

### OMK Survey App

The OMK app can be installed via the [Play store](https://play.google.com/store/apps/details?id=org.redcross.openmapkit&hl=en_US).

### ODK Collect App

The ODK Collect app can be installed via the [Play store](https://play.google.com/store/apps/details?id=org.odk.collect.android).

### How to Contribute
---

Pull requests can be [submitted](https://github.com/hotosm/OpenMapKitServer/pulls) to the HOT OSM fork of OMK.

### Code of Conduct
---

### Authors
---

The OMK software was originally developed by the [POSM team](https://github.com/posm). The version referenced here is maintained by the [HOT OSM team](https://github.com/hotosm).

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
