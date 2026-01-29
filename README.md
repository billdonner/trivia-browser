# Trivia Browser

A simple static webapp for browsing trivia questions from the Trivia Database Server.

## Features

- Browse random questions from the database
- Filter by category and difficulty
- Interactive quiz mode - click answers to reveal correct/incorrect
- Configurable server URL

## Usage

### Option 1: Open directly
```bash
open index.html
```

### Option 2: Serve locally (for CORS)
```bash
python3 -m http.server 3000
# Then open http://localhost:3000
```

### Option 3: Use Live Server (VS Code)
Right-click `index.html` and select "Open with Live Server"

## Requirements

- Trivia Database Server running (default: http://localhost:8080)
- Server must have CORS enabled for your origin

## Configuration

Enter the server URL in the input field at the top of the page. Default is `http://localhost:8080`.
