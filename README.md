#EC2

# Key Pair

1. In the navigation pane, under Network & Security, choose Key Pairs. (Key pairs are used to securely log into your AWS servers without needing a password.)
2. Choose Create Key Pair (Top Right)
3. For Name, enter a descriptive name for the key pair
4. Key Pair Type : RSA
5. Private key file format : ppk (Since we’re using PuTTY)
6. Tag : For eg -
   a. Key : name  
   b. Value : anything (your choice)  
   Repeat for each tag
7. Click Create key pair
8. The private key file is automatically downloaded by your browser. The base file name is the name that you specified as the name of your key pair [THIS IS THE ONLY CHANCE FOR YOU TO SAVE THE PRIVATE KEY FILE, if you miss it redo the entire process]

# Security Group

1. Do not touch the default security groups
2. In the navigation pane, under Network & Security, choose Security Groups.
3. Choose Create Security Group.
4. Enter a descriptive name (You can't change the name of the security group after its created)
5. Leave the VPC as it is
6. Inbound rules :  
   a. It defines which incoming traffic is allowed to reach my EC2 Instance from outside world  
   b. We are defining where the traffic is allowed to come from  
   c. SSH :  
      i. Type - SSH  
      ii. Source - It is recommended to set it to ‘My IP’. But for Practicals we’ll select ‘Anywhere - IPv4’  
   d. Custom TCP :  
      i. Type - Custom TCP  
      ii. Port Range : Enter the Port on which your Express App is running  
      iii. Source - ‘Anywhere - IPv4’. Reason : Since this is a web app we want everyone to access our website  
7. Click Create Security Group

# Instances

1. In the navigation pane, under Instances choose Instances.
2. Click on Launch Instances
3. Give a descriptive name
4. Under Application & OS Images > Quick Start > Ubuntu > LTS (free tier eligible)
5. Under Instance Type > t2 .micro (for practicals)
6. Under Key pair - Give the key pair you created a while ago
7. Similar with the security group
8. Under Configure Storage : Use the free tier eligible
9. Review the summary (Right Side)
10. Click Launch Instance
11. It will take few minutes for the instance to run

# Elastic IP Address Allocation

1. In the navigation pane, under Network & Security, choose Elastic IPs
2. Click on Allocate Elastic IP Address
3. Just give it an existing tag
4. Click on Allocate
5. Click on Action, (besides Allocate Elastic IP Address) > Associate Elastic IP > Resource Type - Instance > Choose the Instance we created > Choose the IP Addr shown
6. Click on Allocate
7. To check go under Instances choose Instances > Select the instance created > scroll down > You’ll see an Elastic IP Addr value  
//Elastic IP Addr will be allocated to our instance

# PuTTy Configuration

1. Copy your Public IPv4 addr
2. Paste it under Host Name
3. Under Category > Connection > SSH > Auth > Credentials > Browse the ppk file we downloaded when we created Key Pair
4. Click Open > Accept
5. Login as : ubuntu
6. Run commands :  
   a. sudo apt update  
   b. sudo apt install nodejs npm (Do you want to continue : y)  
   //It will take some time  
   c. git clone <github link of your Express App>
7. To check if your folder has been cloned or not, use command : ls  
   a. cd <folderName>  
   b. nano <your html file>
8. Create a H1 tag “EC2”
9. Ctrl + O [this will save your file] > Press Enter
10. Ctrl + X [This will close your file]
11. Install Express : npm install express
12. Now run your JS file : node <JS file name >
13. Copy your Public IPv4 Addr, Paste it on the browser with your Port  
   a. “154.54.25.32:3000”  
Take a Screenshot of your page and the console
