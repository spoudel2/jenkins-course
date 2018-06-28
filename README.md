# Starting, stopping, and restarting Jenkins on Ubuntu
Jenkins by default starts running when installed. Here are the commands to start, stop, restart, and check the status of the Jenkins service:

* To start Jenkins, use the following command:
 ```shell
 sudo systemctl start jenkins
 ```
* Similarly, to stop Jenkins, use the following command:
  ```shell
  sudo systemctl stop jenkins
  ```
* To restart Jenkins, use the following command:
```shell
sudo systemctl restart jenkins
```
* To check the status of the Jenkins service, use the following systemctl command:
```shell
sudo systemctl status jenkins
```
You should see the following output:
```shell
● jenkins.service - LSB: Start Jenkins at boot time
   Loaded: loaded (/etc/init.d/jenkins; bad; vendor preset: enabled)
   Active: inactive (dead) since Thu 2018-06-28 20:39:16 IST; 13min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 7632 ExecStop=/etc/init.d/jenkins stop (code=exited, status=0/SUCCESS
  Process: 2038 ExecStart=/etc/init.d/jenkins start (code=exited, status=0/SUCCE

Jun 28 20:25:41 shilpa su[2682]: Successful su for jenkins by root
Jun 28 20:25:41 shilpa su[2682]: + ??? root:jenkins
Jun 28 20:25:41 shilpa su[2682]: pam_unix(su:session): session opened for user j
Jun 28 20:25:43 shilpa jenkins[2038]:    ...done.
Jun 28 20:25:43 shilpa systemd[1]: Started LSB: Start Jenkins at boot time.
Jun 28 20:39:14 shilpa systemd[1]: Stopping LSB: Start Jenkins at boot time...
Jun 28 20:39:14 shilpa jenkins[7632]: Correct java version found
Jun 28 20:39:14 shilpa jenkins[7632]:  * Stopping Jenkins Automation Server jenk
Jun 28 20:39:16 shilpa jenkins[7632]:    ...done.
Jun 28 20:39:16 shilpa systemd[1]: Stopped LSB: Start Jenkins at boot time.
```
