# devops-design-assignment.



## 📊 Architecture Diagram



## 1. UI (Frontend) Design

- **Hosting**: S3 + CloudFront for static React/Angular/Vue builds.
- **Scaling**: Stateless frontend scales horizontally via S3 and CloudFront.
- **Traffic Routing**: Route53 → CloudFront → S3.
- **Caching/CDN**: CloudFront edge caching improves performance.
- **Availability Zones**: Multi-AZ redundancy via Route53 and CloudFront.



## 2. API (Backend) Design

- **Hosting**: ECS Fargate for containerized Node/Python/Go services.
- **Traffic Entry**: Application Load Balancer (ALB) routes traffic to ECS tasks.
- **Secrets Management**: AWS Secrets Manager stores DB credentials and API keys.
- **DB Communication**: ECS communicates securely with RDS via private subnets and security groups.
- **Scaling**: ECS service auto-scaling based on CloudWatch metrics.



## 3. Database Design

- **Engine**: Amazon RDS (Postgres/MySQL).
- **Scaling**: Read replicas, vertical scaling, Multi-AZ deployment.
- **Backup Plan**: Automated snapshots, PITR enabled.
- **Migration Strategy**: Schema versioning via Flyway/Liquibase.



## 4. CI/CD Pipeline

- **Tool**: GitHub Actions.
- **Triggers**: PR merge or push to `main`.
- **Build Stage**: Install dependencies, lint, compile.
- **Testing**: Unit and integration tests.
- **Deployment**: 
  - Frontend → S3 + CloudFront invalidation.  
  - Backend → ECS rolling updates.
- **Health Checks**: ALB health checks + CloudWatch alarms.
- **Promotion Strategy**: Dev → Stage → Prod via environment branches.




- [x] Diagram uploaded (`diagram.png` or `diagram.pdf`)
- [x] README.md with explanations
- [x] Covers UI, API, DB, CI/CD
