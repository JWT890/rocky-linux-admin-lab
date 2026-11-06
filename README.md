# rocky-linux-admin-lab

This is a Rocky Linux admin lab, a good precursor project to a more Enterprise administration lab with more features

Rocky Linux download: https://rockylinux.org/download   
Downloaded Rocky Linux 9

# Setup
Name: Rocky Linux Lab   
Rocky 9 ISO 
Type: Linux with Red Selected   
Memory: 8192    
60 GB of disk   
NAT for Adapter 1   
Host only for Adapter 2 

After those inputs get Rocky Linux up which will take a few minutes.    
![Linux](./images/linux.png)    
Then run ip a in the terminal to get the address for enp0s8. After that run ping -c 3 google.com to check for network connectivity. 
After verifying, SSH into the Rocky Linux instance mainly so I don't have to escape out of the VM repeatealy.    
Then run sudo dnf update -y to update the system, then run sudo dnf install -y vim tar bash-completion net-tools bind-utils lsof. After that its time for the administration site of it.    

# Administration
We are going to create a user by typing sudo useradd -m -s /bin/bash alice, then type sudo passwd alice to give her a password. 
Then type sudo groupadd developers to create the developers group, then add alice to the group by typing sudo usermod -aG developers alice, then verify by running id alice and getent group developers to verify group membership for alice:   
![Alice](./images/alice.png)    
To change the status of alice's account, lock by typing sudo usermod -L alice, to see status run sudo passwd -S alice, to unlock run sudo usermod -U alice, to change password run sudo chage -l alice, to set a password change date run sudo chage -M 90 alice.   
To verify alice can be reached type su - alice and it will switch to her.   
![Alice1](./images/alice1.png)  
What is being checked here is that /etc/passwd stores the password, /etc/shadow hashes the password so passwords can stay here, and /etc/group shows group membership.  
Delete the alice user and lets move on to file permissions. 
