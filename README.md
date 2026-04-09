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
b.) Under Prerequisite - Prepare Template > click Build from Infrastructure Composer > Under Build from Infrastructure Composer > Click Create in Infrastructure Composer > At the top there are two choices Canvas/Template and Yaml/Json > choose Template and Yaml. > you need a yaml file, so in another browser tab go to my github repository "https://github.com/Ghabaei-Behzad/Final-Project-AWS-Portfolio-Project/edit/main/README.md" find MyStack-ASG.yaml. Copy the file from github and in the CloudFormation Infrastructure Composer Template code editor, paste it. > A button appears to "Validate" and "Create Template". first Validate, and if the yaml file is "Valid" click "Create Template"
c.) 


* Resources * 
1. "Introduction To AWS CloudFormation" | Jenna Pederson | " https://www.jennapederson.com/blog/introduction-to-aws-cloudformation/#:~:text=AWS%20CloudFormation%20is%20a%20framework,Mappings%2C%20Resources%2C%20and%20Outputs. "
2. "AWS CloudFormation Tutorial" | "https://www.youtube.com/watch?v=KO0zl6deRfs&t=526s"
   


