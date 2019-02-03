[![license](https://img.shields.io/github/license/RedisTimeSeries/JRedisTimeSeries.svg)](https://github.com/RedisTimeSeries/JRedisTimeSeries)
[![CircleCI](https://circleci.com/gh/RedisTimeSeries/JRedisTimeSeries/tree/master.svg?style=svg)](https://circleci.com/gh/RedisTimeSeries/JRedisTimeSeries/tree/master)
[![GitHub issues](https://img.shields.io/github/release/RedisTimeSeries/JRedisTimeSeries.svg)](https://github.com/RedisTimeSeries/JRedisTimeSeries/releases/latest)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.redislabs/jredistimeseries/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.redislabs/jredistimeseries)
[![Codecov](https://codecov.io/gh/RedisTimeSeries/JRedisTimeSeries/branch/master/graph/badge.svg)](https://codecov.io/gh/RedisTimeSeries/JRedisTimeSeries)

# JRedisTimeSeries
Java Client for RedisTimeSeries

### Official Releases

```xml
  <dependencies>
    <dependency>
      <groupId>com.redislabs</groupId>
      <artifactId>jredistimeseries</artifactId>
      <version>0.0.1</version>
    </dependency>
  </dependencies>
```

### Snapshots

```xml
  <repositories>
    <repository>
      <id>snapshots-repo</id>
      <url>https://oss.sonatype.org/content/repositories/snapshots</url>
    </repository>
  </repositories>
```

and

```xml
  <dependencies>
    <dependency>
      <groupId>com.redislabs</groupId>
      <artifactId>jredistimeseries</artifactId>
      <version>0.1.0-SNAPSHOT</version>
    </dependency>
  </dependencies>
```


# Example: Using the Java Client

```java
   Pool<Jedis> pool = ...
   RedisTimeSeries rts = new RedisTimeSeries(pool);
   
   rts.create("cpu1", 60*10 /*10min*/, 100, null);
   
   rts.create("cpu1-avg", 60*10 /*10min*/, 100, null);
   rts.createRule("cpu1", Aggregation.AVG, 60 /*1min*/, "cpu1-avg");
   
   rts.add("cpu1", -1 /*server time*/, 80, null);
```
