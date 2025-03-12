# CloudFront:

Role: CloudFront serves as the entry point for user requests. It caches static content and reduces latency by serving data from edge locations worldwide.
Interaction: Once a request reaches CloudFront, it checks if the requested content is cached. If not, CloudFront forwards the request to the Elastic Load Balancer (ELB).

# ELB
Role: ELB distributes incoming traffic across multiple EC2 instances in the Auto Scaling Group, ensuring high availability and load distribution.
Interaction: After CloudFront forwards the request, ELB routes the traffic to one of the healthy EC2 instances running your application.

# ASG
Role: Auto Scaling automatically adjusts the number of EC2 instances based on incoming traffic. It ensures that the application has enough resources during traffic spikes and reduces resources during low traffic.
Interaction: The ASG is tied to ELB, ensuring that the instances it launches are registered with the load balancer.

# RDS
Role: RDS provides a relational database backend for dynamic data storage. Read Replicas ensure the application can scale database reads efficiently without overwhelming the primary database.
Interaction: EC2 instances interact with RDS to fetch dynamic data and perform CRUD operations.

# S3
Role: S3 is used to store static assets such as images, videos, stylesheets, and JavaScript files.
Interaction: Static assets are served from S3 through CloudFront, ensuring fast global delivery.
