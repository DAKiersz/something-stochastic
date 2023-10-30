
# Linux - User and Permissions Management

## id

Print real and effective user and group IDs:

```shell
id username
```

## chmod

Change permissions of a file.

```
sudo chmod 755 file
```

## chown

Change owner of the file

```
sudo chown user file
```

`-R` is recursive to change the owner for the whole directory.

## Create a new user

```shell
sudo adduser -uid 3100 bob
```

## Create new group

```shell
sudo addgroup --gid 3100 bob
```

## Change users primary group

```shell
sudo usermod -g groupname username
```

## Add an existing user to a secondary group

```shell
sudo usermod -aG groupname username
```

Where `-a` is append.

## Remove a User From a Group

```shell
sudo gpasswd -d username groupname
```

## Delete a group

```shell
sudo groupdel bob
```


