# High-Traffic Web Scaling

This project demonstrates how to set up a free scalable AWS web infrastructure to handle high levels of traffic using cloud-based solutions.
You can make a web application that is designed for high-traffic,
But what if the traffic doesn't stop?
That's when this solution comes into the play, involving AWS services like: ALB, ASG, and RDS Read Replicas.

## Architecture

The architecture utilizes AWS services like:
- **Elastic Load Balancer (ELB)** for distributing incoming traffic
- **CloudFront** for CDN caching to reduce latency
- **Auto Scaling** for dynamic adjustment of EC2 instances based on traffic
- **RDS Read Replicas** for scaling database reads
- **S3** for serving static assets


## Prerequisites:
- An AWS account
- AWS CLI configured on your local machine
- Basic knowledge of AWS and infrastructure setup
- Terraform or CloudFormation (depending on your preference)
- Git installed
- An HTTP web application ready for deployment (e.g., a simple Node.js or Python app)


## 1. Set Up Your AWS Account and Create a Free Tier Instance
- Sign up for an AWS account (if you haven't already) and make sure you're using the free tier.
- Launch an EC2 instance using Amazon Linux or Ubuntu for your web server.
![Image](https://github.com/user-attachments/assets/7b7bf0e9-82f3-41c4-bebe-3cd8d2568754)

## 2. Set Up a Web Server (Apache)
- SSH into your EC2 instance: ssh -i your-key.pem ec2-user@your-ec2-public-ip
- Install Apache on your instance:
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd

## 3. Set Up a Load Balancer
- Go to the Elastic Load Balancing section of the AWS Management Console.
- Choose Create Load Balancer and select an Application Load Balancer (ALB).
- Set up the load balancer:
Choose the VPC and availability zones.
Configure security groups (allow HTTP/HTTPS).
Add your EC2 instances to the target group.
![Image](https://github.com/user-attachments/assets/9d22d83e-cb70-4a07-8ebe-cbbfd62dca1c)

## 4. Set Up Auto Scaling
- In the Auto Scaling section, create an Auto Scaling group.
- Link the Auto Scaling group to your load balancer and specify the minimum, maximum, and desired instances.
- Set up scaling policies based on CPU usage or traffic volume.
![Image](https://github.com/user-attachments/assets/8c5d0d6e-d7d7-4862-b1ab-f8169b5c5d25)

## 5. Set Up Amazon CloudFront (CDN) for Caching
- Go to the CloudFront service in the AWS Management Console.
- Create a new distribution:
Choose your EC2 instance as the origin.
Enable caching and specify TTL (time-to-live) settings.
![Image](https://github.com/user-attachments/assets/3a301d8e-bf2b-48aa-90e7-41f3427e55cf)

## 6. Set Up Read Replicas in RDS
- Enable Read Replicas to improve database read performance.
- Go to the RDS dashboard and create a read replica of your main database instance.

## 7. Set Up Monitoring with CloudWatch
- Set up CloudWatch for monitoring the health of your instances, load balancer, and auto-scaling activity.
- Create CloudWatch alarms for instance health and scaling triggers.
![Image](https://github.com/user-attachments/assets/76779e73-2d98-4377-88c7-501067a02153)

## 8. Test and Optimize
- Generate traffic to simulate high-traffic conditions.
- Monitor the scaling behavior and performance of your infrastructure.

## Final notes
- This represents how AWS can handles high traffic
- You can tweak instance types, labels, and connections (it won't be free-tier)
- Save different versions as your infrastructure evolves
