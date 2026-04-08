# Final-Project-AWS-Portfolio-Project
design, deploy, and document a cloud architecture -  Compute Services -  Infrastructure &amp; Supporting Services  - Architecture Requirements- Working Deployment

Based on your template, this architecture establishes a highly available web server environment. Traffic enters via the Application Load Balancer (ALB), which is governed by the ALBSecurityGroup to allow public HTTP access. The ALB then forwards requests to the Auto Scaling Group (ASG).
