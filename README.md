# HTTP Log Monitoring

This program monitors HTTP access log (https://www.w3.org/Daemon/User/Config/Logging.html).

## Installation

### Requirements

Minimum requirements to run the application is JRE 11

Use this [link](https://adoptopenjdk.net/installation.html?variant=openjdk11&jvmVariant=hotspot#x64_mac-jre) to install the jre.

## Usage

```bash
$ java -jar http-log-monitoring.jar --help

HTTP Log Monitoring Tool

Usage: <main class> [-DhV] [-d=NUM] [-f=FILE] [-i=NUM] [-t=NUM]
Prints usage help and version help when requested.

  -d, --alertDuration=NUM    The duration window (seconds) to analyse the alerts. (Default: 120)
  -D, --debug                Write debugging messages into the "http_log_monitoring.log" file.
  -f, --file=FILE            The HTTP access log file. (Default: /tmp/access.log)
  -h, --help                 Print usage help and exit.
  -i, --summaryInterval=NUM  The periodic interval (seconds) to compute summary. (Default: 10)
  -t, --alertThreshold=NUM   The threshold requests per seconds to trigger alerts. (Default: 10)
  -V, --version              Print version information and exit.
```

Below is the summary printed after every "summaryInterval"

```
SUMMARY
From {2019/Dec/10, 23:13:07} To {2019/Dec/10, 23:13:17}
Total Requests: 10
Total Bytes: 49860
Total Unique Users: 0
Hits per Section:
  /list=1
  /app=2
  /apps=2
  /posts=1
  /wp=3
  /explore=1
HTTP StatusCodes Counts:
  404=1
  200=9
```

Below is the alert triggered, if the requests per seconds in more than "alertThreshold" (defined over the period of "alertDuration")

```
High traffic generated an alert - hits = 28, triggered at 2019/Dec/10, 23:13:07
```

Recovery alert triggered when the requests per seconds drops below "alertThreshold".

```
Alert recovered at 2019/Dec/10, 23:13:55
```

## How to build

You require the following to build the source code:

    JDK 11
    Gradle


## License
[MIT](https://choosealicense.com/licenses/mit/)