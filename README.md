# How to Install Grafana on Ubuntu 22.04 or 20.04 LTS Linux
Step 1: Start with Ubuntu System Update
We need to run the system update command on the  Linux system from time to time, especially before  installing some software package. It is because it not only installs the latest updates available for the  installed applications but even refreshes the package index cache of APT. So, open your  Ubuntu command terminal and run:
```
sudo apt update && sudo apt upgrade
```
# Step 2: Install the required extra packages
There are a few packages that we will require to perform the commands given in this tutorial, so install them using the given syntax.
```
sudo apt install -y apt-transport-https software-properties-common wget
```
 Add Grafana GPG key and Repository
To  install Grafana on Ubuntu, you can use the APT package manager. However, before that, we need to add its repository and a GPG key used to sign the packages available through that repository. it is because the default  Ubuntu repos don’t supply the packages we are required to  install  Grafana on Linux.

First, let’s add the GPG key.
```
sudo mkdir -p /etc/apt/keyrings/
```
```
wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
```
Now, add the repository:
```
echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```
# Step 3: Installing Grafana on Ubuntru 22.04 or 20.04
Once you have executed all the above-given commands your  Ubuntu system will be ready to install Grafana, however, before that rerun the system update command. It is because we have manually added a new repository in the previous step and need to refresh the APT package index cache to make it recognize the newly available packages to  install.
```
sudo apt update
```
Now, use APT to install the latest Grafana open source or community edition:
```
sudo apt install grafana
```
(optional) Those, who are interested in the latest Enterprise edition (paid), can run this command instead of the above one:
```
sudo apt install grafana-enterprise
```
<img src="./esp32mqttdht22_github.svg" width=100% height=40%>
# Step 4 - Start the Grafana service
Once the Grafana installation process has been completed, you can verify the version using:
```
sudo grafana-server -v
```
Next, start the Grafana service and enable it to start automatically at system reboot using the following commands:
```
sudo systemctl start grafana-server
```
```
sudo systemctl enable grafana-server
```
