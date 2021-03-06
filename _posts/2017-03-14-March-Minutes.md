---
layout: post
title: "March 2017 Meetup Minutes"
date: 2017-03-14
---
The agenda for this meeting was a "free for all", where we each shared our own QGIS topics. 

* Robert Catherman showed a report he read about damming the Mekong river in Vietnam which included no maps, and showed maps he had made with QGIS to illustrate the information included in that report.
    * Robert found the dams in Wikipedia, but also was able to locate the dams by following the river on aerial photography available in Google earth.
    * Robert made a map with the river, country boundaries and the locations of dams.
    * Robert also made a map showing the extent of saltwater intrusion, to illustrate the problem this was causing to agricultural production.
        * Many farmers are replacing rice paddies with shrimp farming and others with mango orchards.
* Andrew demonstrated an alternative method to compute the nearest neighbor.
    * Using the [refFunctions](https://plugins.qgis.org/plugins/refFunctions/) plugin.
    * refFunctions adds several new geometry related functions to the field calculator interface in a function group named "Reference".
        * Basic topological geometry relationships including:
            * intersecting_geom_count - count of intersecting geometry features
            * geomnearest - specify a layer and a field
            * geomdistance - can set maximum distance to search for
    * Example problem: culvert points do not line up with the desired stream network for analysis.
        * QGIS allows you to update the geometry from the field calculator, so you can snap the point to the location you want without running another tool.
            * Use several nested functions
                * The innermost function is geomdistance. Use $geometry for the field and streams for the layer as parameters. That will return the geometry of the closest stream as WellKnownText. $distance is another useful value to use in this function.
                * Use that value as the parameter for geom_from_wkt.
                * Use that value and the geometry of the culvert point ($geometry) as parameters for closest_point. 
            * Select <geometry> as the output of the expression.
    * In QGIS 2.14 they added default values. You can create fields for township and range, and then set their default values to field calculator expressions that use the intersect function to automatically populate the values from an existing polygon layer as features are added by a user.
* Clifford Snow has been manually digitizing land use features in Skagit Valley on OpenStreetMap.
    * He's done farmland interpretation from aerial photography, which has gone pretty well.
    * He decided to also digitize forested areas, but that is much more work so he wants to automate the process.
        * He is getting LANDSAT-8 and SENTINEL-2 data from [LandViewer](https://lv.eosda.com/). You can preview the imagery that meets your requirements. Pick imagery by:
            * time period
            * percent cloud cover
            * bounding box with 8 or fewer vertices
            * which specific bands you want
        * He is using the [Semi-Automatic Classification Plugin](https://fromgistors.blogspot.com/p/semi-automatic-classification-plugin.html) to detect the forest cover.
    * Robert suggested Clifford look at [Global Forest Watch](http://www.globalforestwatch.org/) to see if what they have done would work for his purposes.
* Evan Derickson shared [Open Aerial Map](https://openaerialmap.org/).
    * There is not much available in Washington State. People who have data should load it.
    * There is a cool very high resolution data set for part of Luther Burbank Park on Mercer Island.
* Andrew shared [Washington Lidar portal](http://lidarportal.dnr.wa.gov/)
    * An interesting source of elevation data.
* Stu Smith demonstrated how to read and write to [Esri File GeoDB](http://desktop.arcgis.com/en/arcmap/10.3/manage-data/administer-file-gdbs/file-geodatabases.htm).
    * By default in QGIS you can open them read-only.
        * Add vector layer -> source type = Directory -> OpenFileGDB.
    * There is another option: ESRI file GeoDB
        * Stu supplied [his notes](/downloads/How_to_create_and_edit_FGDB_in _QGIS.doc) on how to install the function and navigate some of the pitfalls. Stu gave credit to [GIS Stack Exchange](https://gis.stackexchange.com/) where he found much of the information that he has collected here.
        * You can save to this format. There is some tricky business in entering the name documented in Stu's notes.
        * You can create and use existing Feature Datasets
        * You can create and use existing GeoDBs
        * Stu installs using [OSGeo4W](https://trac.osgeo.org/osgeo4w/). He does the default install then goes back and installs this one additional package.
            * Andrew pointed out that there are instructions for Mac and Linux available but none of us have tried it after reading trough the instructions.
* Evan asked Stu if he ever figured out SpatiaLite and GeoPackages.
    * Stu has problems with it on his windows surface.
* Andrew pointed out there is a [QGIS mailing list](https://www.qgis.org/en/site/getinvolved/mailinglists.html) that can be used to ask questions.
* Paul mentioned WAURISA 2017 conference and [CUGOS](http://cugos.org/) Spring Fling are coming up in May, and looking for work shops.
    * Anyone interested in doing a QGIS workshop at the CUGOS Spring Fling can [contact the organizers](mailto:hello@cugos.org)
* Evan was already signed up to do a QGIS workshop at The [2017 Washington GIS Conference](http://www.waurisa.org/conferences/2017_Conference_Index.php) and looking for interesting things to cover.
    * Evan is considering a theme of creating a park map, but has also considered a zombie themed map excercise.
    * Andrew suggested forms and customizing them with images and web links to create a front end for data entry.
    * Stu suggested covering the time manager capability to show off the power and ability of Open Source software to the largely commercial software oriented group. Added that someone could show a time manger video as part of a presentation or lightning talk.
    * Clifford referred him to a 4 hour workshop from Boundless to look at.
* Robert mentioned that UW has come out with an free online course [GIS for Health Researchers](http://us8.campaign-archive2.com/?u=e682402ff461b79bf8c2d128e&id=b7cdc621c9) based on QGIS. 
* Andrew mentioned a QGIS cource is available at [Lynda.com](https://www.lynda.com/) which is available through the [Seattle Library](https://www.spl.org/about-the-library/library-news-releases/lyndacom-319).