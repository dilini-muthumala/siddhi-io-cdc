Siddhi IO CDC
===================

  [![Jenkins Build Status](https://wso2.org/jenkins/job/siddhi/job/siddhi-io-cdc/badge/icon)](https://wso2.org/jenkins/job/siddhi/job/siddhi-io-cdc/)
  [![GitHub Release](https://img.shields.io/github/release/siddhi-io/siddhi-io-cdc.svg)](https://github.com/siddhi-io/siddhi-io-cdc/releases)
  [![GitHub Release Date](https://img.shields.io/github/release-date/siddhi-io/siddhi-io-cdc.svg)](https://github.com/siddhi-io/siddhi-io-cdc/releases)
  [![GitHub Open Issues](https://img.shields.io/github/issues-raw/siddhi-io/siddhi-io-cdc.svg)](https://github.com/siddhi-io/siddhi-io-cdc/issues)
  [![GitHub Last Commit](https://img.shields.io/github/last-commit/siddhi-io/siddhi-io-cdc.svg)](https://github.com/siddhi-io/siddhi-io-cdc/commits/master)
  [![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

The **siddhi-io-cdc extension** is an extension to <a target="_blank" href="https://wso2.github.io/siddhi">Siddhi</a> that captures change data from databases such as MySQL, MS SQL, PostgreSQL, H2 and Oracle.

For information on <a target="_blank" href="https://siddhi.io/">Siddhi</a> and it's features refer <a target="_blank" href="https://siddhi.io/redirect/docs.html">Siddhi Documentation</a>. 

## Download

* Versions 3.x and above with group id `io.siddhi.extension.*` from <a target="_blank" href="https://mvnrepository.com/artifact/io.siddhi.extension.io.cdc/siddhi-io-cdc/">here</a>.
* Versions 2.x and lower with group id `org.wso2.extension.siddhi.*` from <a target="_blank" href="https://mvnrepository.com/artifact/org.wso2.extension.siddhi.io.cdc/siddhi-io-cdc">here</a>.

## Latest API Docs 

Latest API Docs is <a target="_blank" href="https://siddhi-io.github.io/siddhi-io-cdc/api/2.0.2">2.0.2</a>.

## Features

* <a target="_blank" href="https://siddhi-io.github.io/siddhi-io-cdc/api/2.0.2/#cdc-source">cdc</a> *(<a target="_blank" href="http://siddhi.io/en/v5.1/docs/query-guide/#source">Source</a>)*<br> <div style="padding-left: 1em;"><p>The CDC source receives events when change events (i.e., INSERT, UPDATE, DELETE) are triggered for a database table. Events are received in the 'key-value' format.<br>The key values of the map of a CDC change event are as follows.<br>&nbsp;&nbsp;&nbsp;&nbsp;For insert: Keys are specified as columns of the table.<br>&nbsp;&nbsp;&nbsp;&nbsp;For delete: Keys are followed followed by the specified table columns. This is achieved via 'before_'. e.g., specifying 'before_X' results in the key being added before the column named 'X'.<br>&nbsp;&nbsp;&nbsp;&nbsp;For update: Keys are followed followed by the specified table columns. This is achieved via 'before_'. e.g., specifying 'before_X' results in the key being added before the column named 'X'.<br>For 'polling' mode: Keys are specified as the coloumns of the table.<br>See parameter: mode for supported databases and change events.</p></div>


## Dependencies 
JDBC connector jar should be added to the runtime. Download the JDBC connector jar based on the database type that is being used.

For MySQL, use connector version 5.1.xx.

In addition to that, there are some prerequisites that need to be met based on the CDC mode used. Please find them below.

**Default mode (Listening mode):**

Currently MySQL, PostgreSQL and SQLServer are supported in Listening Mode.
To capture the change events, databases have to be configured as shown below.

* MySQL - https://debezium.io/docs/connectors/mysql/#setting-up-mysql
* PostgreSQL - https://debezium.io/docs/connectors/postgresql/#setting-up-PostgreSQL
* SQLServer - https://debezium.io/docs/connectors/sqlserver/#setting-up-sqlserver

**Polling mode:**

* Change data capturing table should be have a polling column. Auto Incremental column or Timestamp can be used.

Please see API docs for more details about change data capturing modes.

## Installation

For installing this extension on various siddhi execution environments refer Siddhi documentation section on <a target="_blank" href="https://siddhi.io/redirect/add-extensions.html">adding extensions</a>.

## Running Integration tests in docker containers(Optional)

The CDC functionality are tested with the docker base integration test framework.
The test framework initialize a docker container with required configuration before execute the test suit.

**Start integration tests**

 1. Install and run docker

 2. To run the integration tests, navigate to the siddhi-io-cdc/ directory and issue the following commands.

    * H2 default:

            mvn clean install

    * MySQL 5.7:

             mvn verify -P local-mysql -Dskip.surefire.test=true

    * Postgres 9.6:

             mvn verify -P local-postgres -Dskip.surefire.test=true

    * MSSQL:

             mvn verify -P local-mssql -Dskip.surefire.test=true

    * Oracle 11.2.0.2-xe:

             mvn verify -P local-oracle -Dskip.surefire.test=true

## Support and Contribution

* We encourage users to ask questions and get support via <a target="_blank" href="https://stackoverflow.com/questions/tagged/siddhi">StackOverflow</a>, make sure to add the `siddhi` tag to the issue for better response.

* If you find any issues related to the extension please report them on <a target="_blank" href="https://github.com/siddhi-io/siddhi-execution-string/issues">the issue tracker</a>.

* For production support and other contribution related information refer <a target="_blank" href="https://siddhi.io/community/">Siddhi Community</a> documentation.

