# Day5 Assignment

1. Create a directory structure in your home folder named **webapp-deploy**

```
mkdir -p ~/webapp-deploy/{config,bin,backup}
```

2. Inside ~/webapp-deploy/config/, create a file named **app_settings.conf**

```
touch ~/webapp-deploy/config/app_settings.conf
```

3. Add the following content to it (DATABASE_HOST=localhost, DATABASE_PORT=3306)

```
echo -e "DATABASE_HOST=localhost\nDATABASE_PORT=3306" > ~/webapp-deploy/config/app_settings.conf
```

4. Create a hard link named **production_settings.conf** inside the backup directory pointing to the original file

```
ln ~/webapp-deploy/config/app_settings.conf ~/webapp-deploy/backup/production_settings.conf
```

5. Check inode numbers and save the output to **hardlink_proof.txt**

```
ls -li ~/webapp-deploy/config/app_settings.conf ~/webapp-deploy/backup/production_settings.conf > ~/webapp-deploy/hardlink_proof.txt
```

6. Create a symbolic link named **current_config** in bin using a relative path

```
cd ~/webapp-deploy/bin
ln -s ../config/app_settings.conf current_config
```

7. Verify the symlink using cat and append output to **symlink_proof.txt**

```
cat ~/webapp-deploy/bin/current_config >> ~/webapp-deploy/symlink_proof.txt
```

8. Create an uncompressed tar archive **config_backup.tar** containing only config contents

```
tar -cf ~/webapp-deploy/backup/config_backup.tar -C ~/webapp-deploy/config .
```

9. Verify archive contents and save listing to **archive_contents.txt**

```
tar -tf ~/webapp-deploy/backup/config_backup.tar > ~/webapp-deploy/archive_contents.txt
```

10. Create a gzip archive **webapp_deploy.tar.gz** for the entire directory

```
tar -czf ~/webapp_deploy.tar.gz -C ~ webapp-deploy
```

11. Move the compressed archive into ~/webapp-deploy

```
mv ~/webapp_deploy.tar.gz ~/webapp-deploy/
```

12. Display sizes of both archives and save output to **size_comparison.txt**

```
du -h ~/webapp-deploy/backup/config_backup.tar ~/webapp-deploy/webapp_deploy.tar.gz > ~/webapp-deploy/size_comparison.txt
```
