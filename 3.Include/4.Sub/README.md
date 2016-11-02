# 4.Sub function library

4.Sub folder contains the important function library used by 1.Init.qvs during initiation. This library is loaded in during initiation (executing 99.LoadAll.qvs) and adds additional functionallity when creating load scripts in Qlik Sense/QlikView. Sub function documantation is avalible on community in the QDF development guide https://community.qlik.com/docs/DOC-5306.

- 99.LoadAll.qvs --> Auto loads all sub functions during initiation (by 1.Init.qvs)
- 1.FileExist.qvs --> Validates file(s) or folder(s) , can be used to avoid errors during script load due to missing content.
*call vL.FileExist('$(vG.QVDPath)\filename'); Variable vL.FileExist returns true or false.*
- 2.LoadVariableCSV.qvs --> Load variables stored in csv files into the Qlik Script. This file is used by 1.Init to load Custom Global Variables.
*call LoadVariableCSV('[My Variable File.csv]', [‘Search Tag’], [‘Container Prefix’], [‘Comments as variables’] [‘Container Map Mode’]);*
- 3.LoadContainerMap.qvs --> Load and validate Container Map csv file, this function is used internaly by other functions
sub LoadContainerMap(‘Container Map file’, ’Container name’, [' Optional $(vG.BasePath)']);
- 4.GenericContainerLoader.qvs --> Creates Global Variable links (mounts) to other containers based on the Container Map.
Call LCGV (‘Container Prefix’, [' Specific folder [;Additional folders separated by ;]);
- 5.DoDir.qvs --> Will index selected folder/file structure and return a table containing file name and path under selected file system.
Call DoDir (Scan Path, [Table Name], [Folders Only], [Single Folder], [Qualified Felds], [Hide QDF Templates])
- 6.CreateFolder.qvs --> create non existing folder or a folder structure. CreateFolder does not work in Qlik Sense without changing Engine to legacy mode.
sub CreateFolder (vL.FolderName)
- 7.CalendarGen.qvs --> Generic calendar generation script that enables scalable handling of creating and navigating multiple date fields
*CALL CalendarGen('Date Field',[ 'Calendar Table'] [,‘Months Left Fiscal Date’] [,‘Min Date’, ‘Max Date’][,’Link Table’][,’DateFormat’]); *
- 8.QVFileInfo.qvs --> Returns metadata (in table format) from Qlik files, at the moment QVW and QVD file formats. 
*Call QVFileInfo( 'Fully Qualified file Name',['Table Name']);*
- 9.QVDMigration.qvs --> Migrates and consolidates qvd data between containers, using fixed file names or wildcard (*) migrating a qvd folder in one single statement. 
*Call QVDMigration (QVD Source File, QVD Destination File, [Select specific fields (, separator) leave blank for all fields], [Scrambled fields (, separator)], [Table Name Suffix], [Include Subfolders], [Format-Spec], [No of Records]);*
- 10.QVDLoad.qvs --> Load up qvd files into a data model based on the meta-data headers in the qvd files.
*Call QVDLoad(QVD Repository, [Select specific fields (, separator) leave blank for all fields], [Scrambled fields (, separator)], [Table Name Suffix], [Include Subfolders], [No of Records]);*
- 11.DynamicContainerLoader.qvs --> Loads Global Variables within containers based on folder name.
*Call DynamicContainerGlobalVariables (‘Container Path Name’, ['Single Folder [; Additional folders separated by ;]'] , [’Override Prefix’] , [’Use Shared Folder Container Map’]);*
- 12.Index.qvs --> Index is functions that creates and maintains a set of indexes for Qlik Data files (QVD). These indexes are used when searching for data types across multiple qvd files this means that developers and power users select needed data using a simple command. 
-	 IndexAdd Will create the QVD indexes, should be done during qvd creation.
*Call IndexAdd([‘QVD path and name’],['Index folder name'] ,['Container name'] ,['Tags'] ,['Alternative Index path']);*                                                 
-  IndexLoad Loads Qlik data based on combination of index criteria’s like file name, tags, table, fiels…
*Call IndexLoad([‘QVD file name’],['Table Name'] ,['Index Folder Name'] ,['Tags'] ,['Fields'] ,['Index Only'] ,['Load Max Rows'] ,[ ['Alternative Index path'],[‘Load Expressions’]);*                                               
-	IndexDel Delete index and optionally referring qvd file.
*Call IndexDel(‘Index file name’,['Delete associated QVD files'] ,['Index Folder Name'] ,['Alternative Index path']);*
