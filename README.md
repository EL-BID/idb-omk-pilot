<img align="right" width="115" height="49" src="https://github.com/EL-BID/idb-omk-pilot/blob/master/IDB_logo.jpg"><img align="right" height="39" src="https://github.com/EL-BID/Building-Detection/blob/master/img/azavea_RGB_72dpi_trans_sm.png">


## IDB OpenMapKit Pilot                                                        
### Description and Context
---

OpenMapKit (OMK) allows users to complete data collection surveys in the field that contain geospatial information. In addition to an Android device, there are three software components that makes this possible:

- OMK Server
- OMK Survey App
- OpenDataKit (ODK) Collect App

Note that OMK Server is under continuous development. Currently deploying a functioning server involves many challenging technical steps.

### User Guide

#### Creating a survey

OMK adds geospatial data collection capabilities to [ODK surveys](https://docs.opendatakit.org/) by extending the [XLSForm standard](http://xlsform.org/en/) used by ODK for specifying surveys with OSM related fields.

OMK provides [documentation](http://openmapkit.org/docs_odkformsforomk.html) for creating a survey, as well as a sample survey [form](https://docs.google.com/spreadsheets/d/11H4-mGYTS61GLjSbVoTbmhoI5DjlF5fcBwNwQcvd2Go/edit#gid=0).

Once a survey form has been created, it needs to be uploaded to the OMK server. Login to the OMK administration dashboard, and click the "Upload Form" button in the header.

<img width="371" src="https://user-images.githubusercontent.com/1042475/54620928-4efa5580-4a3d-11e9-9f20-65a2c3418a95.png">

If the form does not contain any errors, you should see the following message.

<img width="1158" src="https://user-images.githubusercontent.com/1042475/54621169-b57f7380-4a3d-11e9-8ad9-ab277e46ab8b.png">

#### Filling out a survey

To fill out the survey you created, you must first point the ODK Collect App at the IDB OMK server. This can be set under the Server section of the General Settings menu.

<img src="https://user-images.githubusercontent.com/1014341/50118987-639d3680-021f-11e9-910d-a0509d9b4f76.png" width="300px">

Back on the app home screen, click the "Get Blank Form" button. This will download a list of all the forms available on the server. Once the list is populated, select the form you want and click "Get Selected". The form should now be downloaded to your device.

From the home screen, click "Fill Blank Form", and select the survey you would like to complete. The survey should now launch. Swipe left to proceed through the survey questions.

When you reach an OMK question in the survey, you will be prompted to launch the OMK app. The OMK questions are different than the other survey questions in that they involve adding a node to the map and filling out attributes about that node instead of just answering a question. When OMK opens, click the "Add Node" button (the round button with a "+"), and then click a spot on the map to add a point (lines and polygons are not supported). After the node is added, a form will appear with the OSM attributes that were specified in the survey.

<img src="https://user-images.githubusercontent.com/1014341/50118981-6304a000-021f-11e9-9dbe-50393f6b5d03.png" width="300px">

Fill in the relevant attributes by clicking on the form and swiping through each attribute. After you complete the geospatial components of the survey, click "Save to ODK Collect", and you'll be redirected back to the ODK app. Proceed through the rest of the survey.

When you finish the survey, you need to send the completed survey back to the OMK server. This step requires an internet connection. If you are without internet in the field, you can wait until you have a connection because the survey results are stored locally on your device. Once you have a connection, click the "Send Finalized Form" button on the ODK app home screen. Check any surveys that you have completed, and then click "Send Selected". The results of the survey will now be available on the server.

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

#### Offline Tiles

The OMK app can operate offline and show basemaps which have been copied to the device in the `mbtiles` format.
Prepare an `mbtiles` package by using the [HOT Export Tool](https://export.hotosm.org/) following [these directions](http://openmapkit.org/docs_creatingbasemaps.html)

Once generated, copy the `mbtiles` to your Android device and place in `/<storage>/openmapkit/mbtiles`. Do not put the `mbtiles` in a subfolder of that directory. They will then appear as an option on the OMK basemap selector. Since `mbtiles` are large, it may make sense to break them apart by zoom levels or geographic area when generating them.

Note that the ODK Collect app also has support for offline basemaps and uses the same mechanism. Copy the mbtiles to `/<storage>/odk/layers`. More complete instructions can be found [here](https://docs.opendatakit.org/collect-offline-maps/).

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

The Documentation of Support and Use of the software is licensed under Creative Commons IGO 3.0 Attribution-NonCommercial-NoDerivative (CC-IGO 3.0 BY-NC-ND)

The codebase of this repo uses [AM-331-A3 Software License](LICENSE.md).

### Limitation of responsibilities
---

The IDB is not responsible, under any circumstance, for damage or compensation, moral or patrimonial; direct or indirect; accessory or special; or by way of consequence, foreseen or unforeseen, that could arise:

I. Under any concept of intellectual property, negligence or detriment of another part theory; I

ii. Following the use of the Digital Tool, including, but not limited to defects in the Digital Tool, or the loss or inaccuracy of data of any kind. The foregoing includes expenses or damages associated with communication failures and / or malfunctions of computers, linked to the use of the Digital Tool.
