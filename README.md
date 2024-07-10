AWS Cloud Cost Optimization - Identifying Stale Resources
Identifying Stale EBS Snapshots
In this example, we'll create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

Description:
The Lambda function fetches all EBS snapshots owned by the same account ('self') and also retrieves a list of active EC2 instances (running and stopped). For each snapshot, it checks if the associated volume (if exists) is not associated with any active instance. If it finds a stale snapshot, it deletes it, effectively optimizing storage costs.

Create one dummy ec2 instance 
![create-ec2](https://github.com/Suresh-mpt/cost-optimization-ebs/assets/173250817/4c8aac63-1193-475d-bf58-22e58dee095a)
Take the snapshot from volume id which is associated with ec2-instance
![snapshot](https://github.com/Suresh-mpt/cost-optimization-ebs/assets/173250817/3ebd163f-d98f-4bed-82e7-62d5241fc2ef)
Create a lambda function
![create-lambda-func](https://github.com/Suresh-mpt/cost-optimization-ebs/assets/173250817/a6119ac9-94e4-43da-aa94-c14639594a36)
Import the python code in lambda function
![lambda-code](https://github.com/Suresh-mpt/cost-optimization-ebs/assets/173250817/9f6d2117-39e3-4c95-ab0e-831caea11b60)
Create IAM policy for happening communication between lambda with ec2
![create-iam-policy](https://github.com/Suresh-mpt/cost-optimization-ebs/assets/173250817/0f33eb74-a6d7-4146-b9df-3f8679ca904e)
Attach the created policy with role
![attach-policy-role](https://github.com/Suresh-mpt/cost-optimization-ebs/assets/173250817/bf0dbfd9-1daf-4127-982f-bd6314581b4b)
Deploying the code and test the function the execution will success
![func-execution-success](https://github.com/Suresh-mpt/cost-optimization-ebs/assets/173250817/6ed1f9f9-165a-4b99-a032-c9baae932296) 
Snapshot availabe 
![snap available](https://github.com/Suresh-mpt/cost-optimization-ebs/assets/173250817/6f044559-2b57-4940-b4ce-8e18a5170ee1)
Delete the ec2 instance (volume also deleted with ec2 itself) Now the snapshot is in stale mode
Again test the code ,stale snapshot will be get deleted
![exec-snap-deleted](https://github.com/Suresh-mpt/cost-optimization-ebs/assets/173250817/3e017b37-7b70-4d40-8fda-aa16ad259ad7)
Check the snapshot whether its deleted or not ,its deleted!!!
![snap-deleted](https://github.com/Suresh-mpt/cost-optimization-ebs/assets/173250817/c91e95f9-662c-4a14-84d3-4710732355a2)






