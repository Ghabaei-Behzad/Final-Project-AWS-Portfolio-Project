## Deployment. 
Create Stack > Under Prerequisite - Prepare Template > click Build from Infrastructure Composer > Create a Template in Infrastructure Composer > click Create in Infrastructure Composer > At the top there are two choices Canvas/Template > choose Template > then choose between Yaml/Json > choose Yaml. Paste in the yaml file from this github repo.> Validate > if "Valid" then great!, if "invalid", then try my secondaryTemplate.yaml or amazon.yaml (but amazon.yaml doesn't have LB or ASG) > create/update template > a pop up displays the recently created S3 bucket called something like cf-template-xxxx  > click confirm and continue to cloudformation > next > provide a stack name i.e: "MyStack-ASG" > leave default on instance and ami, they are filled > then add your subnets (at least 2) > select the VPCID, click and fill it (default) > next > next (review) > submit

<img width="1366" height="649" alt="1" src="https://github.com/user-attachments/assets/4a600d6f-6555-4648-9f61-b9be9f1f74ec" />
<img width="1366" height="653" alt="2" src="https://github.com/user-attachments/assets/614dfce3-9329-40b3-806f-8533a3b6e99b" />
<img width="1366" height="649" alt="3" src="https://github.com/user-attachments/assets/9f810973-b8f6-4f62-9567-5a259b47478c" />
<img width="1366" height="641" alt="4" src="https://github.com/user-attachments/assets/5a8081c8-eedc-43ac-9e20-b5c96f346aa5" />
<img width="1366" height="641" alt="5" src="https://github.com/user-attachments/assets/0e68deae-a45b-42d9-96b6-ab0d235db259" />
<img width="1366" height="649" alt="6" src="https://github.com/user-attachments/assets/04db4ebb-bbe5-4d3d-b151-6681fa826dc5" />
<img width="709" height="246" alt="resMap" src="https://github.com/user-attachments/assets/558cfed3-20d6-47a5-9598-e07dd02eeb0c" />

Here are a few output samples:
<img width="1366" height="673" alt="Browser" src="https://github.com/user-attachments/assets/a10e8939-4450-4649-8ca0-cfdbcf81203d" />
<img width="1366" height="669" alt="BudgetTracker" src="https://github.com/user-attachments/assets/bd4e533b-4327-4115-9531-b5e6c135d5e9" />







