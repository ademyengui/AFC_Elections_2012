# EduPulse AI — Technical Specification

## 🎯 Objective
Build an MVP of an AI-powered platform for tutoring centers that:
- Tracks student performance
- Predicts failure/dropout risk
- Generates actionable interventions
- Produces automated reports & marketing content

---

## 🏗️ System Architecture

### High-Level Components

1. **Frontend (Dashboard UI)**
2. **Backend API (FastAPI)**
3. **Data Layer (Database + Synthetic Data Generator)**
4. **AI Layer (LLM + Rule-based scoring)**

---

## 🧩 Component Breakdown

### 1. Frontend (React)

#### Pages:
- Dashboard
- Student Profile
- Insights Panel
- Reports / Marketing Generator

#### Key Features:
- Data visualization (charts for grades, attendance)
- Risk indicators (color-coded)
- AI insights display
- Action buttons (generate plan, generate post)

#### Suggested Stack:
- React + Vite
- Chart library (Recharts / Chart.js)
- TailwindCSS

---

### 2. Backend (FastAPI)

#### Structure:
```
/backend
  /app
    main.py
    routes/
      students.py
      analytics.py
      ai.py
    services/
      risk_engine.py
      insights_engine.py
      intervention_engine.py
    models/
      student.py
      performance.py
    db/
      database.py
```

---

## 📊 Data Model

### Student
```
{
  id: int,
  name: string,
  level: string,
  subjects: [string]
}
```

### Performance Record
```
{
  student_id: int,
  date: datetime,
  subject: string,
  grade: float,
  attendance: boolean
}
```

---

## 🧠 AI + Logic Layer

### 1. Risk Scoring Engine (Rule-Based MVP)

#### Inputs:
- Recent grades trend
- Attendance rate

#### Logic (example):
```
if avg_grade_last_3 < 10:
    risk += 0.4
if attendance_rate < 0.7:
    risk += 0.3
if grade_trend == "downward":
    risk += 0.3
```

#### Output:
```
{
  fail_risk: float (0-1),
  dropout_risk: float (0-1)
}
```

---

### 2. Insights Engine (LLM)

#### Prompt Template:
```
Given the following student data:
- Grades: {grades}
- Attendance: {attendance}

Generate:
1. Key insights
2. Detected problems
3. Behavioral patterns
```

---

### 3. Intervention Engine (LLM)

#### Prompt Template:
```
Student has the following issues:
{issues}

Generate:
- Study plan
- Teacher actions
- Timeline for improvement
```

---

### 4. Marketing Generator (LLM)

#### Prompt Template:
```
Given student improvement data:
{data}

Generate:
- Social media post
- Success story
- Key stats
```

---

## 🔌 API Endpoints

### Students
- GET /students
- GET /students/{id}

### Analytics
- GET /students/{id}/risk
- GET /students/{id}/insights

### AI
- POST /students/{id}/intervention
- POST /marketing/generate

---

## 🧪 Data Simulation

### Script:
- Generate ~20 students
- Random grade evolution (improving / declining / stable)
- Attendance patterns

Use Python script:
```
import random
```

---

## ⚙️ LLM Integration

### Use:
- OpenAI API or Claude API

### Wrapper Service:
```
def call_llm(prompt: str) -> str:
    # API call
    return response
```

---

## 🚀 MVP Priorities (IMPORTANT)

### Must Have:
- Student dashboard
- Risk scoring
- Insights generation

### Should Have:
- Intervention generation
- Marketing posts

### Nice to Have:
- Chatbot

---

## 🧱 Development Plan (24–48h)

### Day 1:
- Setup backend + DB
- Generate fake data
- Build risk engine

### Day 2:
- Integrate LLM
- Build frontend dashboard
- Connect API

---

## 🧑‍💻 Team Split (4 people)

1. Backend + DB
2. AI / LLM integration
3. Frontend UI
4. Data simulation + demo preparation

---

## 🏁 Success Criteria

- Risk prediction works
- Insights are meaningful
- Demo is smooth
- System feels intelligent

---

## ⚠️ Notes

- Keep logic simple but believable
- Focus on UX clarity
- Prioritize demo storytelling over perfection

