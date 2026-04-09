# Final-Project-AWS-Portfolio-Project
Design, deploy, and document a Cloud Architecture, Compute Services, Infrastructure, and Supporting Services.  Include Architecture Requirements and a Working Deployment.

Based on your template, this architecture establishes a highly available web server environment. Traffic enters via the Application Load Balancer (ALB), which is governed by the ALBSecurityGroup to allow public HTTP access. The ALB then forwards requests to the Auto Scaling Group (ASG).

## Project overview and setup instructions
AWS CloudFormation is an Infrastructure as Code (IaC) service that allows you to model, provision, and manage AWS resources, like EC2 instances or S3 buckets, using declarative JSON or YAML templates. By grouping resources into "stacks," it automates deployment, updates, and deletion in the correct order, ensuring consistent, repeatable infrastructure. *1 

The Key concepts are, 
a.) Templates: Text files (YAML is recommended) that define your infrastructure components and their settings.
b.) Stacks: The instantiation of a template; a single unit that manages the lifecycle of all resources defined in the template.
c.) Resources: The required section in a template declaring the actual AWS components to create (i.e., AWS::EC2::Instance).
d.) Parameters: Allow you to input custom values when creating or updating a stack, making templates reusable.
e.) Outputs: Returns information about your stack (i.e., an S3 bucket URL) to use in other stacks or tools.
*2

The benefits of using CloudFormation are,
a.) Automation: Eliminates manual resource creation, reducing human error.
b.) Version Control: Store infrastructure code in repositories like Git, allowing tracking and easy rollovers.
c.) Safety & Rollbacks: If a deployment fails, CloudFormation automatically rolls back to the previous stable state, preventing orphaned resources.
d.) Dependency Management: Automatically understands the relationships between resources (i.e., creating a security group before an EC2 instance).
The setup instructions.
The prerequisites are, 
a.) Access to an AWS account with an IAM user or role that has permissions to use Amazon EC2, S3, and CloudFormation, or administrative access.
b.)  Have a Virtual Private Cloud (VPC) that has access to the internet. This template requires a default VPC, which comes with newer AWS accounts. 
Instructions.
a.) Go to the AWS Console > in the search bar type CloudFormation > click on Create Stack (or hamburger icon > Stacks > Create Stack)
b.) Under Prerequisite - Prepare Template > click Build from Infrastructure Composer > Under Build from Infrastructure Composer > Click Create in Infrastructure Composer > At the top there are two choices Canvas/Template and Yaml/Json > choose Template and Yaml. > you need a yaml file, so in another browser tab go to my github repository "https://github.com/Ghabaei-Behzad/Final-Project-AWS-Portfolio-Project/edit/main/README.md" find MyStack-ASG.yaml. Copy the file from github and in the CloudFormation Infrastructure Composer Template code editor, paste it. > A button appears to "Validate" and "Create Template". first Validate, and if the yaml file is "Valid" click "Create Template" > pop up message which mentions "it's putting the template in an existing bucket" > click Confirm and continue to CloudFormation. > at Create Stack page click Next > Specify Stack Details, Stack Name: MyStack (no spaces) > Under Parameters the instance type is default t3.micro (free tier) > Latest AMI is probably: /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2 > under subnets click Subnets that you wanted (probably up to 6 available) click all or at least 2. > Under VPCID click your security group (choosing the default provided) > click next > Configure Stack Options we will keep the default choices made. > at the bottom Capabilities click the box saying "I acknowledge that AWS CloudFormation might create IAM resources." > click Next > last page at the bottom says submit, click it. > If you get a ROLLBACK_IN_PROGRESS (in red) then delete the stack and start over again trying a different yaml file. I recommend amazon's https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/gettingstarted.walkthrough.html (If you start over again go to S3 > Under General Purpose buckets > click the cf- bucket and "empty" > then exit  > after that, click the s3 cf- bucket again and click delete. Then start over after s3 has been cleared of previous ClouFormation delete, with the new yaml file.
c.) If you get CREATE_IN_PROGRESS then get 


* Resources * 
1. "Introduction To AWS CloudFormation" | Jenna Pederson | " https://www.jennapederson.com/blog/introduction-to-aws-cloudformation/#:~:text=AWS%20CloudFormation%20is%20a%20framework,Mappings%2C%20Resources%2C%20and%20Outputs. "
2. "AWS CloudFormation Tutorial" | "https://www.youtube.com/watch?v=KO0zl6deRfs&t=526s"
   


