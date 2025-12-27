# 📊 TaskGlitch - Sales Task Management App

A modern, feature-rich task management application designed for sales teams to track, manage, and prioritize tasks based on ROI (Return on Investment).

![React](https://img.shields.io/badge/React-18.3.1-blue)
![TypeScript](https://img.shields.io/badge/TypeScript-5.6.2-blue)
![Material-UI](https://img.shields.io/badge/Material--UI-6.1.7-blue)
![Vite](https://img.shields.io/badge/Vite-5.4.8-purple)

## 🚀 Live Demo

[Deploy on Vercel](https://vercel.com) - Ready for deployment!

## ✨ Features

### Core Functionality
- ✅ **Task CRUD Operations** - Add, edit, delete, and view tasks
- ✅ **Smart Search & Filters** - Filter by status, priority, and search by title
- ✅ **ROI Calculation** - Automatic ROI calculation (Revenue ÷ Time Taken)
- ✅ **Intelligent Sorting** - Sort by ROI, priority weight, and alphabetically
- ✅ **Undo Delete** - Recover accidentally deleted tasks with snackbar notification

### Analytics & Insights
- 📊 **Metrics Dashboard** - Total revenue, time efficiency, average ROI, performance grade
- 📈 **Charts & Visualizations** - Revenue by priority, status distribution, ROI buckets
- 📉 **Advanced Analytics** - Funnel analysis, throughput trends, velocity tracking, forecasting
- 📥 **CSV Export** - Export filtered tasks to CSV format

### User Experience
- 🎨 **Material Design** - Clean, modern UI with Material-UI components
- 📱 **Responsive Layout** - Works seamlessly on desktop, tablet, and mobile
- 🌙 **Activity Log** - Track all task operations (add, update, delete, undo)
- ⚡ **Fast Performance** - Built with Vite for lightning-fast development and builds

## 🛠️ Tech Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| **React** | 18.3.1 | UI Framework |
| **TypeScript** | 5.6.2 | Type Safety |
| **Vite** | 5.4.8 | Build Tool |
| **Material-UI** | 6.1.7 | Component Library |
| **MUI X Charts** | 7.20.0 | Data Visualization |
| **dayjs** | 1.11.13 | Date Utilities |
| **Emotion** | 11.13.3 | CSS-in-JS |

## 🐛 Bug Fixes Implemented

This project demonstrates professional debugging and problem-solving skills. All major bugs have been identified and fixed:

### ✅ Bug #1: Double Fetch Issue
- **Problem**: Task data was fetched twice on page load
- **Fix**: Removed duplicate useEffect hook
- **Impact**: Improved performance and eliminated duplicate data

### ✅ Bug #2: Undo Snackbar Bug
- **Problem**: Deleted task state not cleared when snackbar closed
- **Fix**: Implemented `clearLastDeleted()` function called on snackbar close
- **Impact**: Prevents phantom data recovery after snackbar expires

### ✅ Bug #3: Unstable Sorting
- **Problem**: Tasks with same ROI/priority flickered due to random sorting
- **Fix**: Replaced `Math.random()` with alphabetical title sort
- **Impact**: Stable, consistent task ordering

### ✅ Bug #4: Double Dialog Opening
- **Problem**: Edit/Delete buttons triggered both action and view dialogs
- **Fix**: Added `event.stopPropagation()` to prevent event bubbling
- **Impact**: Clean UX with single dialog per action

### ✅ Bug #5: ROI Calculation Errors
- **Problem**: Division by zero, NaN, and Infinity values in ROI
- **Fix**: Input validation with `Number.isFinite()` checks
- **Impact**: No invalid ROI values, robust error handling

### ✅ Bug #6: XSS Vulnerability (Security)
- **Problem**: Task notes rendered with `dangerouslySetInnerHTML`
- **Fix**: Changed to plain text rendering
- **Impact**: Eliminated XSS attack vector

### ✅ Bug #7: ROI Bucketing Issues
- **Problem**: Chart incorrectly categorized null/NaN ROI values
- **Fix**: Proper validation before bucketing ROI data
- **Impact**: Accurate data visualization

### ✅ Bug #8: Malformed Data Injection
- **Problem**: Random invalid data injected on load
- **Fix**: Removed malformed data injection code
- **Impact**: Data integrity maintained

## 📦 Installation

### Prerequisites
- Node.js 18+ 
- npm or yarn

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/Kushal-Raj-G-S/kushalrajgs-task-glitch.git
   cd kushalrajgs-task-glitch
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Open browser**
   ```
   http://localhost:5173
   ```

## 🏗️ Build for Production

```bash
npm run build
```

Output will be in the `dist/` folder, ready for deployment.

## 🚀 Deployment

### Deploy to Vercel (Recommended)

1. **Install Vercel CLI** (optional)
   ```bash
   npm i -g vercel
   ```

2. **Deploy via Vercel Dashboard**
   - Push your code to GitHub
   - Import project in [Vercel Dashboard](https://vercel.com/new)
   - Vercel auto-detects Vite configuration
   - Deploy! 🎉

3. **Or deploy via CLI**
   ```bash
   vercel
   ```

### Build Settings for Vercel
- **Framework Preset**: Vite
- **Build Command**: `npm run build`
- **Output Directory**: `dist`
- **Install Command**: `npm install`

## 📜 Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server with hot reload |
| `npm run build` | Build for production (TypeScript check + Vite build) |
| `npm run preview` | Preview production build locally |

## 📂 Project Structure

```
kushalrajgs-task-glitch/
├── public/
│   └── tasks.json          # Initial task data
├── src/
│   ├── components/         # React components
│   │   ├── ActivityLog.tsx
│   │   ├── AnalyticsDashboard.tsx
│   │   ├── ChartsDashboard.tsx
│   │   ├── MetricsBar.tsx
│   │   ├── TaskDetailsDialog.tsx
│   │   ├── TaskForm.tsx
│   │   ├── TaskTable.tsx
│   │   └── UndoSnackbar.tsx
│   ├── context/            # React Context providers
│   │   ├── TasksContext.tsx
│   │   └── UserContext.tsx
│   ├── hooks/              # Custom React hooks
│   │   └── useTasks.ts
│   ├── utils/              # Utility functions
│   │   ├── csv.ts
│   │   ├── logic.ts
│   │   └── seed.ts
│   ├── App.tsx             # Main app component
│   ├── main.tsx            # Entry point
│   ├── theme.ts            # MUI theme
│   └── types.ts            # TypeScript types
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

## 🎯 Key Concepts

### Task Model
```typescript
interface Task {
  id: string;
  title: string;
  revenue: number;
  timeTaken: number;
  priority: 'High' | 'Medium' | 'Low';
  status: 'Todo' | 'In Progress' | 'Done';
  notes?: string;
  createdAt: string;
  completedAt?: string;
}
```

### ROI Calculation
```typescript
ROI = Revenue ÷ Time Taken
- Returns null for invalid inputs (timeTaken = 0, NaN, Infinity)
- Displayed as "N/A" in UI when null
```

### Sorting Logic
1. **Primary**: ROI (highest to lowest)
2. **Secondary**: Priority Weight (High=3, Medium=2, Low=1)
3. **Tertiary**: Alphabetical by title (A-Z)

### Performance Grade
- **Excellent**: Average ROI > 500
- **Good**: Average ROI ≥ 200
- **Needs Improvement**: Average ROI < 200

## 🤝 Contributing

This is a portfolio/assignment project. Contributions, issues, and feature requests are welcome!

## 👨‍💻 Author

**Kushal Raj G S**
- GitHub: [@Kushal-Raj-G-S](https://github.com/Kushal-Raj-G-S)
- Email: kushalrajgs@gmail.com

## 📄 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

- Built as part of an SDE assignment demonstrating debugging and problem-solving skills
- All intentional bugs successfully identified and resolved
- Production-ready code with security best practices

---

**⭐ Star this repo if you found it helpful!**
