# Task 7: Monitor System Resources Using Netdata

## Objective
Install Netdata and visualize system and application performance metrics in real-time using Docker.

## Tools Used
- **Docker Desktop** (version 28.4.0)
- **Netdata** (open-source monitoring tool)
- **Web Browser** (for dashboard access)
- **Windows PowerShell** (command execution)

## Steps Followed

### 1. Prerequisites Check
✅ Verified Docker installation:
```bash
docker --version
# Output: Docker version 28.4.0, build d8eb465
```

✅ Created project structure:
```
netdata-monitoring-task7/
├── screenshots/
├── commands.txt
└── README.md
```

### 2. Netdata Installation
Pulled and ran the Netdata Docker container:
```bash
docker run -d --name=netdata -p 19999:19999 netdata/netdata
```

**What this command does:**
- `docker run` - Creates and starts a container
- `-d` - Runs in detached mode (background)
- `--name=netdata` - Names the container "netdata"
- `-p 19999:19999` - Maps port 19999 (host:container)
- `netdata/netdata` - Uses the official Netdata image

### 3. Verification
Verified container is running:
```bash
docker ps
# Shows: netdata container with STATUS "Up" on port 19999
```

### 4. Dashboard Access
✅ Accessed the dashboard at: **http://localhost:19999**

### 5. Metrics Monitored

#### CPU Usage
- **Location**: System → CPU
- **Metrics**: Real-time CPU utilization across all cores
- **Observed**: CPU usage patterns, system vs user time
- **Update Frequency**: Every second

#### Memory Usage
- **Location**: System → Memory  
- **Metrics**: RAM usage, cache, buffers, swap
- **Observed**: Memory allocation patterns, available memory
- **Key Insights**: Real-time memory consumption tracking

#### Disk Performance
- **Location**: Disk → Disk Space & I/O
- **Metrics**: Read/write operations, disk space usage
- **Observed**: I/O performance, disk utilization
- **Features**: Per-disk breakdown

#### Docker Containers
- **Location**: Containers section
- **Metrics**: Per-container CPU, memory, network usage
- **Observed**: Netdata container resource consumption
- **Benefits**: Container-level monitoring

### 6. Key Observations
🔍 **Performance Insights:**
- CPU usage remained stable around 5-15% during normal operation
- Memory usage showed efficient allocation with minimal swap activity
- Disk I/O operations were within normal parameters
- Container monitoring provided clear resource usage visibility

🎯 **Dashboard Features:**
- Real-time updates every second
- Interactive charts with zoom/pan capabilities
- Color-coded alerts and thresholds
- Comprehensive system overview

### 7. Advanced Features Explored

#### Interactive Charts
- ✅ Zoom: Click and drag on charts
- ✅ Pan: Shift + drag to navigate
- ✅ Reset: Double-click to reset view
- ✅ Highlight: Hover over legend items

#### Time Windows
- ✅ Last minute view
- ✅ Last hour view  
- ✅ Last day view
- ✅ Custom time ranges

#### Alert System
- ✅ Built-in health checks
- ✅ Configurable thresholds
- ✅ Real-time alert notifications

## Screenshots
All screenshots are available in the `/screenshots` directory:

1. **dashboard-overview.png** - Main dashboard showing overall system metrics
2. **cpu-metrics.png** - Detailed CPU utilization charts
3. **memory-metrics.png** - Memory usage graphs and statistics
4. **docker-containers.png** - Container monitoring view
5. **chart-detail.png** - Expanded chart view with detailed metrics

## Interview Questions & Answers

### 1. What does Netdata monitor?
Netdata monitors comprehensive system and application metrics including:
- **System Resources**: CPU, RAM, disk, network interfaces
- **Application Performance**: Process-level metrics, application response times
- **Container Metrics**: Docker container resource usage
- **Services & Processes**: System services, running processes
- **Hardware Sensors**: Temperature, power consumption (when available)
- **Custom Metrics**: Via 300+ built-in collectors and plugins

### 2. How do you view real-time metrics?
Real-time metrics are viewed through:
- **Web Dashboard**: Access via http://localhost:19999
- **Auto-Updates**: Metrics refresh every second automatically
- **Interactive Charts**: Time-series data with zoom/pan functionality
- **Live Data**: No page refresh needed, streaming data visualization
- **Mobile Support**: Responsive design for mobile access

### 3. How is Netdata different from Prometheus?
**Netdata**:
- ✅ Zero-configuration setup
- ✅ Instant visualization with built-in dashboard
- ✅ Per-second metrics collection
- ✅ Minimal resource overhead
- ✅ Standalone operation

**Prometheus**:
- 🔧 Requires configuration setup
- 🔧 Pull-based metric collection
- 🔧 Needs Grafana for visualization
- 🔧 Better for large-scale distributed systems
- 🔧 More complex alerting rules

### 4. What is a collector?
A **collector** is a plugin/module that gathers specific metrics:
- **Built-in Collectors**: 300+ collectors included (CPU, memory, disk, etc.)
- **Examples**: MySQL collector, Docker collector, Nginx collector
- **Custom Collectors**: Can be written in Python, Go, or shell scripts
- **Auto-Detection**: Netdata automatically detects and enables relevant collectors
- **Configuration**: Collectors can be configured via YAML files

