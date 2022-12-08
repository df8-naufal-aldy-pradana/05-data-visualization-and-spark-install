
## Linux

Here we'll show you how to install Spark 3.0.3 for Linux.
We tested it on Ubuntu 20.04 (also WSL), but it should work
for other Linux distros as well


### Installing Java

Download OpenJDK 11 or Oracle JDK 11 (It's important that the version is 11 - spark requires 8 or 11)

We'll use [OpenJDK](https://jdk.java.net/archive/)

Download it (e.g. to `~/spark`):

```
wget https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_linux-x64_bin.tar.gz
```

Unpack it:

```bash
tar xzfv openjdk-11.0.2_linux-x64_bin.tar.gz
```

Move folder jdk-11.02 inside spark folder:
```bash
mv jdk-11.02 ~/spark/
```

define `JAVA_HOME` and add it to `PATH`:

```bash
export JAVA_HOME="${HOME}/spark/jdk-11.0.2"
export PATH="${JAVA_HOME}/bin:${PATH}"
```

check that it works:

```bash
java --version
```

Output:

```
openjdk 11.0.2 2019-01-15
OpenJDK Runtime Environment 18.9 (build 11.0.2+9)
OpenJDK 64-Bit Server VM 18.9 (build 11.0.2+9, mixed mode)
```

Remove the archive:

```bash
rm openjdk-11.0.2_linux-x64_bin.tar.gz
```

### Installing Spark

Download Spark. Use 3.1.3 version:

```bash
wget https://dlcdn.apache.org/spark/spark-3.1.3/spark-3.1.3-bin-hadoop3.2.tgz
```

Unpack:

```bash
tar xzfv spark-3.1.3-bin-hadoop3.2.tgz
```

Remove the archive:

```bash
rm spark-3.1.3-bin-hadoop3.2.tgz
```

Move spark3.1.3 to spark folder:
```bash
mv spark-3.1.3-bin-hadoop3.2 ~/spark/

Add it to `PATH`:

```bash
export SPARK_HOME="${HOME}/spark/spark-3.1.3-bin-hadoop3.2"
export PATH="${SPARK_HOME}/bin:${PATH}"
```

### Testing Spark

Execute `spark-shell`, if you succeed, you'll see something like this:

![spark-install](../docs/spark-install.png)

Also try running the following code, to make sure that everything works:

```scala
val data = 1 to 10000
val distData = sc.parallelize(data)
distData.filter(_ < 10).collect()
```

### PySpark

It's the same for all platforms. Go to [pyspark.md](pyspark.md). 