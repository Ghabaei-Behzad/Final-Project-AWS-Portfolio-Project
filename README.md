#### Behzad Ghabaei
#### CS79C - AWS Compute Engines
#### Instructor Seno
#### 4/9/2026

# Final-Project-AWS-Portfolio-Project
Design, deploy, and document a Cloud Architecture, Compute Services, Infrastructure, and Supporting Services.  Include Architecture Requirements and a Working Deployment.

Based on your template, this architecture establishes a highly available web server environment. Traffic enters via the Application Load Balancer (ALB), which is governed by the ALBSecurityGroup to allow public HTTP access. The ALB then forwards requests to the Auto Scaling Group (ASG).

## Project overview and setup instructions
AWS CloudFormation is an Infrastructure as Code (IaC) service that allows you to model, provision, and manage AWS resources, like EC2 instances or S3 buckets, using declarative JSON or YAML templates. By grouping resources into "stacks," it automates deployment, updates, and deletion in the correct order, ensuring consistent, repeatable infrastructure. *1 

# The Key concepts are, 
#### a.) Templates: Text files (YAML is recommended) that define your infrastructure components and their settings.
#### b.) Stacks: The instantiation of a template; a single unit that manages the lifecycle of all resources defined in the template.
#### c.) Resources: The required section in a template declaring the actual AWS components to create (i.e., AWS::EC2::Instance).
#### d.) Parameters: Allow you to input custom values when creating or updating a stack, making templates reusable.
#### e.) Outputs: Returns information about your stack (i.e., an S3 bucket URL) to use in other stacks or tools.
*2

# The benefits of using CloudFormation are,
#### a.) Automation: Eliminates manual resource creation, reducing human error.
#### b.) Version Control: Store infrastructure code in repositories like Git, allowing tracking and easy rollovers.
#### c.) Safety & Rollbacks: If a deployment fails, CloudFormation automatically rolls back to the previous stable state, preventing orphaned resources.
#### d.) Dependency Management: Automatically understands the relationships between resources (i.e., creating a security group before an EC2 instance).
# The setup instructions.
## The prerequisites are, 
#### a.) Access to an AWS account with an IAM user or role that has permissions to use Amazon EC2, S3, and CloudFormation, or administrative access.
#### b.)  Have a Virtual Private Cloud (VPC) that has access to the internet. This template requires a default VPC, which comes with newer AWS accounts. 
## Instructions.
#### a.) Go to the AWS Console > in the search bar type CloudFormation > click on Create Stack (or hamburger icon > Stacks > Create Stack)
#### b.) Under Prerequisite - Prepare Template > click Build from Infrastructure Composer > Under Build from Infrastructure Composer > Click Create in Infrastructure Composer > At the top there are two choices Canvas/Template (first choose Template) > then beside it Yaml/Json appears > choose yaml > you need a yaml file, so find MyStack-ASG.yaml. > Copy the file from github > and paste it in the CloudFormation Infrastructure Composer Template code editor > A button appears to "Validate" and "Create Template". first Validate, and if the yaml file is "Valid" click "Create Template" > if "invalid forget it, get another template like amazon.yaml > if your yaml is valid and you can continue to create a template, a pop up message appears and mentions "it's putting the template in an existing bucket" > click Confirm and continue to CloudFormation. > at Create Stack page click Next > Specify Stack Details, Stack Name: MyStack (no spaces) > Under Parameters the instance type is default: t3.micro (free tier) > Latest AMI is probably: /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2 > under subnets click Subnets that you wanted (probably up to 6 available) click all or at least 2. > Under VPCID click your default VPC (choosing the default provided) > click next > on Configure Stack Options we will keep the default choices made. > at the bottom of this page, you'll see Capabilities, click the box saying "I acknowledge that AWS CloudFormation might create IAM resources." > click Next > last page, at the bottom says submit, click it. > If you get a ROLLBACK_IN_PROGRESS (in red) then delete the stack and start over again trying a different yaml file. I recommend amazon.yaml *3 > (If you start over again go to S3 > Under, General Purpose buckets > click the cf-template bucket and "empty" then permanently delete > then empty > then exit  > after that, click the S3 cf-template bucket again > put in the entire name and click delete bucket. > Now you can start over after S3 has been cleared of the previous CloudFormation cf-template bucket, >
#### c.) next, with the valid yaml file. or If you get CREATE_IN_PROGRESS wait for 3 minutes,  until CREATE_COMPLETE appears (in green) > because the stack is running green, you can go to CloudFormation > Stacks > Outputs > in the WebsiteURL field, you'll see the public URL of your EC2 instance. >  Open a browser and go to the URL listed under WebsiteURL. Since there was an echo message in the CloudFormation template, you have that message in your browser.  You should see a simple message such as "Simple Budget Tracker, or "Hello from the ASG" > if you see the message, Congratulations! You did it!  > you could look around at your resources allocated from CloudFormation > Navigate to EC2 with the search bar, and take a look at the EC2 instances. >  under EC2, take a look at your Load Balancer and EC2 Auto-Scaling Groups. (these are on the side tab when you scroll down.) > also, you can navigate with the search bar, to your bucket > take a look at S3 > General Purpose Bucket, > cf-template-xxx 
##(Optional) With an S3 bucket, you could put in my web app if you want, BudgetTracker.html. > go to S3 > General Purpose buckets > choose upload > upload the file > name it BudgetTracker.html > when successfully uploaded and created inside the cf-template > choose Open (located at the top of the newly created BudgetTracker.html bucket in S3, cf-template.) 
(Optional) Instructions for using the BudgetTracker.html web app, with persistent storage.  If you are running this app, in the description input box you must type a description such as Salary or Grocery, or Food or Gift. >  In the amount input box you must type a positive integer number. Floating point or negative numbers will not work. >  Next, you must choose expense or income. > Finally you must click Add Transaction. > Budget Visualizer will display a history of each transaction which can be deleted with the small x next to it. > The balance is displayed at the top, along with expenses and income separated with green or red.
#### d.) Clean-Up. Cleaning up requires you to select the stack created "MyStack-ASG" and click delete. > confirmation wants "delete" typed in. > the stack changes to DELETE_IN_PROGRESS. > next, navigate to S3 to delete the cf-template bucket > choose empty > empty bucket by typing, permanently delete. > choose exit > click the bubble on the bucket name > choose delete > type the name and choose delete bucket. > End of Project.
#### e.) What we did is, transition from a simple template to a high-availability setup, we swapped the single EC2 instance from the original yaml template, for an Auto Scaling Group (ASG) and an Application Load Balancer (ALB). We added a 
##### i.) Launch Template: I used a LaunchTemplate instead of a LaunchConfiguration, as it’s the current AWS best practice.
##### ii.) Security Groups: I added a two-tier security model. The ALB is open to the world, but the Instances only accept traffic from the ALB.
##### iii.) Target Group: This acts as the bridge between your Load Balancer and the Auto Scaling Group.
##### iv.) Parameters: I added VpcId and Subnets parameters, because an ALB requires at least two Availability Zones to function.

