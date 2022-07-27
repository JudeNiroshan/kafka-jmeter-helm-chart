## Performance test

The performance test is a helm chart that has 2 jobs, each containing c container with a jmeter used as kafka producer.
One of the producers is writing to transaction-list topic and another to account topic.

### Set parameters
Set the wanted parameters in [values.yaml](values.yaml):

`numRecords` - the number of record to send to the topic

`recordSize` - the record size to send to the topic

`sleepTime` - the time to wait between batches of records being sent

`loopCount` - the number of times to send records to the topics

### Install the helm chart

Install the chart on the Openshift and check that 2 jobs were created successfully with their pods.

```shell
helm install performance-test .
```

### Monitor cpu/memory usage
To see the cpu/memory usage while test is running, switch to developer perspective and go to monitoring section,
select in the workload dropdown list the kafka stateful set. 


### Test

I ran the test with the following parameters:

#### transaction-list topic

`numRecords` - 1600

`recordSize` - 410 byte

#### account topic

`numRecords` - 400

`recordSize` - 280 byte

#### jmeter parameters

`sleepTime` - 30 seconds

`loopCount` - 2880



