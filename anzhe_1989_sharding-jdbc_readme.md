# Sharding-JDBC - JDBC driver for shard databases and tables 

# [中文主页](http://dangdangdotcom.github.io/sharding-jdbc)

[![Build Status](https://secure.travis-ci.org/dangdangdotcom/sharding-jdbc.png?branch=master)](https://travis-ci.org/dangdangdotcom/sharding-jdbc)
[![Maven Status](https://maven-badges.herokuapp.com/maven-central/com.dangdang/sharding-jdbc/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.dangdang/sharding-jdbc)
[![Coverage Status](https://coveralls.io/repos/dangdangdotcom/sharding-jdbc/badge.svg?branch=master&service=github)](https://coveralls.io/github/dangdangdotcom/sharding-jdbc?branch=master)
[![GitHub release](https://img.shields.io/github/release/dangdangdotcom/sharding-jdbc.svg)](https://github.com/dangdangdotcom/sharding-jdbc/releases)
[![Hex.pm](http://dangdangdotcom.github.io/sharding-jdbc/img/license.svg)](http://www.apache.org/licenses/LICENSE-2.0.html)

# Overview

Sharding-JDBC is a JDBC extension, provides distributed features such as sharding, read/write splitting and BASE transaction.

# Features

## 1. Sharding
* Aggregation functions, group by, order by and limit SQL supported in distributed database.
* Join (inner/outer) query supported.
* Sharding operator `=`, `BETWEEN` and `IN` supported.
* Sharding algorithm customization supported.
* Hint supported.

## 2. Read/Write Splitting
* Same transaction data concurrency guarantee.
* Hint supported.

## 3. BASE Transaction
* Best efforts delivery transaction.
* Try confirm cancel transaction (TBD).

## 4. Compatibility
* ORM self-adapting. JPA, Hibernate, Mybatis, Spring JDBC Template or JDBC supported.
* Connection-pool self-adapting. DBCP, C3P0, BoneCP, Druid supported.
* Any Database supported theoretically. Support MySQL, Oracle, SQLServer and PostgreSQL.

## 5. Configuration
* Java config
* Spring namespace
* YAML
* Inline expression

## 6. ID Generation
* Distributed Unique Time-Sequence Generation

# Architecture

![Architecture](http://dangdangdotcom.github.io/sharding-jdbc/img/architecture_en.png)

# [Release Notes](https://github.com/dangdangdotcom/sharding-jdbc/releases)

# [Roadmap](ROADMAP.md)

# Quick Start

## Add maven dependency

```xml
 
 
     com.dangdang 
     sharding-jdbc-core 
     ${latest.release.version} 
 

 
```

## Rule configuration

```java
ShardingRule shardingRule = ShardingRule.builder()
        .dataSourceRule(dataSourceRule)
        .tableRules(tableRuleList)
        .databaseShardingStrategy(new DatabaseShardingStrategy("sharding_column", new XXXShardingAlgorithm()))
        .tableShardingStrategy(new TableShardingStrategy("sharding_column", new XXXShardingAlgorithm())))
        .build();
```

## Use raw JDBC API

```java
DataSource dataSource = ShardingDataSourceFactory.createDataSource(shardingRule);
String sql = "SELECT i.* FROM t_order o JOIN t_order_item i ON o.order_id=i.order_id WHERE o.user_id=? AND o.order_id=?";
try (
        Connection conn = dataSource.getConnection();
        PreparedStatement preparedStatement = conn.prepareStatement(sql)) {
    preparedStatement.setInt(1, 10);
    preparedStatement.setInt(2, 1001);
    try (ResultSet rs = preparedStatement.executeQuery()) {
        while(rs.next()) {
            System.out.println(rs.getInt(1));
            System.out.println(rs.getInt(2));
        }
    }
}
```

## Use spring namespace

```xml
 
 
     
    
     
         
         
         
         
     
     
         
         
         
         
     

     
     
     
         
             
                 
                 
             
             
         
     
 
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)