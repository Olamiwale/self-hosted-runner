# Self-Hosted GitHub Actions Runner Setup

## Overview
This project demonstrates how to set up a **self-hosted GitHub Actions runner** on a local PC and run a **test pipeline**.


## Steps to Reproduce

### 1. Create Repository
Created a new GitHub repo named `self-hosted-runner`.

### 2. Register the Runner

- Went to **Settings → Actions → Runners → New self-hosted runner**

- Selected runner image ( Linux )

- Selected default x64 Architecture 

- Downloaded and configured the runner: 

follow the command prompt
 
$ mkdir actions-runner && cd actions-runner# Download the latest runner package

$ curl -o actions-runner-linux-x64-2.329.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.329.0/actions-runner-linux-x64-2.329.0.tar.gz# (Optional: To validate the hash)

$ echo "194f1e1e4bd02f80b7e9633fc546084d8d4e19f3928a324d512ea53430102e1d  actions-runner-linux-x64-2.329.0.tar.gz" | shasum -a 256 -c# Extract the installer

$ tar xzf ./actions-runner-linux-x64-2.329.0.tar.gz


### 3. Verify Connection

After registration, the terminal displayed:

```
√ Connected to GitHub
Runner listening for Jobs
```

### 4. Add Workflow File

Created `.github/workflows/test-runner.yml` to test the created self-hosted runner


self-hosted-runner-demo/
├── .github/
│   └── workflows/
│       └── test-runner.yml
└── README.md



### 5. Push and Trigger

Committed and pushed changes.
Observed workflow successfully executed on **my local PC**.



## Challenges & Solutions

Runner failed to connect due to firewall


Workflow stuck in “Waiting for Runner”



## Security Considerations

* Generated runner **token** is **temporary** (valid for a few minutes only).
* Never commit or expose the token in any file.

* Regularly **remove inactive runners**
* Use **labels** to isolate environments (e.g., dev-runner vs prod-runner).
* Keep system and dependencies updated to avoid vulnerabilities.

---

## What I'd Do Differently in Production


 **Isolation**    Run self-hosted runner in a VM or Docker container

 **Scaling**      Use multiple runners with autoscaling                        
 **Security**     Restrict network access and secrets to specific environments 
 **Monitoring**   Add logging/monitoring       
 **Maintenance**  Automate updates and cleanup for old runner versions         



## 📎 Repository

🔗 [GitHub Repository Link](https://github.com/<your-username>/self-hosted-runner-demo)


