# 🎭 KubeChaos - Project Summary

## 📄 Project Overview

**KubeChaos** is a powerful **CLI tool** for Kubernetes chaos engineering that tests application resilience through a wide range of failure scenarios. It is designed to be production-ready, extensible, and cross-platform.

---

## 🗂️ Project Structure

```
kubechaos/
├── .github/workflows/           # GitHub Actions CI/CD
├── dist/                        # Built binaries for all platforms
├── releases/                    # Release packages
├── tests/                       # Test scenarios and documentation
├── main.go                      # Main CLI application
├── chaos_types.go               # Chaos type implementations
├── test_pods.go                 # Test pod management
├── version.go                   # Version information
├── go.mod & go.sum              # Go dependencies
├── README.md                    # Comprehensive usage documentation
├── LICENSE                      # MIT License
├── .gitignore                   # Git ignore rules
├── Makefile                     # Build automation
├── build.sh                     # Cross-platform build script
├── create_release.ps1           # Release packaging script
├── install.sh & install.ps1     # Installation scripts for Unix and Windows
├── Dockerfile & docker-compose.yml # Container support
├── package.json                 # Optional: NPM distribution metadata
├── GITHUB_SETUP.md              # GitHub repository setup guide
├── PROJECT_SUMMARY.md           # This file
└── demo_scripts/                # Testing and demonstration scripts
```

---

## 🚀 Key Features

### ✅ Core Functionality

* ✅ Multiple Chaos Types: CPU stress, memory stress, process killing, memory corruption
* ✅ In-Pod Chaos: Execute directly within target pods using `kubectl exec`
* ✅ Cron Scheduling: Periodic chaos triggers via custom CRON expressions
* ✅ Label Filtering: Target pods by Kubernetes labels and namespaces
* ✅ Dry-Run Mode: Simulate chaos without actual execution
* ✅ Health Monitoring: Real-time pod health tracking
* ✅ CLI-first: Intuitive command-line interface with help/version flags

### 🧪 Chaos Types

1. `pod-delete`: Delete random pods
2. `in-pod-cpu-stress`: CPU stress within containers
3. `in-pod-memory-stress`: Memory stress within containers
4. `in-pod-mixed-stress`: CPU + Memory combined stress
5. `kill-process`: Terminate random processes in containers
6. `corrupt-memory`: Attempt to simulate memory corruption

### 💻 Platform Support

* Windows (x64 and x86)
* Linux (AMD64, x86, ARM64)
* macOS (Intel and Apple Silicon)
* Docker (Container support)

---

## 📦 Installation

### 1. Direct Download (Recommended)

```bash
# For Windows
Invoke-WebRequest -Uri "https://github.com/Verma-Prawal/kubechaos/releases/latest/download/kubechaos-windows-amd64.zip" -OutFile "kubechaos.zip"

# For Linux/macOS
curl -L -o kubechaos https://github.com/Verma-Prawal/kubechaos/releases/latest/download/kubechaos-linux-amd64
chmod +x kubechaos && sudo mv kubechaos /usr/local/bin/
```

### 2. Build from Source

```bash
git clone https://github.com/Verma-Prawal/kubechaos.git
cd kubechaos
go build -o kubechaos main.go test_pods.go chaos_types.go version.go
```

### 3. Docker

```bash
docker build -t kubechaos .
docker run -v ~/.kube:/home/chaos/.kube:ro kubechaos --help
```

### 4. Go Install

```bash
go install github.com/Verma-Prawal/kubechaos@latest
```

---

## 🧑‍💻 CLI Usage Examples

```bash
# View help
kubechaos --help

# Show version
kubechaos --version

# Apply CPU stress to nginx pods
kubechaos -chaos-type=in-pod-cpu-stress -labels="app=nginx" -intensity=7

# Memory stress on cron schedule
kubechaos -cron="*/5 * * * *" -chaos-type=in-pod-memory-stress -labels="app=web"

# Kill processes in production
kubechaos -namespace=prod -chaos-type=kill-process -intensity=3 -duration=30s

# Preview chaos without execution
kubechaos -chaos-type=pod-delete -dry-run -labels="app=critical"
```

---

## 🔧 Technical Implementation

### Core Components

* `main.go`: Entry point and CLI argument parsing
* `chaos_types.go`: Core chaos logic
* `test_pods.go`: Utilities for pod creation/deletion
* `version.go`: Version management and metadata

### Tech Stack

* **Go 1.21+**
* **client-go**: Kubernetes Go client
* **robfig/cron**: Cron parsing and execution
* **Docker**: Containerization
* **GitHub Actions**: CI/CD automation

---

## 🏗️ Architecture Overview

```
CLI Layer (main.go)
      ↓
Chaos Controller
      ↓
Chaos Executors (chaos_types.go)
      ↓
Kubernetes API (client-go)
      ↓
Target Pods
```

---

## 🧪 Testing & Validation

* Bash + PowerShell demo scripts
* Test on real applications
* Scheduled chaos testing
* Health checks during experiments
* Intensity control (1–10)
* Dry-run preview mode

---

## 📦 Release System

* Cross-platform builds: Windows, Linux, macOS
* CI builds via GitHub Actions
* Zip/tarball release packaging
* Docker build support
* SHA256 checksum generation

---

## 🚀 Deployment Options

* Local Binary: Use directly via terminal
* Docker: Run as container
* Kubernetes Job: Deploy in-cluster
* CI/CD: Integrate in GitHub workflows

---

## 🔒 Safety Features

* ✅ Dry-run simulation
* ✅ Duration-based execution
* ✅ Health monitoring
* ✅ Namespace & label targeting
* ✅ Configurable intensity

---

## 🧭 Roadmap

### Near-Term

* Add chaos types: Network delay, I/O stress
* Prometheus/Grafana metrics
* Improved logging and error tracking

### Long-Term

* Web-based dashboard
* Saved chaos experiments
* Slack & Discord notifications
* Kubernetes operator mode
* Open source community engagement

---

## 📚 Documentation

* `README.md`: Full usage guide
* `GITHUB_SETUP.md`: Repository & release setup
* `FAILURE_SCENARIOS.md`: Scenario walkthroughs
* Inline code comments for developers

---

## 📦 External Dependencies

* `client-go`: Kubernetes API client
* `robfig/cron/v3`: Cron scheduler
* `spf13/pflag`: CLI flag parser

System requirements:

* A Kubernetes cluster
* `kubectl` access
* Docker (optional)

---

## 🏆 Project Milestones

* ✅ Complete CLI-based chaos system
* ✅ Six core chaos types
* ✅ Windows/Linux/macOS support
* ✅ Docker and Kubernetes compatibility
* ✅ GitHub Actions automation
* ✅ Release packaging
* ✅ Full documentation
* ✅ Health & safety checks

---

## 🎯 Conclusion

**KubeChaos** offers a production-grade chaos engineering CLI tool built with simplicity, power, and safety in mind. Whether you're stress-testing a web app, validating recovery mechanisms, or building resilience into microservices — **KubeChaos is ready.**

> 🚀 Use it. Break it. Harden your systems.

---
