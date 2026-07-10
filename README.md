# AWS Load Balancing Documentation

## Objective

The aim of this task was to make sure our application could be accessed through a **Load Balancer**. A Load Balancer shares traffic between servers so that no single server becomes overloaded.

---

## Step 1 – Create a Target Group

A **Target Group** is where the Load Balancer sends traffic.

1. Go to **EC2** in the AWS Console.
2. Select **Target Groups**.
3. Click **Create target group**.
4. Choose **Instances** as the target type.
5. Give the target group a name ending in **`-tg`**.
   - Example: `tech610-tg`
6. Leave the default settings unless instructed otherwise.
7. Register the EC2 instances that will receive traffic.
8. Click **Create target group**.

---

## Step 2 – Create an Application Load Balancer

The **Application Load Balancer (ALB)** receives requests from users and sends them to the servers in the target group.

1. Go to **Load Balancers**.
2. Click **Create Load Balancer**.
3. Choose **Application Load Balancer**.
4. Give the Load Balancer a name.
5. Select **Internet-facing**.
6. Select **IPv4**.
7. Choose **all Availability Zones**.
8. Attach the target group created earlier.
9. Click **Create**.

---

## Step 3 – Create an Auto Scaling Group

An **Auto Scaling Group** manages the EC2 instances.

### Settings Used

- **Health Check:** Elastic Load Balancer (ELB)
- **Desired Capacity:** 2 instances
- **Minimum Capacity:** 2 instances
- **Maximum Capacity:** 2 instances
- **Cooldown Period:** 90 seconds

This ensures there are always **2 running EC2 instances**.

---

## How It Works

1. A user visits the application.
2. The request goes to the **Application Load Balancer**.
3. The Load Balancer checks which server is healthy and available.
4. The request is sent to one of the EC2 instances in the **Target Group**.
5. If one server fails, the Load Balancer automatically sends traffic to the other healthy server.

---

## Why We Use a Load Balancer

- Distributes traffic across multiple servers.
- Prevents one server from becoming overloaded.
- Improves reliability and availability.
- Keeps the application running if one server fails.
- Works with Auto Scaling to manage EC2 instances.

---

## Summary

| Setting | Value |
|---------|-------|
| **Load Balancer Type** | Application Load Balancer (ALB) |
| **Target Group** | Created with `-tg` at the end of the name |
| **Health Check** | Elastic Load Balancer (ELB) |
| **Desired Capacity** | 2 |
| **Minimum Capacity** | 2 |
| **Maximum Capacity** | 2 |
| **Cooldown Period** | 90 seconds |