## * Resources * 
#### 1. "Introduction To AWS CloudFormation" | Jenna Pederson | " https://www.jennapederson.com/blog/introduction-to-aws-cloudformation/#:~:text=AWS%20CloudFormation%20is%20a%20framework,Mappings%2C%20Resources%2C%20and%20Outputs. "
#### 2. "AWS CloudFormation Tutorial" | "https://www.youtube.com/watch?v=KO0zl6deRfs&t=526s"
#### 3. aws.amazon.com | "Creating Your First Stack" | https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/gettingstarted.walkthrough.html

# Architecture Components
# AWS CloudFormation: The management layer that automates the deployment of the entire stack.
#### a.) Amazon S3: An independent object store used for hosting static assets or software authorization files.
#### b.) Elastic Load Balancer (ALB): Situated in public subnets to receive external traffic and distribute it to the healthy backend instances.
#### c.) Auto Scaling Group (ASG): Manages a minimum of two Amazon Linux 2 EC2 instances across multiple Availability Zones (AZs) for high availability.
#### d.) Default Security Group: Acts as a virtual firewall for the VPC, initially allowing all inbound traffic from other members of the same group while blocking external traffic until rules are added.

# Logical traffic Flow: 
#### 1.) User Request - External users access the application via the Application Load Balancer (ALB) 
#### 2.) Load Balancer - The ALB evaluates health checks and routes traffic to instances within the Auto Scaling Group.
#### 3.) EC2 Instances - At least two Amazon Linux 2 instances (configured via a Launch Template) process the requests.
#### 4.) Data Access - Instances retrieve or store data in the Amazon S3 bucket as required by the application logic.
#### 5.) Security - All traffic within the VPC is governed by the Default Security Group, which by default allows communication between these internal resources.

<img width="1408" height="768" alt="ArchitectureDiagram" src="https://github.com/user-attachments/assets/baf03ffd-be93-44d3-8e91-b5905c85984a" />

Load Balancer.  Resource Map.
<img width="1142" height="252" alt="4 - Copy" src="https://github.com/user-attachments/assets/76c3b1cd-2bf3-4c18-b18a-6db7b63aef6a" />
AWS Template Architecture.
<img width="709" height="246" alt="resMap" src="https://github.com/user-attachments/assets/dd59c29d-48c4-408a-8f91-0fc03a43d549" />



   


