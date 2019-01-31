# WIS Datahub Setup

This document details out the setup instructions for the datahub development environment setup.

### Pre-Requisites
* JDK 1.8 latest patch
* Apache Maven 3.5.x
* Apache Tomcat 7.x


### Setup Steps
#### 1. Install Maven
   * Download maven archive from [Maven Download](https://archive.apache.org/dist/maven/maven-3/3.5.0/binaries/)
   * Unarchive the maven package to a local disk location
   * Setup the `M2_HOME` environment variable ponting to the maven installation location.
   * Add the `$M2_HOME/bin` (For Windows `%M2_HOME%\bin`) to the `path` variable.
   * Validate the maven installation by opening the commnd prompt / console and by typing the command `mvn --version`
#### 2. Checkout the code
   * Take the latest code from repository and go to the directory `Hybris\datahub\datahub-new\wis-datahub\`

#### 3. Install the pre-requisite artifacts to maven
   * For windows, execute the command `setup.bat`
   * For Unix/OSX, execute the command `sh setup.sh`

#### 4. Build the project
   * Copy the environment specific `local.properties` and `encryption-key.txt` files to `wis-datahub/datahub-overlay/src/main/resources/`
   * Execute the command `mvn clean install`
   * The deployable `datahub-webapp.war` file is created at `wis-datahub/datahub-overlay/target/`

#### 5. Setup Apache Tomcat Server for Datahub
   * Download & Install apache tomcat from  [Apache Tomcat 7.x](https://tomcat.apache.org/download-70.cgi)
   * Copy all the files from `wis-datahub/dependencies/` to `<TOMCAT>/lib/`
   
### Deploying datahub to tomcat
   To deploy datahub to tomcat, do following:
   * Stop tomcat if running
   * Copy `wis-datahub/datahub-overlay/target/datahub-webapp.war` to `<Tomcat>/webapps`
   * Start tomcat
   
### Validating datahub running status
   After starting the tomcat - 
   * Try hitting the URL `http://localhost:8080/datahub-webapp/v1/status` in browser
   * This should show as `Running` in the browser.