### 5. What are some performance KPIs to watch?
**Critical Performance KPIs**:
- 🚨 **CPU Utilization**: >80% sustained indicates potential bottleneck
- 🚨 **Memory Usage**: High swap activity suggests memory pressure
- 🚨 **Disk I/O Wait Time**: High iowait indicates disk bottleneck
- 🚨 **Network Latency**: Response time degradation
- 🚨 **Application Response Time**: User experience metric
- 🚨 **Error Rates**: Application/service failure indicators
- 🚨 **Load Average**: System load distribution
- 🚨 **Database Connections**: Connection pool utilization

### 6. How to deploy Netdata on a VM?
**VM Deployment Steps**:
```bash
# 1. SSH into VM
ssh user@vm-ip-address

# 2. Install Docker (if not present)
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh

# 3. Run Netdata container
docker run -d --name=netdata -p 19999:19999 netdata/netdata

# 4. Configure firewall
sudo ufw allow 19999/tcp

# 5. Access via VM IP
# http://vm-ip-address:19999
```

**Alternative - Native Installation**:
```bash
bash <(curl -Ss https://my-netdata.io/kickstart.sh)
```

### 7. How does Netdata alerting work?
**Alert System Components**:
- **Health Checks**: Built-in health monitoring rules
- **Thresholds**: Configurable warning/critical levels
- **Alert States**: Clear → Warning → Critical
- **Notification Methods**: 
  - Email notifications
  - Slack integration
  - Discord webhooks
  - Custom HTTP endpoints
- **Configuration**: Via `/etc/netdata/health.d/` files
- **Silence Options**: Temporary alert suppression

### 8. What is a dashboard in this context?
A **dashboard** in Netdata context is:
- **Web Interface**: Browser-based visualization platform
- **Real-time Display**: Live updating metrics and charts
- **Organized Sections**: Grouped by system components (CPU, Memory, Disk, etc.)
- **Interactive Elements**: Clickable charts, expandable sections
- **Responsive Design**: Works on desktop, tablet, and mobile
- **Customizable**: Can be themed and configured
- **Multiple Views**: Overview, detailed, and comparison modes

## Technical Implementation Details

### Container Configuration
```bash
# Basic setup
docker run -d --name=netdata -p 19999:19999 netdata/netdata

# Enhanced setup with additional privileges (if needed)
docker run -d --name=netdata -p 19999:19999 --cap-add SYS_PTRACE netdata/netdata

# Production setup with volume mounting
docker run -d --name=netdata -p 19999:19999 \
  -v /etc/passwd:/host/etc/passwd:ro \
  -v /etc/group:/host/etc/group:ro \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  netdata/netdata
```

### Performance Impact
- **CPU Usage**: ~1-2% CPU overhead
- **Memory Usage**: ~100-200MB RAM
- **Network**: Minimal bandwidth for dashboard access
- **Storage**: Log rotation handles disk usage

## Learning Outcomes
✅ **Monitoring Expertise**: Gained hands-on experience with real-time system monitoring
✅ **Docker Proficiency**: Learned containerized application deployment
✅ **Performance Analysis**: Understanding of system resource management principles
✅ **Dashboard Navigation**: Proficiency in metric visualization and interpretation
✅ **Alerting Concepts**: Knowledge of monitoring alerting strategies
✅ **DevOps Skills**: Practical monitoring tool implementation

## Cleanup Commands
```bash
# Stop the container
docker stop netdata

# Remove the container
docker rm netdata

# Remove the image (optional - frees ~200MB)
docker rmi netdata/netdata

# Verify cleanup
docker ps -a
```

## Troubleshooting Guide

### Common Issues & Solutions

**Issue 1: Port Already in Use**
```bash
# Solution: Use different port
docker run -d --name=netdata -p 20000:19999 netdata/netdata
# Access at http://localhost:20000
```

**Issue 2: Container Won't Start**
```bash
# Check logs
docker logs netdata

# Restart Docker daemon (Windows)
# Restart Docker Desktop application
```

**Issue 3: Dashboard Not Loading**
- Wait 10-20 seconds after container start
- Try http://127.0.0.1:19999 instead
- Check Windows Firewall settings
- Verify container status: `docker ps`

**Issue 4: Missing Metrics**
```bash
# Run with additional privileges
docker run -d --name=netdata -p 19999:19999 --cap-add SYS_PTRACE netdata/netdata
```

## Quick Reference Commands
```bash
# Essential Commands
docker ps                    # Check running containers
docker start netdata        # Start stopped container
docker stop netdata         # Stop running container
docker restart netdata      # Restart container
docker logs netdata         # View container logs
docker exec -it netdata bash # Access container shell

# System Commands
docker system df            # Check Docker disk usage
docker system prune         # Clean up unused resources
```

## Additional Resources
- 📚 [Official Netdata Documentation](https://learn.netdata.cloud/)
- 🐳 [Docker Documentation](https://docs.docker.com/)
- 📊 [Monitoring Best Practices](https://sre.google/workbook/monitoring/)
- 🔧 [Grafana + Prometheus Comparison](https://prometheus.io/docs/introduction/comparison/)

## Project Status
- ✅ **Container Running**: Netdata successfully deployed
- ✅ **Dashboard Accessible**: http://localhost:19999
- ✅ **Metrics Collected**: CPU, Memory, Disk, Container data
- ✅ **Screenshots Taken**: All required dashboard views captured
- ✅ **Documentation Complete**: Comprehensive README and commands
- ✅ **Interview Questions**: All questions answered with detailed explanations

---

**Task Completion**: Successfully implemented Netdata monitoring solution with Docker, explored all key features, documented the process comprehensively, and prepared for GitHub submission.

**Next Steps**: Upload to GitHub repository and submit before 10:00 PM deadline. 🚀
