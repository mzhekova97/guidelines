# Chrony installation and setup

**If `chrony` is not installed:**
1. Install it with `sudo apt install chrony`.
2. Open the configuration file on the control station `sudo vim /etc/chrony/chrony.conf` and add the following lines

    ```
    driftfile /var/lib/chrony/chrony.drift
    #This directive lets 'chronyd' to serve time even if unsynchronised to any ntp server
    local stratum 8
    manual
    #This directive designates subnets (or nodes) from which NTP clients are allowed
    #to access to 'chronyd'.
    allow 192.168.30
    smoothtime 400 0.01
    ```
3. Add the follwing lines to the configuration files of the robot
    ```
    server 192.168.30.106  iburst minpoll 0 maxpoll 5 maxdelay .005
    driftfile /var/lib/chrony/drift
    logdir /var/log/chrony
    log measurements statistics tracking
    makestep 1 -1
    pool 2.debian.pool.ntp.org offline iburst
    ```
4. To synchronise both, check the date and time in the drone and PC by tapping 
    ```
    date
    ``` 
5. If the date is not corresponding, kill chrony by typing `sudo killall -9 chronyd`. Check again.

*Note:*  
*If the date corresponds but the time is not corresponding after step 5, it is not that big of an issue.*
