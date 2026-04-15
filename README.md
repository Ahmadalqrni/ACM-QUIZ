This is an impressive **real-time multiplayer quiz game** built with Firebase and styled for ACM Chapter events. Here's a comprehensive README:

---

Link [https://ahmadalqrni.github.io/ACM-QUIZ/]

# 🎓 ACM Chapter - Knowledge Challenge

A **real-time multiplayer quiz game** where a host creates a room, students join, and everyone competes against each other (and a GPT-Bot!) across 5 questions in their chosen major.

## ✨ Features

### 🎮 **Two Roles**

- **Host** – Password-protected room creation, real-time player monitoring, controls game flow
- **Student** – Join via room code or QR, answer timed questions, see live leaderboard

### 📚 **4 Major Tracks**

- Computer Engineering (CS)
- Electrical Engineering (EE)
- Architecture (ARCH)
- "No Major" – mixed general knowledge

### 🤖 **GPT-Bot Opponent**

- Always present in every room
- Answers randomly (70% chance correct) with variable delay (8–20s)
- Scoring based on speed (faster = more points)

### ⏱️ **Dynamic Scoring System**

| Time remaining | Points earned |
| -------------- | ------------- |
| 20–30 seconds  | 1000 points   |
| 10–20 seconds  | 700 points    |
| 0–10 seconds   | 400 points    |
| Time's up      | 0 points      |

### 🏆 **Post-Game Features**

- Podium display (🥇🥈🥉)
- Personalized badges (Perfect answers, Beat AI, Champion)
- Confetti animation for winners
- Full leaderboard with player scores

## 🛠️ **Technical Stack**

- **Frontend**: Vanilla HTML/CSS/JS
- **Backend**: Firebase Realtime Database
- **QR Codes**: QR Server API (auto-generated for room join)
- **Styling**: Glassmorphism design, responsive RTL layout

## 🚀 **Setup Instructions**

### 1. Firebase Configuration

Create a Firebase project and replace the `firebaseConfig` object in the script:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "your-project.firebaseapp.com",
  databaseURL: "https://your-project-default-rtdb.firebaseio.com",
  projectId: "your-project",
  storageBucket: "your-project.firebasestorage.app",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID",
};
```

### 2. Database Rules

Set Realtime Database rules to **test mode** (for development):

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

### 3. Host Password

Change the default password (optional):

```javascript
const HOST_PASSWORD = "ACM2025"; // Change this
```

### 4. Question Images

For the **Computer Engineering** category, place images in `/cs/` folder:

- `ram.jpg`, `CPU.jpg`, `motherboard.jpg`, `gpu.jpg`, `ssd.jpg`

Other categories use Wikimedia URLs (already configured).

## 🎮 **How to Play**

### **Host Flow:**

1. Select "أنا مشرف" (I'm Host)
2. Enter password (default: `ACM2025`)
3. Choose major track
4. Share room code or QR code with students
5. Wait for at least 2 students → click "ابدأ اللعبة"
6. Each question: monitor answers, click "عرض النتيجة" then "السؤال التالي"
7. Final results shown after 5 questions

### **Student Flow:**

1. Select "أنا طالب" (I'm Student)
2. Enter room code (or scan QR)
3. Enter name and select your major
4. Wait in lobby for host to start
5. Answer 5 questions with 30-second timer each
6. View per-question results and final leaderboard

## 📁 **File Structure**

```
/
├── index.html          # Complete application (all-in-one)
├── acm-logo.png        # Optional logo (fallback text if missing)
├── cs/                 # CS category images
│   ├── ram.jpg
│   ├── CPU.jpg
│   ├── motherboard.jpg
│   ├── gpu.jpg
│   └── ssd.jpg
```

## 🔒 **Security Notes**

- No authentication – room codes are simple (e.g., `TECH-4821`)
- All players can read/write any room (test mode)
- For production, implement Firebase Auth and stricter database rules
- Host password is hardcoded client-side (not secure for production)

## 🎨 **Customization**

### **Add New Questions**

Edit the `QUESTIONS` object:

```javascript
QUESTIONS.yourMajor = [
  {
    image: "image-url.jpg",
    question: "Your question text?",
    hint: "Clue for students",
    accepted: ["answer1", "answer2", "answer3"],
  },
];
```

### **Change Timer Duration**

Find `startTimer(30, ...)` calls – modify the `30` value (seconds).

### **Modify Scoring**

Edit `calcScore(elapsedSec)` function.

## 🐛 **Troubleshooting**

| Issue                | Solution                                                   |
| -------------------- | ---------------------------------------------------------- |
| Firebase not working | Check console for errors, verify config and database rules |
| Images not loading   | Ensure paths are correct or use absolute URLs              |
| QR code not showing  | API endpoint is public – check network tab                 |
| Students can't join  | Verify room code matches exactly (case-sensitive)          |
| Timer not syncing    | Firebase ServerValue.TIMESTAMP ensures sync                |

## 📱 **Browser Support**

- Chrome/Edge/Firefox (latest)
- Safari (iOS 13+)
- Mobile responsive design

## 🎯 **Future Improvements**

- [ ] User authentication (Google Sign-In)
- [ ] Persistent leaderboards across games
- [ ] More question categories
- [ ] Power-ups or lifelines
- [ ] Audio/visual effects
- [ ] Export results to CSV
- [ ] Spectator mode

## 📄 **License**

Educational use – free to modify for ACM Chapter events.

---

## 🚀 **Quick Start**

1. Clone/download the HTML file
2. Set up Firebase (copy config)
3. Place CS images in `/cs/` folder
4. Open `index.html` in browser
5. Host creates room → Students join → **Play!**

---

**Made with ❤️ for ACM Student Chapters** | Real-time Quiz Platform
