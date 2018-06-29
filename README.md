# What is Jenkins?
* Jenkins is an open source contineous integration ( CI ) and contineous delivery ( CD) tools written in java.
* it is an automation server used to build and deliver software projects .
# What is CI /CD ?
* Continuous Integration ( CI ) is the practice , in softare engineering , of merging all developer working copies to shared machine several times a day.
* Contineous Delivery is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released at any time.

In practice: verify and pulish work by triggering automated builds and tests.

All developers should push their changes to a version control, which should then be built and testing - which cn be done by jenkins.

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
  ------
```
