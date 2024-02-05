# Creating-a-Virtual-Private-Cloud

<h2>Task 1: Creating a VPC </h2>

1. In the search bar search for VPC to open the VPC console
2. Choose Your VPCs
3. Choose Create VPC and enter the following:
   - Lab VPC
   - IPv4 CIDR Block: 10.0.0.0/16
   - Choose Create VPC
4. Choose Actions and select Edit VPC Settings
5. Enable DNS hostname and click save

<p align="center">
<br/>
<img src="https://i.imgur.com/FgxnVMv.png"/>

<h2>Task 2: Creating Public and Private Subnets</h2>

1. In the left navigation pane choose subnets
   - VPC ID: Lab VPC
   - Subnet name: Public Subnet
   - Availability Zone: Select the first availability zone
   - IPv4 CIDR block: 10.0.0.0/24
   - Choose Create Subnet
2. Select Public Subnet
3. Choose Actions and Select Edit subnet settings, then
   - Select: Enable auto-assign public IPv4 Address
   - Choose Save
4. In the left navigation pane, choose subnets
   - VPC ID: Lab VPC
   - Subnet name: Private Subnet
   - Availability Zone: Select the first availability zone
   - IPv4 CIDR block: 10.0.2.0/23
   - Choose Create Subnet
  
<p align="center">
<br/>
<img src="https://i.imgur.com/s02gQpv.png"/>

<h2>Task 3: Creating an Internet Gateway</h2>

1. In the left navigation pane, choose Internet Gateways.
2. Choose Create internet gateway and configure these settings:
   - Name tag: Lab IGW
   - Choose Create internet gateway
   - You can now attach the internet gateway to your Lab VPC.
3. Choose Actions then Attach to VPC, and configure these settings:
   - Available VPCs: Place you cursor in the search box, then select Lab VPC 
   - Choose Attach internet gateway

<p align="center">
<br/>
<img src="https://i.imgur.com/U2xVLlO.png"/>

h2>Task 4: Configuring Route Tables </h2>

1. In the left navigation pane, choose Route Tables.
2. Scroll to the right so that you can see the VPC  column, then expand the width of the column so that you can see which one is used by Lab VPC.
3. Scroll back to the left and select  the route table that shows Lab VPC.
4. In the Name column, choose  then enter the name  Private Route Table and choose .
5. In the lower half of the page, choose the Routes tab.
6. Choose Create route table and configure these settings:
   - Name: Public Route Table
   - VPC: Lab VPC
   - Choose Create route table
7. In the Routes tab, choose Edit routes
8. Choose Add route then configure these settings:
   - Destination: 0.0.0.0/0
   - Target: Select Internet Gateway and then, from the list, select Lab IGW
   - Choose Save changes
9. Choose the Subnet associations tab.
10. Choose Edit subnet associations
11. Select the row with Public Subnet.
12. Choose Save associations

<p align="center">
<br/>
<img src="https://i.imgur.com/qK0XHDC.png"/>

h2>Task 5: Creating a security group for the application server </h2>

1. In the left navigation pane, choose Security Groups.
2. Choose Create security group and configure these settings:
   - Security group name: App-SG
   - Description: Allow HTTP traffic
   - VPC: select the X to clear the default selection, then choose Lab VPC
   - Scroll to the bottom and choose Create security group
3. Verify the Inbound rules tab is selected below.
4. Choose Edit inbound rules
5. Choose Add rule and then configure these settings:
   - Type:  HTTP
   - Source type: Anywhere-IPv4
   - Description: Allow web access
   - Choose Save rules
  
<p align="center">
<br/>
<img src="https://i.imgur.com/Z6apWyv.png"/>

h2>Task 6: Launching an application server in the public subnet</h2>

1. In the search box to the right of  Services, search for and choose EC2 to open the EC2 console.
2. From the Launch instance menu, choose Launch Instance. Configure these options:
   - Name: App Server
   - In the list of available Quick Start AMIs, keep the default Amazon Linux selected. Also keep the specific default Amazon Linux 2023 AMI selected.
   - In the Instance type panel, keep the default t2.micro selected.
   - From the Key pair name menu, select vockey.
   - Next to Network settings, choose Edit, then configure: 
      - Network: Lab VPC
      - Subnet: Public Subnet
   - Under Firewall (security groups), choose  Select an existing security group.
      - For Common security groups, select App-SG.
   - In the Configure storage section, keep the default settings.
   - Expand the Advanced details panel.
   - IAM instance profile: Inventory-App-Role 
   - For the Metadata version set to V1 and V2 (token optional).
   - Scroll to the bottom of the page and then copy and paste the code shown below into the User data box

<p align="center">
<br/>
<img src="https://i.imgur.com/4rIxgLo.png"/>
  
   - At the bottom of the Summary panel on the right side of the screen choose Launch instance. You will see a Success message.
3. Choose View all instances
4. Wait until the App Server instance shows 2/2 checks passed in the Status check column. This may take a few minutes. Choose the refresh  icon at the top of the page every 30 seconds or so to more quickly become aware of the latest status of the instance.
5. Select  App Server.
6. Copy the Public IPv4 DNS value shown in the Details tab at the bottom of the page.
7. Open a new web browser tab with that IP address

<p align="center">
<br/>
<img src="https://i.imgur.com/AsMb74C.png"/>
