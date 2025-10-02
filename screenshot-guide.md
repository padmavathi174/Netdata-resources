# Netdata Dashboard Screenshot Guide

## 🚀 Quick Start
Your Netdata container is running! Access the dashboard at: **http://localhost:19999**

## 📸 Required Screenshots

### Screenshot 1: Dashboard Overview (`dashboard-overview.png`)
**What to capture:**
- **URL**: http://localhost:19999
- **Focus**: Main landing page showing overall system health
- **Key elements**: System overview, main navigation, real-time charts
- **Tip**: Wait 30 seconds for data to populate before taking screenshot

### Screenshot 2: CPU Metrics (`cpu-metrics.png`)
**Navigation:** System → CPU
**What to capture:**
- CPU utilization charts
- Per-core CPU usage
- System vs User CPU time
- Load average graphs
- **Tip**: Click on a CPU chart to expand it for detailed view

### Screenshot 3: Memory Metrics (`memory-metrics.png`)
**Navigation:** System → Memory
**What to capture:**
- RAM usage graphs
- Memory allocation breakdown
- Cache and buffer usage
- Swap activity (if any)
- Available memory indicators

### Screenshot 4: Docker Containers (`docker-containers.png`)
**Navigation:** Containers (in left sidebar)
**What to capture:**
- Container list showing the Netdata container
- Per-container resource usage
- CPU and memory usage per container
- Network traffic for containers

### Screenshot 5: Detailed Chart View (`chart-detail.png`)
**How to get it:**
- Click on any chart to open detailed view
- Choose a chart with interesting data (CPU or Memory recommended)
- **What to capture:** Expanded chart with timeline, zoom controls, detailed metrics

## 🖼️ Screenshot Instructions

### Windows (Recommended method):
1. Press `Win + Shift + S` to open Snipping Tool
2. Select rectangular snip
3. Drag to select the area you want to capture
4. The screenshot will be copied to clipboard
5. Open Paint or any image editor
6. Press `Ctrl + V` to paste
7. Save as PNG file in the `screenshots` folder

### Alternative - Full Screen:
1. Press `Print Screen` key
2. Open Paint
3. Paste and crop as needed
4. Save as PNG file

## 📁 File Naming Convention
Save screenshots with these exact names in the `screenshots` folder:
- `dashboard-overview.png`
- `cpu-metrics.png`
- `memory-metrics.png`
- `docker-containers.png`
- `chart-detail.png`

## 🎯 Pro Tips

1. **Wait for data**: Let the dashboard run for 2-3 minutes before taking screenshots
2. **Zoom level**: Use 100% browser zoom for best quality
3. **Full window**: Capture the full browser window showing the dashboard
4. **Timestamp**: Screenshots should show recent timestamp data
5. **Quality**: Use PNG format for crisp, clear images

## 🔍 What to Look For

### CPU Section:
- Look for real-time CPU usage graphs
- Multiple cores should be visible
- Different colors for system/user/nice processes

### Memory Section:
- RAM usage bar
- Memory breakdown (used, cached, free)
- Swap usage (should be minimal)

### Containers Section:
- Netdata container should be listed
- Resource usage for the container
- Network activity

### Interactive Features:
- Hover effects on charts
- Clickable legends
- Time range selectors
- Zoom functionality

## ⚠️ Troubleshooting

**Dashboard won't load?**
- Wait 30 seconds after starting container
- Try http://127.0.0.1:19999 instead
- Check Windows Firewall
- Verify container: `docker ps`

**No data showing?**
- Refresh the page
- Wait 1-2 minutes for metrics to populate
- Check container logs: `docker logs netdata`

**Container section empty?**
- Docker metrics may take longer to appear
- Restart container: `docker restart netdata`

## ✅ Verification Checklist

Before proceeding to GitHub:
- [ ] All 5 screenshots taken
- [ ] Screenshots saved in correct folder with correct names
- [ ] Dashboard accessible at localhost:19999
- [ ] All screenshots show live data (not empty charts)
- [ ] Images are clear and readable
- [ ] Screenshots show timestamps indicating recent data

---

**Next Step**: Once you have all screenshots, proceed to Phase 4: GitHub setup and upload.
