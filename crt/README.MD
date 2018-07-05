

Execute Below commnad to create client and server cret.


```
cfssl -loglevel 3 gencert -ca=ca.crt -ca-key=nopass.key -config=ca-config.json -profile=server server-csr.json | cfssljson -bare /outputdir/server && \
echo -e "\t\t\t\t[Done]\n\t at /outputdir/server*.pem"

```

```
cfssl -loglevel 3 gencert -ca=ca.crt -ca-key=nopass.key -config=ca-config.json -profile=client client-csr.json | cfssljson -bare /output/client && \
echo -e "\t\t\t[Done]\n\t at /output/client*.pem"
```
