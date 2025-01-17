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
<img src="./Images/grafana01.jpg" width=100% height=100%>

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
<img src="./Images/grafana02.jpg" width=100% height=100%>

# Step 5 - Verify that the Grafana service is running
Now verify that the Grafana service is active by running the command below:
```
sudo systemctl status grafana-server
```
If the Grafana service was started successfully, you should see a sign that it is active and running.
<img src="./Images/grafana03.jpg" width=100% height=100%>
# Step 6 - Open the port in the firewall
Port 3000 is Grafana's default port for its web interface. To allow external access to Grafana, you must enable the firewall and open port 3000. To do this, execute the following commands in your terminal:
```
sudo ufw enable 
sudo ufw allow ssh
sudo ufw allow 3000/tcp
```
<img src="./Images/grafana04.jpg" width=100% height=100%>

# Step 7 - Access the Grafana web interface
To access the Grafana web interface, open a web browser and enter the IP address of your server (or hostname if applicable), followed by port 3000. The URL format should be http://your_server_IP:3000. Once loaded, you should see the Grafana login page. The default credentials are:

Username: admin

Password: admin

<img src="./Images/grafana05.jpg" width=100% height=100%>

Once done, you'll have access to Grafana's dashboard.

<img src="./Images/grafana06.jpg" width=100% height=100%>

You'll be prompted to create a new password. Input a secure password, confirm it, and click the "Submit" button.

<img src="./Images/grafana07.jpg" width=100% height=100%>

# How to uninstall Grafana
If you need to uninstall Grafana for any reason, you can do so by running the following commands:
```
sudo systemctl stop grafana-server
```
```
sudo apt remove grafana
```
<img src="./Images/grafana08.jpg" width=100% height=100%>
