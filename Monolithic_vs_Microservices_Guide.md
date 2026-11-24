# Simple Interview Guide: Monolithic, Microservices, and CI/CD

## 1. Monolithic Architecture

1. A monolithic application contains all features in one application.
2. All modules normally share one codebase and database.
3. The complete application is built and deployed together.
4. It is simple and suitable for small applications and teams.
5. A small change or scaling requirement can affect the whole application.

**Example:** User, Product, Order, and Payment are packaged in one `shopping-app.jar` file.

![Monolithic architecture](01_monolithic_architecture.png)

| Advantages | Disadvantages |
|---|---|
| Simple to develop and deploy | Whole application must usually be redeployed |
| Easy for a small team | Whole application normally scales together |
| Requires less infrastructure | One failure can affect the complete application |

---

## 2. Microservices Architecture

1. Microservices divide an application into small, independent services.
2. Each service handles one business function, such as Orders or Payments.
3. Services communicate using APIs, gRPC, messages, or events.
4. Each service can be developed, deployed, and scaled independently.
5. Microservices provide flexibility but add operational complexity.

**Example:** User, Product, Order, and Payment run as separate services.

![Microservices architecture](02_microservices_architecture.png)

| Advantages | Disadvantages |
|---|---|
| Services deploy independently | More difficult to design and operate |
| Busy services scale independently | Network and service failures must be handled |
| Teams can work independently | Requires monitoring, security, and automation |

---

## 3. Quick Comparison

| Area | Monolithic | Microservices |
|---|---|---|
| Design | One application | Multiple services |
| Deployment | Deploy everything | Deploy one service |
| Scaling | Scale everything | Scale the required service |
| Complexity | Lower | Higher |
| Best for | Small applications | Large applications and teams |

> **Interview tip:** Start with a monolith when the application is small. Use microservices when independent teams, deployments, and scaling provide real value.

---

## 4. What Is a CI/CD Pipeline?

1. A CI/CD pipeline automates the process from code change to deployment.
2. **Continuous Integration** automatically builds and tests every change.
3. **Continuous Delivery** prepares a release and normally waits for approval.
4. **Continuous Deployment** automatically releases every successful change.
5. CI/CD makes releases faster, consistent, and less error-prone.

![CI/CD pipeline](03_cicd_pipeline.png)

### CI/CD Pipeline Steps

| Step | What It Does | Main Owner or Tool |
|---|---|---|
| 1. Develop | Write the code and unit tests | Developers |
| 2. Push | Store code and trigger the pipeline | GitHub or GitLab |
| 3. Build and test | Compile, test, and scan the application | Jenkins, Maven, SonarQube, Trivy |
| 4. Build image | Package the application as a container image | Docker or Buildah |
| 5. Store image | Push the versioned image to a registry | Quay, Harbor, or Docker Hub |
| 6. Approve and deploy | Approve when required and release the image | QA and DevOps teams |
| 7. Run and monitor | Run the application and watch its health | OpenShift, Kubernetes, Operations, or SRE |

### Small CI/CD Example

A developer updates the **Payment Service** and pushes the code. Jenkins builds and tests it, Docker or Buildah creates `payment-service:2.0`, Quay stores the image, and OpenShift deploys it after approval.

### Team Responsibilities

- **Developers:** Write code and tests and fix pipeline failures.
- **QA team:** Test the feature and approve a release when required.
- **DevOps team:** Maintain the pipeline and deployment platform.
- **Security team:** Define checks and review serious vulnerabilities.
- **Operations or SRE team:** Monitor production and respond to failures.

---

## Final Interview Summary

- **Monolithic:** One application that is built, deployed, and scaled together.
- **Microservices:** Small services that deploy and scale independently.
- **CI:** Build, test, and check every code change automatically.
- **CD:** Deliver or deploy a successful release automatically.
- **Flow:** Code → Git → Build and Test → Image → Registry → Deploy → Monitor.

