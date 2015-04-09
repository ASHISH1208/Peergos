Testing
================

These are in increasing order of difficulty and each assumes nothing but fresh git clone.

###Single machine, single process, in-memory testing
```bash
make tests
java -jar PeergosTests.jar -local
```

###Single machine, two process, persistent testing
Start a local 5 node cluster with
```bash
java -jar PeergosServer.jar -test 5 -script testscripts/empty.txt
```

In another terminal, run
```bash
java -jar PeergosTests.jar
```

###Two machine, persistent testing
Start a 5 node cluster on machineA with
```bash
java -jar PeergosServer.jar -test 5 -script testscripts/empty.txt
```

On machineB, run
```bash
java -jar PeergosTests.jar -clusterAddress machineA -coreAddress machineA
```

###Distributed test

