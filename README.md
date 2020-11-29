# ufw-spamhaus
Download Spamhaus DROP and EDROP Lists and block access with UFW or use the following instructions:
Go to the folder where you want to store the list (either your local user or root)

<pre>
# make yourself sudo if possible
sudo su
# find a nice home
cd /root/

# wget the file from this repository (if git is installed)
wget https://github.com/dajul/ufw-spamhaus/blob/master/ufw-spamhaus.sh

# (optional) manually copy and create the file
vim ufw-spamhaus.sh

# make it executable
chmod +x ufw-spamhaus.sh

# set it loose
./spamhaus.sh

# confirm the rules have been added
iptables -L Spamhaus -n
</pre>

As user do:
<pre>
# find a nice home
cd /home/YOUR-USERNAME/bin/

# wget the file from this repository (if git is installed)
wget https://github.com/dajul/ufw-spamhaus/blob/master/ufw-spamhaus.sh

# create the file and paste
vim spamhaus.sh

# make it executable
chmod +x spamhaus.sh

# set it loose
sudo ./spamhaus.sh

# confirm the rules have been added
sudo iptables -L Spamhaus -n
</pre>

# Automatic Updating #
crontab as root
If you want to run this script through `crontab -e`, you must copy and paste your system path from `/etc/crontab` file. For example:
<pre>
# fire up the crontab (no sudo)
crontab -e

run the script every day at 3am
0 3 * * * /root/ufw-spamhaus.sh
</pre>

crontab as user
In order for the list to automatically update each day, you'll need to setup a cron job with crontab.
<pre>
# fire up the crontab (no sudo)
crontab -e

run the script every day at 3am
0 3 * * * /home/YOUR-USERNAME/bin/spamhaus.sh
</pre>

## Troubleshooting ##
If you need to remove all the Spamhaus rules, run the following:
<pre>
sudo iptables -F Spamhaus
</pre>
