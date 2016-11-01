# Qlik-Deployment-Framework (QDF)
QDF Development version 1.6.5

# QDF is a set of Qlik scripts and utilities that enables: 
Resource Sharing, Reuse, Organization, Structure and Standards providing an effective and efficient Qlik deployment.
Qlik-Deployment-Framework content is avalibla under https://community.qlik.com/groups/qlikview-deployment-framework/overview

# Qlik Deployment Framework resource containers
QDF is based on a resource container architecture, arrange containers (building blocks and security separators) to fit the current needs, when demand changes its easy to reorganize and add additional containers. QlikView and/or Qlik Sense applications are hooked into the containers in which all needed resources are resided.

# Qlik-Deployment-Framework GitHub repository
Qlik-Deployment-Framework GitHub repository contains Qlik Script code that resides inside each QDF container, not the complete container.
# Qlik-Deployment-Framework GitHub content:
- Version1.6.5.txt --> File containing version number and code modifications
- InitLink.qvs --> Initiation script that links Qlik Sense/QlikView to 1.Init.qvs
- 3.Include/1.BaseVariable/1.Init.qvs --> Main initiation script for both Qlik Sense and QlikView (run automatically by InitLink.qvs).InitLink will validate and create global variables for the current environment.
- 3.Include/1.BaseVariable/3.SystemVariables.qvs --> Only for QlikView, loads system variables (filepath to logs and more)
- 3.Include/2.Locale --> contains locale files used during initiation
- 3.Include/4.Sub/  --> contains most important function library, 
