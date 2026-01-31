# Trivia Browser Web App

## Overview
Single-page web app for playing trivia quizzes. Vanilla JavaScript with no build step - just open `index.html` in a browser or serve via HTTP.

## Quick Start
```bash
# Serve locally (needed for API calls due to CORS)
python3 -m http.server 3000

# Open in browser
open http://localhost:3000
```

## Features
- **Quiz Mode** - Random questions with timer option
- **Browse Mode** - Explore questions by category
- **Statistics** - Track accuracy, streaks, category performance
- **Challenge Friends** - Share quiz via email
- **Offline Support** - LocalStorage persistence

## Architecture

### Single File App
Everything in `index.html`:
- HTML structure with tab navigation
- CSS styles (embedded)
- JavaScript app logic (embedded)

### State Management
Uses LocalStorage for persistence:
```javascript
localStorage.getItem('triviaStats')     // Overall statistics
localStorage.getItem('triviaHistory')   // Quiz history
localStorage.getItem('triviaSettings')  // User preferences
```

### API Integration
Connects to trivia-ill backend:
```javascript
const API_BASE = 'http://localhost:8080/api/v1';

// Get random questions
GET ${API_BASE}/questions/random?count=10&category=...

// Get categories
GET ${API_BASE}/categories

// Create challenge
POST ${API_BASE}/challenges
```

## UI Sections

### Tabs
1. **Quiz** - Start new quiz, select category/difficulty/count
2. **Browse** - View questions by category
3. **Stats** - Accuracy ring, streaks, category breakdown
4. **Settings** - Timer toggle, sound, clear history

### Quiz Flow
1. User selects options and starts quiz
2. Questions displayed one at a time
3. Timer countdown (optional)
4. Results shown with score
5. Option to challenge friend

## Key Functions
```javascript
startQuiz()           - Begin new quiz session
submitAnswer(index)   - Check answer, update stats
showResults()         - Display final score
challengeFriend()     - Send quiz via email
updateStats()         - Recalculate statistics
renderHistory()       - Show past quizzes
```

## Styling
- CSS variables for theming
- Mobile-responsive design
- Dark mode support via `prefers-color-scheme`

## Configuration
Edit these constants in the script:
```javascript
const API_BASE = 'http://localhost:8080/api/v1';
const DEFAULT_QUESTION_COUNT = 10;
const TIMER_SECONDS = 30;
```

## Development Notes
- No build tools required
- No npm dependencies
- Works offline after initial load (cached questions)
- CORS: Must be served via HTTP, not file://

## Related Projects
- `trivia-ill` - Backend API server
- `trivia-browser-ios` - iOS native app
- `trivia-gen-daemon` - Question acquisition
