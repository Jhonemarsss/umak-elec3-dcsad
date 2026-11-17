# Lab 1 Submission

## Part B
Error Action Name: You are not authorized to perform this operation. User: arn:aws:iam::548387266019:user/dcsad-g01 is not authorized to perform: ec2:RunInstances on resource: arn:aws:ec2:ap-southeast-1:548387266019:instance/* because no identity-based policy allows the ec2:RunInstances action.

## Part C
**Policy Statement Blanks:**
- `"Action"`: ec2:RunInstances
- `"Resource"`: arn:aws:ec2:ap-southeast-1:548387266019:instance/*
- `"ec2:InstanceType"`: t3.micro

## Part D
**Security Group Error Text:** You are not authorized to perform this operation. User:arn:aws:iam::548387266019:user/dcsad-g01 is not authorized to perform: ec2:CreateSecurityGroup on resource: arn:aws:ec2:ap-southeast-1:548387266019:security-group/* with an explicit deny or missing required tag

**Running Instance Time:** November 17, 2026, 2:42:54 PM (PHT)

## Part E
**t3.small / Tokyo Denial Error:** You are not authorized to perform this operation. User: arn:aws:iam::548387266019:user/dcsad-g01 is not authorized to perform: ec2:RunInstances on resource: arn:aws:ec2:ap-southeast-1:548387266019:instance/* with an explicit deny in a permissions boundary: arn:aws:iam::548387266019:policy/umak-lab-boundary.


## Part F Questions
1. Which action did the Part B error name? ec2:RunInstances
2. In your policy, which condition limits `ec2:RunInstances`? The ec2:InstanceType condition limits the action to t3.micro
3. After you attached `ec2:*` on `*`, why was `t3.small` still denied? Name the boundary statement. It was still denied because the permissions boundary contains an explicit Deny for instance types other than t3.micro. The statement is DenyAnyInstanceTypeButT3Micro.
4. Why is `ec2:*` on `*` a poor policy even with a boundary? It grants unnecessarily broad EC2 permissions and violates the principle of least privilege. It can allow actions beyond what the user actually needs, even if the permissions boundary limits the maximum permissions.
5. In two sentences: what does the boundary control that your policy cannot? The permissions boundary controls the maximum permissions an IAM user can have, regardless of what the identity-based policy allows. It can explicitly deny actions, restrict instance types, and limit access to specific AWS regions and resources.
