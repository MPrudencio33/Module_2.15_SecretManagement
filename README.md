# Module_2.15_SecretManagement
Answers to Assignment on Module 2.15 Secrets Management in AWS

1. What is needed to authorize your EC2 to retrieve secrets from the AWS Secret Manager?-
   ANSWER:
   Set up IAM permissions and ensure the instance can assume them.
   The following are the high-level details:
   a. Setup IAM role with secretsmanager:GetSecretValue permission
   b. Attach the IAM role to the EC2 instance
   c. Ensure networking allows access to Secrets Manager (public endpoint or VPC endpoint)
   d. Use AWS SDK/CLI on the EC2 (it fetches temporary creds via instance profile)

3. Derive the IAM policy (i.e. JSON)?-
   Using the secret name secret name prod/cart-service/credentials as the specific resource for access
   ANSWER:

{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": [
				"secretsmanager:GetSecretValue"
			],
			"Resource": "arn:aws:secretsmanager:us-east-1:255945442255:secret:prod/cart-service/credentials-xlNtF0"
		}
	]
}
