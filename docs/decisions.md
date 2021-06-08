# Decision Log

This project captures important decisions in the evolution of the project with [architectural decision records](https://adr.github.io/). These records provide a sense of context, trade-offs, and direction taken at various project cross-roads. The goals are to preserve an understanding of how the project has grown, and the conditions under which previous decisions might be revisted.

Each decision might have a **history** note, indicating where changes to earlier decisions might cause revisiting the current decision.

Decision records should attempt to follow the Y-statement format for consistency:

```md
In the context of **<use case/user story u>**, facing **<concern c>** we decided for **<option o>** and neglected <other options>, to achieve <system qualities/desired consequences>, accepting <downside d/undesired consequences>, because <additional rationale>.
```

## Decision: Frontend Avoids JS Frameworks

In the context of the **frontend tech stack**, deciding to use plain JavaScript + libraries or use a rich framework such as Angular, React, or Vue, we decided to **use plain JavaScript to keep the frontend implementation approachable to backend developers**, accepting we will be less effective engaging with frontend engineers attempting to use serverless and may eventually outgrow a plain JavaScript code architecture.

* **Date:** 2021/03

## Decision: Backend Default Language is Python

In the context of the **backend tech stack**, deciding which languages to use for a web backend and API we decided to **default to Python** to maximize our use of language skills on the team that are also common across the industry, accepting many enterprise organizations use other languages for application implementation and may learn less from the application codebase.

* **Date:** 2021/03
* **Note:** The application code is not the focus for learning in this app.

## Decision: Monorepo for Code Management

In choosing how to **host code for development**, deciding between a monorepo and 3+ repositories, we decided to use a **monorepo pattern** to keep discovery & maintainability manageable, accepting additional complexity in pipeline configuration, needing extra caution to avoid creating an unintentional "decoupled monolith", and leaving use cases of multi-repo management outside our scope.

* **Date:** 2021/03

## Decision: Use Terraform for Infrastructure Management

In choosing how to **manage our Cloud Infrastructure**, deciding between ad hoc, scripted, or terraform-based approach, we decided to **use Terraform** in order to help customers engage with infrastructure as code in a serverless context, accepting more contributors will need extra time learning Terraform in order to contribute infrastructure changes.

* **Date:** 2021/03

## Decision: Use Terraform in a Single Directory

In choosing how to **manage our Terraform configuration for different services**, deciding between a central directory or spreading terraform config throughout the repository, we decided to use a **central directory** because it's easier to understand at the scale of this project, accepting it will be a less effective example for showing how multiple teams can separately own the infrastructure of their services.

* **Date:** 2021/03

## Decision: Deploy code with gcloud

In choosing how to **deploy services**, deciding between using Terraform to manage deployment, use gcloud "imperatively", or use product-specific configuration-as-code features, we decided to use **gcloud to imperatively manage services** because we want to keep infrastructure and software management separate and deployment operations familiar, accepting we are not addressing the ambiguity of service configuration including some infrastructural pieces.

* **Date:** 2021/03

## Decision: Use GitHub Actions for Static Analysis

In choosing how to **run static analysis and workflow automations**, deciding between Cloud Build and GitHub Actions, we decided to **use GitHub Actions because of it's simpler syntax, deeper GitHub integration, and thriving ecosystem of examples**, accepting this will create fewer opportunities to provide feedback to the Cloud Build product team.

* **Date:** 2021/03

## Decision: Rollbacks for Cloud Run use Traffic Splitting

In choosing how to **handle rollbacks for Cloud Run services**, deciding between
reverting deployments to a previous stable revision and rerouting traffic to a previous known-good revision, we decided to **re-route traffic** for highest recovery speed and least chance of unintended side-effects, accepting this capability is not consistent across all hosting platforms and does not address state management.

* **Date:** 2021/03