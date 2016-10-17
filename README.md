# [Vangav Backend](http://www.vangav.com/)
### [back-the-end]

[vangav.com](http://www.vangav.com/)

# Intro

Vangav Backend is an open source (license-free) backend. vos (in vos_backend) stands for (vangav open source).

**As a REST service generator.** Vangav Backend can be used to generate REST services. When using Vangav Backend, one doesn't start by writing code. Instead the service's entry points (controllers) and databse tables/queries are defined in minimal json files and Vangav Backend's generators takes care of adding the majority of the code a service needs, while maintaining the highest performance and design quality we know how to do.

**As a commons lib.** Vangav Backend's can also be used as a commons library, so to utilize it built-in utilities (listed below) for any project.

+ **90+% less code:** Instead of writing so much code, Vangav Backend has built-in service code generator. Just write a minimal JSON definition of a new service's entry points (controllers) and database's tables/queries. Then using one command line `java -jar backend_generator.jar new my_new_service_name` Vangav Backend takes care of generating 90+% of the code needed for that new service.
+ **10-% of hello-world-logic:** The generated service adds TODOs where the user should add the service's logic. Usually few method calls with few if-conditions and/or loops.
+ **eclipse-ready:** The generated service's JAVA project is ready for import in eclipse.
+ **post-generation-config:** Modify the service's database config (add/remove/edit) then run one command line `java -jar cassandra_keyspaces_updater.jar`.
+ **built-in dispatcher/worker:** With dispatchable queries and push notifications.
+ **key built-in utilities:**
  + [compression](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/compression) algorithms
  + [content](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/content) formatting/checking/generation (CQL, JAVA, Phriction, ...)
  + [data structures and algorithms](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/data_structures_and_algorithms)
  + [exceptions](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/exceptions)
  + [file-operations](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/files)
  + [geo](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/geo) (geo grids, lite reverse geo coding and geo hashing)
  + [IDs](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/ids) (sequential ids, twitter snow flake and uuid operations)
  + [math/geometry](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/math)
  + [metrics](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/metrics) (distance/time)
  + **[email clients](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/networks)** (JAVA and mailgun), **[REST client](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/networks)** (sync/async)
  + **[public apis](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/public_apis)** (Facebook Graph API and car2go public API)
  + **[push notifications](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/push_notifications)** (android and ios)
  + **[authentication](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/security)** (Facebook, Google, OAuth2 and transaction tokens) **[cryptography](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/security)** (asymmetric, password hashing and two-way encryption)
  + built-in configurable [threadpools](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/thread_pool) and latch threads
  + **[Vangav M](http://www.vangav.com/)** deeply integrated

# Contents

+ [apache-cassandra-2.1.2](https://github.com/vangav/vos_backend/tree/master/apache-cassandra-2.1.2) is the cassandra's version used by Vangav Backend. Services generated using Vangav Backend automatically use this cassandra on dev mode. For prod mode refer to the "Deployement" section below.
+ [data](https://github.com/vangav/vos_backend/tree/master/data) hold's the data files included with Vangav Backend for optional use like the data for reverse geo coding.
+ [dist](https://github.com/vangav/vos_backend/tree/master/dist) contains Vangav Backend's lib (gets automatically copied into new services upon generation).
+ [lib](https://github.com/vangav/vos_backend/tree/master/lib) contains all the third-party libraries used by Vangav Backend.
+ [play-2.2.6](https://github.com/vangav/vos_backend/tree/master/play-2.2.6) is the play framework's version used by Vangav Backend. Each generated service comes with _scripts (_run, _compile, etc ...) that point to this directory for play framework. No need to do anything here.
+ [prop](https://github.com/vangav/vos_backend/tree/master/prop) contains all the mandatory/optional properties files used by services generated using Vangav Backend. Relevant properties files get automatically copied into newely generated service; optionally copy more properties files from here if needed for an additional optional feature.
+ **[src/com/vangav/backend](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend)** contains all Vangav Backend's source code. The whole code is license-free with minor exceptions put under packages called "third_party" like geo hashing.
+ **[tools_bin](https://github.com/vangav/vos_backend/tree/master/tools_bin)** contains `backend_generator.jar` which the exec responsible for generating new Vangav Backend services using the command `java -jar backend_generator.jar new my_new_service_name`.

+ **[vangav_backend_templates](https://github.com/vangav/vos_backend/tree/master/vangav_backend_templates)** contains functional templates for Vangav Backend's services.

# System Requirements

+ unix operating system (e.g.: mac os, ubuntu, etc ...)
+ JAVA 8
+ python 2.6 (only for using cassandra)

# Prerequisites

+ Basic JAVA
+ Basic Play Framework (optional for using Vangav Backend to build services)
+ Basic Cassandra/CQL (optional for using cassandra)

# Using Vangav Backend as a commons lib

+ Download **vos_backend.jar** from https://github.com/vangav/vos_backend/tree/master/dist and add it to your project's dependencies.
+ For some of the built-in utilities (e.g.: [email clients](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/networks), [push notifications](https://github.com/vangav/vos_backend/tree/master/src/com/vangav/backend/push_notifications), etc ...) more libraries need to be added to your project's dependencies; those libraries can be found at https://github.com/vangav/vos_backend/tree/master/lib

# Quick Start Example (vos_calculate_sum)

vos_calculate_sum is a service that takes two floats (a and b) request and returns a double (c) response representing the summation of a and b.

> Check out a finished version of this service at **https://github.com/vangav/vos_calculate_sum**

### Init
1. create a workspace directory "**my_services**" - this is the directory to contain both of vos_backend and all the services generated using it
2. download this (**vos_backend.zip**) project inside the workspace directory and unzip it
3. **rename** downloaded vos_backend-master to vos_backend

### Generate a new service
1. create a new directory "**my_services/vos_calculate_sum**"
2. **copy** **controllers.json** from vos_backend/vangav_backend_templates/vos_calculate_sum/ to the directory vos_calculate_sum created in (1)
3. open a terminal session and **cd** to my_services/vos_backend/tools/bin
4. execute the command **`java -jar backend_generator.jar new vos_calculate_sum`**
5. enter **`Y`** for using the config directory
6. enter **`Y`** to generate an eclipse-compatible project
7. enter **`N`** for generating a worker service

### Writing the service's logic code
+ open eclipse and **import** vos_calculate_sum project
+ double check the java version used for compiling the project. right click the project > properties > Java Compiler > Enable project specific settings > Compiler compliance level > 1.7 or 1.8
+ open class **HandlerCalculateSum.java** under package `com.vangav.vos_calculate_sum.controllers.calculate_sum`, method **processRequest** should be as follows
```java
  @Override
  protected void processRequest (final Request request) throws Exception {

    // use the following request Object to process the request and set
    //   the response to be returned
    RequestCalculateSum requestCalculateSum =
      (RequestCalculateSum)request.getRequestJsonBody();
    
    // set response's value
    ((ResponseCalculateSum)request.getResponseBody() ).set(
      requestCalculateSum.a + requestCalculateSum.b);
  }
```

### Start the service
1. **cd** to my_services/vos_calculate_sum
2. execute the command **`./_run.sh`**

### Try it out
1. open an internet browser page and type **`http://localhost:9000/calculate_sum?a=1.2&b=2.3`** - this returns 3.5
2. play with `a` and `b` values in the request string in (1)

### Stop the service
1. in the terminal session where you started the service press **`control + d`**

> **Voila, few minutes, few lines of code and the calculate_sum's backend is up and running. That's Vangav Backend.**

# Intermediate Example (vos_geo_server)

vos_geo_server is a service that takes a latitude/longitude request and returns the reverse geo code (continent, country, major city, city). It also keeps track of queried continents/countries to also provide lists of sorted top queried continents/countries.

> Check out a finished version of this service at **https://github.com/vangav/vos_geo_server**

### Init
1. create a workspace directory "**my_services**" - this is the directory to contain both of vos_backend and all the services generated using it
2. download this (**vos_backend.zip**) project inside the workspace directory and unzip it
3. **rename** downloaded vos_backend-master to vos_backend

### Generate a new service
1. create a new directory "**my_services/vos_geo_server**"
2. **copy** **controllers.json** and **gs_top.keyspace** from vos_backend/vangav_backend_templates/vos_geo_server/ to the directory vos_geo_server created in (1)
3. open a terminal session and **cd** to my_services/vos_backend/tools/bin
4. execute the command **`java -jar backend_generator.jar new vos_geo_server`**
5. enter **`Y`** for using the config directory
6. enter **`Y`** to generate an eclipse-compatible project
7. enter **`N`** for generating a worker service

### Init the service's cassandra database
1. **cd** to my_services/vos_geo_server/cassandra/cql/
2. execute the command **`./_start_cassandra.sh`** - to start cassandra
3. **cd** to my_services/vos_geo_server/cassandra/cql/drop_and_create/
4. execute the command **`./_execute_cql.sh gs_top_dev.cql`**

### Init service's data
1. **copy** the contents of the directory my_services/vos_backend/data/geo/reverse_geo_coding/ to my_services/vos_geo_server/conf/data/geo/reverse_geo_coding/

### Start the service
1. **cd** to my_services/vos_geo_server
2. execute the command **`./_run.sh`**

### Preliminary testing
1. open an internet browser page and type **`http://localhost:9000/reverse_geo_code?latitude=49&longitude=11`** - this returns an empty response

### Stop the service
1. in the terminal session where you started the service press **`control + d`**

### Writing the service's logic code
+ open eclipse and **import** vos_geo_server project
+ double check the java version used for compiling the project. right click the project > properties > Java Compiler > Enable project specific settings > Compiler compliance level > 1.7 or 1.8
+ under package **com.vangav.vos_geo_server** add a new package **common**
+ in the created package in the previous step add a new class **InitIndexInl** with the following implementation:
```java
package com.vangav.vos_geo_server.common;

import com.datastax.driver.core.ResultSet;
import com.vangav.vos_geo_server.cassandra_keyspaces.gs_top.NameIndex;

/**
 * InitIndexInl has inline static method to init Cassandra's gs_top.index
 *   table by inserting index_key values (continents and countries)
 * */
public class InitIndexInl {

  public static final String kContinentsIndexKey = "continents";
  public static final String kCountriesIndexKey = "countries";
  /**
   * initIndex
   * does first-run initialization for gs_top.index table
   * @throws Exception
   */
  public static void initIndex () throws Exception {
    
    ResultSet resultSet = NameIndex.i().executeSyncSelect(kContinentsIndexKey);
    
    if (resultSet.isExhausted() == true) {
      
      NameIndex.i().executeSyncInsert(kContinentsIndexKey);
    }
    
    resultSet = NameIndex.i().executeSyncSelect(kCountriesIndexKey);
    
    if (resultSet.isExhausted() == true) {
      
      NameIndex.i().executeSyncInsert(kCountriesIndexKey);
    }
  }
}
```
+ in **default_package/Global.java** after the following line
```java
Countries.loadTable();
```
add the following lines
```java
ReverseGeoCoding.load();
InitIndexInl.initIndex();
```
+ open class **HandlerReverseGeoCode.java**, method **processRequest** should be as follows
```java
  @Override
  protected void processRequest (final Request request) throws Exception {

    // use the following request Object to process the request and set
    //   the response to be returned
    RequestReverseGeoCode requestReverseGeoCode =
      (RequestReverseGeoCode)request.getRequestJsonBody();
    
    // get geo hash
    String geoHash =
      GeoHash.geoHashStringWithCharacterPrecision(
        requestReverseGeoCode.latitude,
        requestReverseGeoCode.longitude,
        12);
    
    // get reverse geo code
    ReverseGeoCode reverseGeoCode =
      ReverseGeoCoding.i().getReverseGeoCode(
        requestReverseGeoCode.latitude,
        requestReverseGeoCode.longitude);
    
    // set response
    ((ResponseReverseGeoCode)request.getResponseBody() ).set(
      requestReverseGeoCode.latitude,
      requestReverseGeoCode.longitude,
      geoHash,
      reverseGeoCode.getCity(),
      reverseGeoCode.getMajorCity(),
      reverseGeoCode.getCountryCode(),
      reverseGeoCode.getCountry(),
      reverseGeoCode.getContinentCode(),
      reverseGeoCode.getContinent() );
  }
```
+ then add the following method in class **HandlerReverseGeoCode.java**
```java
  @Override
  protected void afterProcessing (
    final Request request) throws Exception {

    // get request Object
    RequestReverseGeoCode requestReverseGeoCode =
      (RequestReverseGeoCode)request.getRequestJsonBody();
    
    // get reverse geo code
    ReverseGeoCode reverseGeoCode =
      ReverseGeoCoding.i().getReverseGeoCode(
        requestReverseGeoCode.latitude,
        requestReverseGeoCode.longitude);
    
    // update continents index
    NameIndex.i().executeAsyncUpdate(
      new HashSet<String>(Arrays.asList(reverseGeoCode.getContinent() ) ),
      InitIndexInl.kContinentsIndexKey);
    
    // update countries index
    NameIndex.i().executeAsyncUpdate(
      new HashSet<String>(Arrays.asList(reverseGeoCode.getCountry() ) ),
      InitIndexInl.kCountriesIndexKey);
    
    // update continents counter's value
    Continents.i().executeAsyncUpdateCounterValue(
      reverseGeoCode.getContinent() );
    
    // update countries counter's value
    Countries.i().executeAsyncUpdateCounterValue(
      reverseGeoCode.getCountry() );
  }
```
+ under package **top_continents** add class **ResponseTopContinent.java** with the following code
```java
package com.vangav.vos_geo_server.controllers.top_continents;

import com.fasterxml.jackson.annotation.JsonIgnore;
import com.fasterxml.jackson.annotation.JsonIgnoreProperties;
import com.fasterxml.jackson.annotation.JsonProperty;

/**
 * ResponseTopContinent represents the response's top-continent
 * */
@JsonIgnoreProperties(ignoreUnknown = true)
public class ResponseTopContinent {
  
  /**
   * Constructor ResponseTopContinent
   * @param continentName
   * @param continentCount
   * @return new ResponseTopContinent Object
   * @throws Exception
   */
  @JsonIgnore
  public ResponseTopContinent (
    String continentName,
    long continentCount) throws Exception {
    
    this.continent_name = continentName;
    this.continent_count = continentCount;
  }

  @JsonProperty
  public String continent_name;
  @JsonProperty
  public long continent_count;
}
```
+ modify class **ResponseTopContinents.java** to be as follows:
```java
package com.vangav.vos_geo_server.controllers.top_continents;

import com.fasterxml.jackson.annotation.JsonIgnore;
import com.fasterxml.jackson.annotation.JsonIgnoreProperties;
import com.fasterxml.jackson.annotation.JsonProperty;
import com.vangav.backend.play_framework.request.response.ResponseBodyJson;

/**
 * ResponseTopContinents represents the response's structure
 * */
@JsonIgnoreProperties(ignoreUnknown = true)
public class ResponseTopContinents extends ResponseBodyJson {

  @Override
  @JsonIgnore
  protected String getName () throws Exception {

    return "TopContinents";
  }

  @Override
  @JsonIgnore
  protected ResponseTopContinents getThis () throws Exception {

    return this;
  }

  @JsonProperty
  public ResponseTopContinent[] top_continents;
  
  @JsonIgnore
  public void set (ResponseTopContinent[] top_continents) {
    
    this.top_continents = top_continents;
  }
}
```
+ in class **HandlerTopContinents.java** method **processRequest** should be as follows:
```java
  @Override
  protected void processRequest (final Request request) throws Exception {
    
    // select continents from gs_top.index
    ResultSet resultSet =
      NameIndex.i().executeSyncSelect(InitIndexInl.kContinentsIndexKey);
    
    // no continents queried before?
    if (resultSet.isExhausted() == true) {
      
      ((ResponseTopContinents)request.getResponseBody() ).set(
        new ResponseTopContinent[0] );
      
      return;
    }
    
    // extract continents index
    Set<String> continentsIndex =
      resultSet.one().getSet(
        NameIndex.kIndexValuesColumnName,
        String.class);
    
    // init top continents
    ArrayList<Pair<String, Long> > topContinents =
      new ArrayList<Pair<String, Long> >();
    
    // for each continent
    for (String continent : continentsIndex) {
      
      // select continent's counter-value
      resultSet = Continents.i().executeSyncSelectCounterValue(continent);
      
      // no data? skip
      if (resultSet.isExhausted() == true) {
        
        continue;
      }
      
      // store continent name-counter pair
      topContinents.add(
        new Pair<String, Long>(
          continent,
          resultSet.one().getLong(Continents.kCounterValueColumnName) ) );
    }
    
    // sort results ascending
    Collections.sort(topContinents, new Comparator<Pair<String, Long> > () {

      @Override
      public int compare (Pair<String, Long> x, Pair<String, Long> y) {

        return Long.compare(x.getSecond(), y.getSecond() );
      }
    } );
    
    // reverse sorted results to put them in a descending order
    Collections.reverse(topContinents);
    
    // fill response array
    
    ResponseTopContinent[] responseArray =
      new ResponseTopContinent[topContinents.size() ];
    
    for (int i = 0; i < topContinents.size(); i ++) {
      
      responseArray[i] =
        new ResponseTopContinent(
          topContinents.get(i).getFirst(),
          topContinents.get(i).getSecond() );
    }
    
    // set response
    ((ResponseTopContinents)request.getResponseBody() ).set(responseArray);
  }
```
+ repeat the last 3 steps for countries

### Try it out
+ start the service as explained above then open an internet browser page and type any of
  + **`http://localhost:9000/reverse_geo_code?latitude=49&longitude=11`** - play around with the latitude and longitude values
  + **`http://localhost:9000/top_continents`**
  + **`http://localhost:9000/top_countries`**
+ stop the service as explained above

> **Voila, few minutes, few lines of code and the geo server's backend is up and running. That's Vangav Backend.**

# Generated REST Service Structure

> This section uses the vos_geo_server example, yet it's the same structure for all REST services generated using Vangav Backend.

### Scripts

The following scripts are generated for every Vangav Backend Service.

+ [_run.sh](https://github.com/vangav/vos_geo_server/blob/master/_run.sh) runs the service in dev mode.
+ [_clean.sh](https://github.com/vangav/vos_geo_server/blob/master/_clean.sh) cleans the service's build.
+ [_compile.sh](https://github.com/vangav/vos_geo_server/blob/master/_compile.sh) compiles the service.
+ [_debug.sh](https://github.com/vangav/vos_geo_server/blob/master/_debug.sh) run the service in debug mode. Debugging the code can happen in eclipse as explained later.
+ [_dist.sh](https://github.com/vangav/vos_geo_server/blob/master/_dist.sh) generates a production executable for the service to deploy it on the production server(s).

### [Conf](https://github.com/vangav/vos_geo_server/tree/master/conf)

The conf directory contains all the configuration files needed by the service during run-time.

+ [routes](https://github.com/vangav/vos_geo_server/blob/master/conf/routes) and [application.conf](https://github.com/vangav/vos_geo_server/blob/master/conf/application.conf) are used by play framework to define the servie's entry points and the service's configuration respectively.

+ [prop](https://github.com/vangav/vos_backend/tree/master/prop) contains all the service's properties files, some of these files gets added (and set) for a Vangav Backend generated service. Add more properties files as needed by copying them from Vangav Backend to your service then optionally set its properties' values.
  + [android_notification_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/android_notification_properties.prop) contains the properties needed to use the Android push notifications utility.
  + [apple_notification_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/apple_notification_properties.prop) contains the properties needed to use the iOS push notifications utility.
  + [cassandra_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/cassandra_properties.prop) contains the properties needed to use Cassandra. Like Cassandra's deployment topology, retries, consistency levels, etc...
  + [dispatcher_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/dispatcher_properties.prop) defines the worker-services deployment topology in order to use the service's dispatcher.
  + [facebook_graph_api_edge_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/facebook_graph_api_edge_properties.prop) contains the properties that controls how to fetch Facebook Graph API's edges. In the current state of Vangav Backend, requesting an edges fetches one page only; however all the tools needed to fetch more pages are provided and can be used externally.
  + [java_email_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/java_email_properties.prop) contains the properties needed to use the JAVA email utility.
  + [mail_gun_email_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/mail_gun_email_properties.prop) contains the properties needed to use the mailgun email utility.
  + [param_validator_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/param_validator_properties.prop) contains properties that controls how some of a request's params get validated.
  + [request_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/request_properties.prop). For each request a Vangav Backend Service receives, there are sequential steps that the request's processing can go through. Those steps can be switched on/off from this properties file.
  + [response_error_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/response_error_properties.prop). In case there's a BAD_REQUEST or an INTERNAL_SERVER_ERROR, Vangav Backend's Services return a JSON response containing the problem's details. This properties file controls which item(s) of the problem's details gets sent to the client making the failed request.
  + [thread_pool_properties.prop](https://github.com/vangav/vos_backend/blob/master/prop/thread_pool_properties.prop)

# REST Service Config Structure

When using Vangav Backend to generate a REST service, adding config files is optional but highly recommended as it saves the majority of the cost needed to implement the REST service. Config consists of one mandatory **controllers.json** file and zero-to-many database config files **keyspace_name.keyspace** (one file per database keyspace).

## controllers.json structure

Template:

```json
{
  "java_package": "",
  "check_source": false,
  "throttle": false,
  "validate_param": true,
  "authenticate": true,
  "after_response": true,
  "after_processing": true,
  "default_operations": false,
  "notifications": true,
  "analysis": false,
  "logging": false,

  "controllers": [
    {
      "is_preset": false,
      "name": "",
      "type": "POST",
      "request_params": [
        {
          "name": "",
          "type": "",
          "is_array": false,
          "optionality": "MANDATORY"
        }
      ],
      "response_type": "JSON",
      "response_params": [
        {
          "name": "",
          "type": "",
          "is_array": false
        }
      ]
    }
  ]
}
```

# Community

[Facebook Group: Vangav Open Source - Backend](http://www.fb.com/groups/575834775932682/)

[Facebook Page: Vangav](http://www.fb.com/vangav.f)

Third party communities for Vangav Backend
- play framework
- cassandra
- datastax

> Tag your question online (e.g.: stack overflow, etc ...) with **#vangav_backend** to easier find questions/answers online.

# Dependencies

> These dependencies are already included in Vangav Backend. That's just FYI.

- [play framework](http://www.playframework.com) for web framework
- [Apache Cassandra](http://www.cassandra.apache.org/) for database
- [datastax](http://www.datastax.com/) for JAVA cassandra driver

# Hassle-Free

Vangav Backend is license-free because we know that starting a startup or developing a new service is already mission-impossible. You already got more than enough to worry about, Vangav Backend doesn't want to be one of those things you worry about.
> "Keep going, never give up".

Have fun!
