Hadoop Plugin for New Relic
===============================

This plugin acts as a sink for the Hadoop Metrics2 framework, using the New Relic Plugin Java SDK.

## Getting Started

You can get this plugin up and running in your Hadoop environment in 5 easy steps.

#### 1. Download and extract the agent and supporting files onto your Hadoop server(s) 

The latest packaged (JAR) version of this agent can be found at this path and file name:
```
    https://github.com/sschwartzman/newrelic_hadoop_plugin.git
    bin/newrelic_hadoop_plugin.jar
```
The JSON Simple JAR is also needed to send metrics to New Relic:
```
https://code.google.com/p/json-simple/
https://json-simple.googlecode.com/files/json-simple-1.1.1.jar
```

#### 2. Add agent JARs to classpath

Add these JAR files to your Hadoop classpath, by either one of two ways:

 * Edit [hadoop_root]/confg/hadoop_env.sh and revise the classpath to include the  JARs:

  ```
  # Extra Java CLASSPATH elements.  Optional.
  export HADOOP_CLASSPATH=/[ext_path]/hadoop_newrelic_plugin.jar:/[ext_path]/json-simple-1.1.1.jar
  ```
OR

 * Add the JARs to the existing [hadoop_root]/lib directory, which should already be in the hadoop classpath.

#### 3. Add & edit the sink configuration

* The sink configuration is found in this plugin at conf/hadoop-metrics2.properties
* If you are not using any other metric sinks, you can simply backup the existing [hadoop_root]/conf/hadoop-metrics2.properties file and replace it with the one in this agent.
* If you are using other metric sinks, you can append the contents of this file to your existing hadoop-metrics2.properties file.

#### 4. Update the hadoop-metrics2.properties file to have your license key.
```
# Enter your license token here
*.sink.newrelic.nrlicensekey=[your_license_key_here]
```

#### 5. Restart your Hadoop processes... and that's it! 

## Notes:

* You can disable metrics for certain processes by editing hadoop-metrics2.properties. 
* You can also use the "debug" mode within hadoop-metrics2.properties. This will output metrics to the .out log file for that process rather than send them to New Relic, should you want to review the kinds of metrics that are being produced and if any are malformed.
* This plugin can be used to collect metrics from any custom "sources" you have defined in Metrics2. Minor updates to hadoop-metrics2.properties will be all that is required to get them.

## Further Reading

This is a good article detailing the Hadoop Metrics2 Framework:
http://blog.cloudera.com/blog/2012/10/what-is-hadoop-metrics2/
