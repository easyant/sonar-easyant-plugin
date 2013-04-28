# Documentation ::  by sonarorg.apache.easyant.plugins
# Description

This module provides integration with sonar, a web based platform monitoring code quality.

# Example
```xml
<ea:plugin organisation="org.apache.easyant.plugins" module="sonar" revision="1.0"/>
```
Organisation attribute is optional. If not specified default one will be used.

```xml
<ea:plugin module="sonar" revision="1.0"/>
```

## Available targets

|target name|description|extension point|depends|
|-----------|-----------|---------------|-------|
|-sonar:subproject||||
|sonar:init-root-project|||sonar:init|
|sonar:sonar|||-sonar:root-project,-sonar:subproject|
|sonar:init||||
|-sonar:root-project|||sonar:init-root-project|

## Module parameters

### Properties

|property|description|required|default value|
|--------|-----------|--------|-------------|
|sonar.binaries|Comma-separated paths to directories containing binaries (in case of Java: directories with class files)|false|target/main/classes|
|sonar.language|Sets the language of source code. If a Sonar plugin allows to analyze another language, the associated source code analyser can be activated with this property. The default language can be set at instance level: go to Configuration - General Settings - General and set the sonar.language property|false|java|
|sonar.host.url|sonar server URL|false|http://localhost:9000|
|sonar.projectVersion|The project version|false|${ivy.revision}|
|sonar.profile|Sometimes, for security or other reasons, project sources must not be stored and displayed|false||
|sonar.jdbc.username|User for the JDBC Connection|false|sonar|
|sonar.sourceEncoding|Encoding of source files. Example of values: UTF-8, MacRoman, Shift_JIS. This property can be replaced by the standard property project.build.sourceEncoding in Maven projects. The list of available encodings depends on your JVM. See http://docs.oracle.com/javase/1.5.0/docs/guide/intl/encoding.doc.html|false||
|sonar.importSources|Sometimes, for security or other reasons, project sources must not be stored and displayed|false|true|
|sonar.sources|Comma-separated paths to directories containing sources|false|src/main/java|
|sonar.jdbc.password|Password for the JDBC Connection|false|sonar|
|sonar.surefire.reportsPath|Tell Sonar where your unit tests execution reports are: absolute or relative path to the directory containing your reports|false|target/test/xml|
|sonar.java.coveragePlugin|tell Sonar which code coverage engine has been used to generate the reports: jacoco or cobertura or emma or clover|false|jacoco|
|sonar.tests|Comma-separated paths to directories containing tests|false|src/test/java,src/integration-test/java|
|sonar.jdbc.url|JDBC Connection URL|false|jdbc:h2:tcp://localhost:9092/sonar|
|sonar.subproject.property.file|path to generated property file for sonar submodules|false|sonar.properties|
|sonar.dynamicAnalysis|Dynamic analysis relates to unit tests. By default, those unit tests are executed but you can optionally decide to do only static analysis or to reuse existing reports which have been previously generated. Possible values are true, false, reuseReports.|false|reuseReports|
|sonar.jdbc.driverClassName|JDBC Driver used by Sonar|false|org.h2.Driver|
|sonar.projectKey|The project key that is unique for each project.|false|${ivy.organisation}:${ivy.module}|
|sonar.projectName|Name of the project that will be displayed on the web interface|false|${sonar.projectKey}|
|sonar.subproject.property.regex|regex used to filter properties in generated ${sonar.subproject.property.file}|false|sonar.*|
