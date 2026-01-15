generate secret key
```shell
openssl rand -base64 32
```

---

It is used to forcefully remove files and directories, including their subdirectories and contents

```shell
rm -rf 
```

---

connect to a remote server

```shell
ssh yang.shi@192.168.18.33
```

---

securely copying files between a local and a remote host or between two remote hosts

```shell
scp [file] jbosssup@10.23.35.168:/tmp/web
```

---

copying files from a source directory  to a remote server

```shell
rsync -azvP server yang.shi@192.168.18.33:~/. 
```

---

rename files and directories

```shell
mv file1.txt main.js
```

--- 

switch to the previous working directory

```shell
cd -
```

---

copy files or directories

```shell
cp path1 path2
```