# Golden AMI and Elastic Beanstalk

# Golden AMI

A **Golden AMI** is a **prebuilt master machine image** for EC2: think of it like a **standard company laptop template** with the OS, patches, agents, and approved software already installed. You create it once, then launch many identical servers from it for **consistency, faster deployment, and fewer configuration mistakes**.

**Key Use Case**

- Choose **Golden AMI** when you need to launch **many identical EC2 instances** quickly with **preinstalled software and hardened settings**.

**Exam Tip**

**If you see “standardized EC2 servers with preinstalled software / faster bootstrapping,” think *Golden AMI*.**

**Main Difference**

**Golden AMI vs EC2 Image Builder:** **Golden AMI** is the **finished standardized image**; **EC2 Image Builder** is the **service that automates creating, testing, and distributing** those images.

![golden-ami.png](Golden%20AMI%20and%20Elastic%20Beanstalk/golden-ami.png)

# Elastic Beanstalk

**Elastic Beanstalk** is like giving AWS your **application code** and asking it to set up the **servers, load balancer, scaling, and health checks** for you. It is a **managed app deployment service** for web apps and services, but your app still runs on resources like **EC2** underneath.

**Key Use Case**

- Choose **Elastic Beanstalk** when you want to **deploy a web app quickly** without manually building the EC2, load balancing, and Auto Scaling setup yourself.

**Exam Tip**

**If you see “just upload code and AWS handles provisioning, load balancing, scaling, and monitoring,” think *Elastic Beanstalk*.**

**Main Difference**

**Elastic Beanstalk vs ECS/Fargate:** **Beanstalk** is simpler **platform-as-a-service** style deployment for apps, while **ECS/Fargate** is more about **container orchestration and container-level control**. Elastic Beanstalk can also deploy **Docker-based** apps, but it abstracts more of the infrastructure setup.

![elastic-beanstalk.png](Golden%20AMI%20and%20Elastic%20Beanstalk/elastic-beanstalk.png)