# thanos <br>
Q: is minio distributed or single node?<br>
A: Yes, its distributed, and hava a balancer "Traefik" before it.<br>
<br><br>
Thanos-compactor command:<br>
<code>/usr/sbin/thanos compact --wait --log.level=debug --data-dir=/thanos/compact --http-address=0.0.0.0:19191 --objstore.config-file=/opt/thanos/storage.yaml --retention.resolution-raw=21d --retention.resolution-5m=90d --retention.resolution-1h=365d --consistency-delay=30m --block-sync-concurrency=20 --compact.concurrency=5
</code>
<br>
Thanos-compactor log:<br>

```
level=warn ts=2020-02-13T06:58:54.435535548Z caller=prober.go:117 msg="changing probe status" status=not-ready reason="error executing compaction: compaction failed: 3 errors: compaction failed for group 0@15871345448339717723: compact blocks [/thanos/compact/compact/0@15871345448339717723/01E0901C5EVJKKDQQ38BP0DNE4 /thanos/compact/compact/0@15871345448339717723/01E096X3E6X0653WT1KPE89G6T /thanos/compact/compact/0@15871345448339717723/01E09DRTP7G9D0F973XBQFM3H8]: write compaction: iterate compaction set: chunk 134217556 not found: segment doesn't include enough bytes to read the chunk - required:134217752, available:134217728; compaction failed for group 0@3615588222792942986: compact blocks [/thanos/compact/compact/0@3615588222792942986/01E0AG3EZ2MVGNH4E4RY0428DD /thanos/compact/compact/0@3615588222792942986/01E0APZ6725DY5PW9WAHQQ9PZG /thanos/compact/compact/0@3615588222792942986/01E0AXTXF2PPS8AP2GST8D3QP4 /thanos/compact/compact/0@3615588222792942986/01E0B4PMQ24C9G6BTN0R18TJMC]: write compaction: iterate compaction set: chunk 134217723 not found: segment doesn't include enough bytes to read the chunk - required:134217839, available:134217728; compaction failed for group 0@10694505281190012710: compact blocks [/thanos/compact/compact/0@10694505281190012710/01E09MMHXTHJWZTBX4DSVEHWWQ /thanos/compact/compact/0@10694505281190012710/01E09VG95EYKXMHZWFX8DK6MAQ /thanos/compact/compact/0@10694505281190012710/01E0A2C0DGW6BQXW8E9K4CMHZ4 /thanos/compact/compact/0@10694505281190012710/01E0A97QNS22R5Z64FYBR1W27Y]: write compaction: iterate compaction set: chunk 134217514 not found: segment doesn't include enough bytes to read the chunk - required:134217797, available:134217728"
level=info ts=2020-02-13T06:58:54.483471541Z caller=http.go:78 service=http/server component=compact msg="internal server shutdown" err="error executing compaction: compaction failed: 3 errors: compaction failed for group 0@15871345448339717723: compact blocks [/thanos/compact/compact/0@15871345448339717723/01E0901C5EVJKKDQQ38BP0DNE4 /thanos/compact/compact/0@15871345448339717723/01E096X3E6X0653WT1KPE89G6T /thanos/compact/compact/0@15871345448339717723/01E09DRTP7G9D0F973XBQFM3H8]: write compaction: iterate compaction set: chunk 134217556 not found: segment doesn't include enough bytes to read the chunk - required:134217752, available:134217728; compaction failed for group 0@3615588222792942986: compact blocks [/thanos/compact/compact/0@3615588222792942986/01E0AG3EZ2MVGNH4E4RY0428DD /thanos/compact/compact/0@3615588222792942986/01E0APZ6725DY5PW9WAHQQ9PZG /thanos/compact/compact/0@3615588222792942986/01E0AXTXF2PPS8AP2GST8D3QP4 /thanos/compact/compact/0@3615588222792942986/01E0B4PMQ24C9G6BTN0R18TJMC]: write compaction: iterate compaction set: chunk 134217723 not found: segment doesn't include enough bytes to read the chunk - required:134217839, available:134217728; compaction failed for group 0@10694505281190012710: compact blocks [/thanos/compact/compact/0@10694505281190012710/01E09MMHXTHJWZTBX4DSVEHWWQ /thanos/compact/compact/0@10694505281190012710/01E09VG95EYKXMHZWFX8DK6MAQ /thanos/compact/compact/0@10694505281190012710/01E0A2C0DGW6BQXW8E9K4CMHZ4 /thanos/compact/compact/0@10694505281190012710/01E0A97QNS22R5Z64FYBR1W27Y]: write compaction: iterate compaction set: chunk 134217514 not found: segment doesn't include enough bytes to read the chunk - required:134217797, available:134217728"
level=info ts=2020-02-13T06:58:54.483630546Z caller=prober.go:137 msg="changing probe status" status=not-healthy reason="error executing compaction: compaction failed: 3 errors: compaction failed for group 0@15871345448339717723: compact blocks [/thanos/compact/compact/0@15871345448339717723/01E0901C5EVJKKDQQ38BP0DNE4 /thanos/compact/compact/0@15871345448339717723/01E096X3E6X0653WT1KPE89G6T /thanos/compact/compact/0@15871345448339717723/01E09DRTP7G9D0F973XBQFM3H8]: write compaction: iterate compaction set: chunk 134217556 not found: segment doesn't include enough bytes to read the chunk - required:134217752, available:134217728; compaction failed for group 0@3615588222792942986: compact blocks [/thanos/compact/compact/0@3615588222792942986/01E0AG3EZ2MVGNH4E4RY0428DD /thanos/compact/compact/0@3615588222792942986/01E0APZ6725DY5PW9WAHQQ9PZG /thanos/compact/compact/0@3615588222792942986/01E0AXTXF2PPS8AP2GST8D3QP4 /thanos/compact/compact/0@3615588222792942986/01E0B4PMQ24C9G6BTN0R18TJMC]: write compaction: iterate compaction set: chunk 134217723 not found: segment doesn't include enough bytes to read the chunk - required:134217839, available:134217728; compaction failed for group 0@10694505281190012710: compact blocks [/thanos/compact/compact/0@10694505281190012710/01E09MMHXTHJWZTBX4DSVEHWWQ /thanos/compact/compact/0@10694505281190012710/01E09VG95EYKXMHZWFX8DK6MAQ /thanos/compact/compact/0@10694505281190012710/01E0A2C0DGW6BQXW8E9K4CMHZ4 /thanos/compact/compact/0@10694505281190012710/01E0A97QNS22R5Z64FYBR1W27Y]: write compaction: iterate compaction set: chunk 134217514 not found: segment doesn't include enough bytes to read the chunk - required:134217797, available:134217728"
level=error ts=2020-02-13T06:58:54.483812551Z caller=main.go:194 msg="running command failed" err="error executing compaction: compaction failed: 3 errors: compaction failed for group 0@15871345448339717723: compact blocks [/thanos/compact/compact/0@15871345448339717723/01E0901C5EVJKKDQQ38BP0DNE4 /thanos/compact/compact/0@15871345448339717723/01E096X3E6X0653WT1KPE89G6T /thanos/compact/compact/0@15871345448339717723/01E09DRTP7G9D0F973XBQFM3H8]: write compaction: iterate compaction set: chunk 134217556 not found: segment doesn't include enough bytes to read the chunk - required:134217752, available:134217728; compaction failed for group 0@3615588222792942986: compact blocks [/thanos/compact/compact/0@3615588222792942986/01E0AG3EZ2MVGNH4E4RY0428DD /thanos/compact/compact/0@3615588222792942986/01E0APZ6725DY5PW9WAHQQ9PZG /thanos/compact/compact/0@3615588222792942986/01E0AXTXF2PPS8AP2GST8D3QP4 /thanos/compact/compact/0@3615588222792942986/01E0B4PMQ24C9G6BTN0R18TJMC]: write compaction: iterate compaction set: chunk 134217723 not found: segment doesn't include enough bytes to read the chunk - required:134217839, available:134217728; compaction failed for group 0@10694505281190012710: compact blocks [/thanos/compact/compact/0@10694505281190012710/01E09MMHXTHJWZTBX4DSVEHWWQ /thanos/compact/compact/0@10694505281190012710/01E09VG95EYKXMHZWFX8DK6MAQ /thanos/compact/compact/0@10694505281190012710/01E0A2C0DGW6BQXW8E9K4CMHZ4 /thanos/compact/compact/0@10694505281190012710/01E0A97QNS22R5Z64FYBR1W27Y]: write compaction: iterate compaction set: chunk 134217514 not found: segment doesn't include enough bytes to read the chunk - required:134217797, available:134217728"
```
<br><br>
Error blocks:<br>
01E0901C5EVJKKDQQ38BP0DNE4<br>
01E096X3E6X0653WT1KPE89G6T<br>
01E09DRTP7G9D0F973XBQFM3H8<br>
01E0AG3EZ2MVGNH4E4RY0428DD<br>
01E0APZ6725DY5PW9WAHQQ9PZG<br>
01E0AXTXF2PPS8AP2GST8D3QP4<br>
01E0B4PMQ24C9G6BTN0R18TJMC<br>
01E09MMHXTHJWZTBX4DSVEHWWQ<br>
01E09VG95EYKXMHZWFX8DK6MAQ<br>
01E0A2C0DGW6BQXW8E9K4CMHZ4<br>
01E0A97QNS22R5Z64FYBR1W27Y<br>
<br><br>
Also, I attach a system organization diagram and configuration files.<br>
All elements are stand-alone servers.<br>
<br>
![screen](https://github.com/Zergvl/thanos/blob/master/Thanos.JPG)
<br>
There is Thanos bucket info in bucket.txt
<br><br>
tags from consul service for traefik:<br>

```
traefik.http.routers.thanos_http.entrypoints=http
traefik.http.routers.thanos_https.entrypoints=https
traefik.http.routers.thanos_http.rule=Host(`****`)
traefik.http.routers.thanos_https.rule=Host(`****`)
traefik.http.routers.thanos_https.tls=true
```
<br><br>
Another question is about retention and downsampling, <br>
Am I understand correctly that according to my settings, Thanos compactor should do downsampling in 5 minutes for data older than 21 days <br>
and an hour-downsampling to data older than 90 days, and all older than 365 - delete?<br>
<br>
