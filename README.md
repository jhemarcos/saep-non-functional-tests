# Saep JMeter
=================================


[![Build Status](https://travis-ci.org/jhemarcos/saep-non-functional-tests.svg?branch=master)](https://travis-ci.org/jhemarcos/saep-non-functional-tests)

This project includes non functional tests for the SAEP system.

This project requires **JDK 1.7** or higher.

# Basic Usage
-----
### Run Tests

Clone or download this repository.

```
cd saep-non-functional-tests/saep-jmeter
mvn verify -Ptests
```


### Analyse Tests

View results:
```
cd saep-non-functional-tests/saep-jmeter/target/reports
```
* Open the index.html file with some browser.

![Index Results](http://i.imgur.com/TMiT6Hz.png)


* Find important data for your evaluation. For example:

![Important Results First](http://i.imgur.com/hxkYwnr.png)

![Important Results Second](http://i.imgur.com/gVut4lr.png)

![Important Results Thirdy](http://i.imgur.com/1jnmCFG.png)


* If you have set up more than one url, you can see detailed results here

![Other Results Thirdy](http://i.imgur.com/PNA5ClQ.png)


# Documentation
-----
### Configure pom.xml

#### Global Properties
These properties refer to all tests that will run.

|     Tag Name    | Group             | Description                                                | Default Value                             |
|:---------------:|-------------------|------------------------------------------------------------|-------------------------------------------|
| webapp.protocol | Global Properties | The protocol used by the application test target           | http                                      |
| webapp.host     | Global Properties |                   The host where the application is hosted |                       www.saep.inf.ufg.br |
| webapp.port     | Global Properties |            The application communication port on that host |                                        80 |
| webapp.uris     | Global Properties | The path where the uri files are to be tested on that host | ${project.basedir}/src/test/uris/uris.txt |

#### Test Properties
These properties are unique to each test. The key ${testTag} refers generically to any test.

|           Tag Name           | Group           | Description                                                       |
|:----------------------------:|-----------------|-------------------------------------------------------------------|
| ${testTag}.name              | Test Properties | The name of the thread group that runs that test                  |
| ${testTag}.numberOfThreads   | Test Properties |                       Number of threads required to run that test |
| ${testTag}.scheduledDelay    | Test Properties |                                Initial delay before starting test |
| ${testTag}.rampUp            | Test Properties |                          Interval in seconds to start each thread |
| ${testTag}.numberOfLoops     | Test Properties | Number of requests per thread                                     |
| ${testTag}.dataFile          | Test Properties | Url file specific to that test                                    |
| ${testTag}.scheduledDuration | Test Properties | Total test duration, even if all requests have not been finalized |

### Configure paths
You can configure more than one path for the requests. The total number of requests for that test group will be divided by the number of registered paths. To configure more paths, open the ```saep-non-functional-tests/saep-jmeter/src/test/uris/uris.txt``` as such and add the paths separated by line breaks. Ex.:

![Other Results Thirdy](http://i.imgur.com/UTh2N5u.png)
