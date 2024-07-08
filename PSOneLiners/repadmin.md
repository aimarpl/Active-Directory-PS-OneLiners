Not a pwsh, but still worth knowing / using it...

Step 1 - Check the replication health

```Repadmin /replsummary```

Step 2 - Check the inbound replication requests that are queued.
```
Repadmin /Queue
```

Step 3 - Check the replication status
```
Repadmin /Showrepl
```

Step 4 - Synchronize replication between replication partners
```
Repadmin /syncall
```

Step 5 - Force the KCC to recalculate the topology
```
Repadmin /KCC
```

Step 6 - Force replication
```
Repadmin /replicate
```

Step 7 - Show only errors
```
repadmin /showrepl /errorsonly
```
