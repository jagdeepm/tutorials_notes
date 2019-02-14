# Usefull Blog to start writing systemd service file
 - https://www.linux.com/blog/learn/intro-to-linux/2018/5/writing-systemd-services-fun-and-profit
 - https://www.linux.com/blog/learn/2018/5/systemd-services-beyond-starting-and-stopping
 

# Important points
 
  - There are several types of systemd units (the formal name of systemd scripts), such as timers, paths, and so on
  - You can add options to your executables, but you can't chain a bunch of Bash commands together . for example `ExecStart: lsmod | grep nvidia > videodrive.txt`
 is invalid
 - If you don't specify an ExecStop, systemd will take it on itself to finish the process as gracefully as possible.
 - The --user option tells systemd to look for the service in your own directories and to execute the service with your user's privileges.
   For ex `systemd --user start minetest`
   
# Example unit service file
  
```
  # minetest.service

  [Unit]  
  Description= Minetest server 
  Documentation= https://wiki.minetest.net/Main_Page 

  [Service] 
  Type= simple 
  ExecStart= /usr/games/minetest --server
```

# Troubleshooting errors
  - service start failed with code = exited and status = 203 , This indicates that the systemd could not either find the file/directory or the file is not executable. 
  To fix this if you are running a bash script to start the the service add `/bin/bash` to start the script for example `/bin/bash /opt/pydata/startpydata.sh `   
  
  ```
   sample.service: Main process exited, code=exited, status=203/EXEC
   sample.service:  Unit entered failed state.
   ```
