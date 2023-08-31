
# systemd model
- this is a model of systemd, it is used as an alternative to cronjob, since for the cronjob to run you need to be logged in, with systemd 
the machine only need to be up
- systemd can have service or both (service and timer)
- the service will point to the file you want to execute, the timer will set the time you want to execute
## Before creating
- first of all systemds are located in the path in linux

```
/etc/systemd/system
```
- you can list current systemds timers with this command

```
systemctl status *timer
```

- the timers look like this :

```
● mlocate-updatedb.timer - Updates mlocate database every day
     Loaded: loaded (/usr/lib/systemd/system/mlocate-updatedb.timer; enabled; vendor preset: enabled)
     Active: active (waiting) since Tue 2020-06-02 08:02:33 EDT; 2 days ago
    Trigger: Fri 2020-06-05 00:00:00 EDT; 15h left
   Triggers: ● mlocate-updatedb.service

Jun 02 08:02:33 testvm1.both.org systemd[1]: Started Updates mlocate database every day.
```

Some information is very important like the line loaded, Active, Trigger, Triggers. In short, the loaded is where the timer file is, the Active indicates the status and when it was executed, the Trigger indicates the approximate date that it will be executed again, the Triggers points to the service. It has other information like description etc.

## Creating a systemd

1 - enter the indicated path where the systemd are <br>
2 - create a file with the name of your service and suffix (extension) .service <br>
3 - create a file with the name of your timer and suffix (extension) .timer<br>
## Activating the timer and service
1 - enable the timer with the command
```
systemctl enable MyScriptTimer.timer
```
2 - start the timer
```
systemctl start MyScriptTimer.timer
```
3 - restart systemd service
```
systemctl daemon-reload
```
4 - copy the template and change it to your needs, remembering that the service can run any program file not just bash scripts.
### references
- https://www.certificacaolinux.com.br/systemd-timer-no-linux-mulplexar-terminal-guia-basico/
- https://opensource.com/article/20/7/systemd-timers

### Comments
You should see this links above, they are more detailed, this repo its more like a shortcut, summerized. So i strongly encourage to search more about systemd.