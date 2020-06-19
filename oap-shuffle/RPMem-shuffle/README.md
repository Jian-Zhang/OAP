#  Shuffle Remote Persistent Memory Extension for Spark
Shuffle Remote Persistent Memory Extension (RPMem shuffle extension for short), previously Spark-PMoF (Persistent Memory over Fabric), is a Spark Shuffle Plugin which enables persistent memory and high performance fabric technology like RDMA for Spark shuffle to improve Spark performance in shuffle intensive scneario. 

## Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)

* [Guide](./doc/RPMem_shuffle_enabling_guide.md)

## Introduction

## Installation
Make sure you got [HPNL](https://github.com/Intel-bigdata/HPNL) installed. Please refer to the enabling guide in doc for other dependencies. 

```shell
git clone https://github.com/Intel-bigdata/oap.git
cd oap/oap-shuffle/RPMem-shuffle; mvn package
```


## Usage
For detail instructions on how to deploy and test RPMem shuffle extension, please refer to the enabling guide in the doc folder. 
This plugin current supports Spark 2.3 and works well on various Network fabrics, including Socket, **RDMA** and **Omni-Path**. Before runing Spark workload, add following contents in spark-defaults.conf, then have fun! :-)

```shell
spark.driver.extraClassPath Spark-PMoF-PATH/target/sso-0.1-jar-with-dependencies.jar
spark.executor.extraClassPath Spark-PMoF-PATH/target/sso-0.1-jar-with-dependencies.jar
spark.shuffle.manager org.apache.spark.shuffle.pmof.RdmaShuffleManager
```

