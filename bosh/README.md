## Bosh

### debugging

```
bosh ssh

sudo su -

monit summary

cat /var/vcap/sys/log/monit/*.log

tail -f /var/vcap/sys/log/**/*.log

# debugging
cat /var/vcap/sys/log/monit/
```

### Blobs

upload blobs to our blobstore using credentials in `config/private.yml`

```
bosh upload blobs
```

Download blobs from blob store using credentials in `config/private.yml`

```
bosh sync blobs
```
