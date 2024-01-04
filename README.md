# AWS-Scenario-Based-Interview-Questions on EC2, IAM and VPC
These questions cover a wide range of topics related to network architecture and security on AWS.

### Question 1: You have been assigned to design a VPC architecture for a 2-tier application. The application needs to be highly available and scalable. How would you design the VPC architecture?
Answer: In this scenario, I would design a VPC architecture in the following way. I would create 2 subnets: public and private. The public subnet would contain the load balancers and be accessible from the internet. The private subnet would host the application servers. I would distribute the subnets across multiple Availability Zones for high availability. Additionally, I would configure auto scaling groups for the application servers.

### Question 2: Your organization has a VPC with multiple subnets. You want to restrict outbound internet access for resources in one subnet, but allow outbound internet access for resources in another subnet. How would you achieve this?

### Question 3: You have a VPC with a public subnet and a private subnet. Instances in the private subnet need to access the internet for software updates. How would you allow internet access for instances in the private subnet?
Answer: To allow internet access for instances in the private subnet, we can use a NAT Gateway or a NAT instance. We would place the NAT Gateway/instance in the public subnet and configure the private subnet route table to send outbound traffic to the NAT Gateway/instance. This way, instances in the private subnet can access the internet through the NAT Gateway/instance.

### Question 4: You have launched EC2 instances in your VPC, and you want them to communicate with each other using private IP addresses. What steps would you take to enable this communication?
Answer: By default, instances within the same VPC can communicate with each other using private IP addresses. To ensure this communication, we need to make sure that the instances are launched in the same VPC and are placed in the same subnet or subnets that are connected through a peering connection or a VPC peering link. Additionally, we should check the security groups associated with the instances to ensure that the necessary inbound and outbound rules are configured to allow communication between them.

### Question 5: You want to implement strict network access control for your VPC resources. How would you achieve this?
Answer: To implement granular network access control for VPC resources, we can use Network Access Control Lists (ACLs). NACLs are stateless and operate at the subnet level. We can define inbound and outbound rules in the NACLs to allow or deny traffic based on source and destination IP addresses, ports, and protocols. By carefully configuring NACL rules, we can enforce fine-grained access control for traffic entering and leaving the subnets.

### Question 6: Your organization requires an isolated environment within the VPC for running sensitive workloads. How would you set up this isolated environment?
Answer: To set up an isolated environment within the VPC, we can create a subnet with no internet gateway attached. This subnet, known as an “isolated subnet,” will not have direct internet connectivity. We can place the sensitive workloads in this subnet, ensuring that they are protected from inbound and outbound internet traffic. However, if these workloads require outbound internet access, we can set up a NAT Gateway or NAT instance in a different subnet and configure the isolated subnet’s route table to send outbound traffic through the NAT Gateway/instance.

### Question 7: Your application needs to access AWS services, such as S3 securely within your VPC. How would you achieve this?
Answer: To securely access AWS services within the VPC, we can use VPC endpoints. VPC endpoints allow instances in the VPC to communicate with AWS services privately, without requiring internet gateways or NAT gateways. We can create VPC endpoints for specific AWS services, such as S3 and DynamoDB, and associate them with the VPC. This enables secure and efficient communication between the instances in the VPC and the AWS services.

### Question 8: What is the difference between NACL and Subnet? Explain with a use case.
Answer: For example, if I want to design a security architecture, I would use a combination of NACLs and security groups. At the subnet level, I would configure NACLs to enforce inbound and outbound traffic restrictions based on source and destination IP addresses, ports, and protocols. NACLs are stateless and can provide an additional layer of defense by filtering traffic at the subnet boundary. At the instance level, I would leverage security groups to control inbound and outbound traffic. Security groups are stateful and operate at the instance level. By carefully defining security group rules, I can allow or deny specific traffic to and from the instances based on the application’s security requirements. By combining NACLs and security groups, I can achieve granular security controls at both the network and instance level, providing defense-in-depth for the sensitive application.

### Question 9: What is the difference between IAM users, groups, roles, and policies?
Answer:
IAM Users: Individual AWS accounts with unique credentials for accessing resources.
IAM Groups: Collections of users for easier permission management.
IAM Roles: Used for delegation of permissions to services, applications, or accounts.
IAM Policies: Documents specifying allowed or denied actions on AWS resources.

### Question 10: You have a private subnet in your VPC that contains a number of instances that should not have direct internet access. However, you still need to be able to securely access these instances for administrative purposes. How would you set up a bastion host to facilitate this access?
Answer:
Set up a bastion host in a public subnet with restricted SSH (or RDP) access.
Place private instances in a private subnet with limited internet access.
Configure security groups to allow traffic from the bastion host to private instances.
Connect to the bastion host and use it as a gateway to access private instances securely.
Use key pairs for authentication. Optionally, enable SSH Agent Forwarding for enhanced security.
Keep bastion host secure and patched. Monitor traffic for auditing purposes.
