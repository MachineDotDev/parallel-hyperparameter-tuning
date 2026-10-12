[![Machine](./docs/github-repo-banner.png)](https://machine.dev/)

Machine supercharges your GitHub Workflows with seamless GPU acceleration. Say goodbye to the tedious overhead of managing GPU runners and hello to streamlined efficiency. With Machine, developers and organizations can effortlessly scale their AI and machine learning projects, shifting focus from infrastructure headaches to innovation and speed.


# Parallel Hyperparameter Tuning

This repository provides a complete, automated workflow for GPU-accelerated hyperparameter tuning of a ResNet model using GitHub Actions powered by Machine.dev. It systematically explores combinations of key training parameters—such as learning rates and batch sizes—to identify the optimal configuration for training a ResNet model on the CIFAR-10 dataset.

---

### ✨ **Key Features**

- **⚡ GPU Acceleration:** Efficiently train and evaluate models using GPUs via [Machine](https://machine.dev)
- **🧪 Systematic Tuning:** Automate the exploration of multiple hyperparameter combinations
- **📊 Performance Comparison:** Automatically aggregate and compare model metrics
- **📤 Artifact Storage:** Conveniently store and retrieve metrics and comparison results using GitHub Actions artifacts
- **📈 Easy Interpretation:** Identify the best-performing configuration quickly with structured CSV outputs

---

### 📁 **Repository Structure**

```
├── .github/workflows/
│   └── resnet-hyperparameter-tuning.yaml   # Workflow for hyperparameter tuning
├── train.py                                # Script to train and evaluate ResNet
├── compare_metrics.py                      # Script to aggregate and compare metrics
└── requirements.txt                        # Python dependencies
```

---

### ▶️ **Getting Started**

#### 1. **Use This Repository as a Template**
Click the **Use this template** button at the top of this page to create your own copy.

#### 2. **Set Up GPU Runners**
Ensure your repository uses Machine GPU-powered runners. No additional configuration is required if you're already using Machine.dev.

#### 3. **Run the Workflow**

- Trigger the workflow manually in GitHub Actions (`workflow_dispatch`)
- The workflow automatically runs training jobs for each combination of hyperparameters defined in the matrix:

  ```yaml
  matrix:
    learning_rate: [0.001, 0.0005]
    batch_size: [32, 64]
  ```

#### 4. **Monitor and Review Results**

- Training progress and metrics are logged during each workflow execution
- Performance metrics for each hyperparameter set are saved as artifacts (`metrics-{learning_rate}-{batch_size}`)
- A final comparison of all training results is saved as `model_comparison.csv` in the artifact `comparison-results`

---

### 🔑 **Prerequisites**

- GitHub account
- Access to [Machine](https://machine.dev) GPU-powered runners

_No local installation necessary—all processes run directly within GitHub Actions._

---

### 📄 **License**

This repository is available under the [MIT License](LICENSE).

---

### 📌 **Notes**

- This hyperparameter tuning template specifically targets ResNet models trained on the CIFAR-10 dataset but can easily be adapted for other models, datasets, and tasks with minimal modifications.

- This repository is currently open for use as a template. While public forks are encouraged, we are not accepting Pull Requests at this time.

_For questions or concerns, please open an issue._

## Machine runtime limits

These workflows run on Machine GPU runners. Install the GitHub App on this
repository before starting a job. Start with $10 of free GPU time. No charge,
no commitment.

Unpaid teams can run one job at a time, for up to 30 minutes. Buy compute or a
plan before running a longer training or evaluation job. A larger
`timeout-minutes` value in GitHub doesn't remove the platform limit.

The matrix has four jobs. On a free team, set `strategy.max-parallel: 1` to
submit them one at a time; otherwise queued jobs can hit the admission timeout.
Paid concurrency depends on your team. Each matrix leg has a distinct runner
label so another leg cannot take its runner.

See [billing and limits](https://machine.dev/docs/guides/billing/) for current limits.
