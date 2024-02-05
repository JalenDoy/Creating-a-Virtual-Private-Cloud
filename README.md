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
