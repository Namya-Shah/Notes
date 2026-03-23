**PROBLEM STATEMENT**
Ambulances lose critical time due to traffic congestion. Traffic police are often informed too late or manually, leading to delays that can impact patient survival.

**PRODUCT DEFINITION**
A system that detects ambulances using traffic cameras, checks congestion ahead, and alerts nearby traffic police in real time.

**PRODUCT OVERVIEW**
An AI-powered system that:
- Detects ambulances using traffic/CCTV cameras
- Detects traffic congestion ahead
- Automatically alerts nearby traffic police in real time

**WHY THIS PRODUCT MATTERS**
- Saves critical minutes during emergencies
- Reduces dependency on manual communication
- Works even without GPS from ambulances
- High social impact (healthcare + public safety)

**SYSTEM ARCHITECTURE**
Traffic Camera / Video Feed → Ambulance Detection (AI) → Congestion Analysis → Decision Engine → Alert Service → Police Dashboard + SMS

**CORE MODULES**
1. Ambulance Detection (AI)
	- Model: YOLOv8
	- Detects: Ambulance, emergency van
	- Tuned for high recall
2. Traffic Congestion Detection
	- Rule-based computer vision (OpenCV)
	- Signals used:
		- Vehicle density
		- Edge density / motion
	- Output: LOW/MEDIUM/HIGH congestion
3. Alert Engine (Core Logic)
	- Alert is triggered when:
		- Ambulance is detected
		- Congestion ahead is HIGH
		- No recent alert (cooldown applied)
	- Includes:
		- Confidence thresholds
		- Cooldown to prevent alert spam
		- Manual acknowledgement
4. Notification System
	- Primary: SMS to traffic police
	- Secondary: Web Dashboard

**FALSE NEGATIVES VS FALSE POSITIVES**
Definitions
- False Negative: Ambulance present but not detected
- False Positive: Alert triggered when no ambulance is present

Why False Negatives are Worse
- Missed ambulance = no alert
- Traffic not cleared
- Critical time lost
- Potential loss of life

**TECHNOLOGY STACK**
🧠 AI / ML
- YOLOv8 (Ultralytics) → ambulance detection
- OpenCV → vehicle count + speed
- Tuning for high recall

🖥️ Backend
- FastAPI (API + alert logic)
- PostgreSQL (events, logs)
- Redis (alert throttling)

🌐 Frontend
- React (or plain HTML + JS if needed)
- Leaflet / Mapbox for maps
- Police Dashboard Needs
	- Alert list
	- Camera snapshot
	- “Acknowledge” button

📲 Notifications
- SMS API
- Browser push

🧩 Deployment
- Edge device (Jetson Nano/Xavier)
