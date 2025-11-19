# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a quiz application focused on sustainable development and environmental concepts (DDRS - Développement Durable, Responsabilité Sociétale). The project includes:
- Quiz data in JSON format covering topics like low-tech, renewable energy, eco-design, sustainability, and planetary boundaries
- A browser extension (Manifest V3) to help search and display quiz questions/answers
- An HTML results file (mes_reponses.html) containing quiz responses from Moodle

## Project Structure

```
DDRS_DO2023/
├── quiz.json              # Primary quiz data with questions and answers
├── quiz2.json             # Secondary quiz data (similar structure)
├── Extension/             # Browser extension files
│   ├── manifest.json      # Manifest V3 configuration
│   ├── popup.html         # Extension popup interface
│   └── popup.js           # Extension logic (searches quiz data)
├── Extension.tar.gz/      # Archived version of extension
└── mes_reponses.html      # Large HTML file with Moodle quiz results
```

## Data Structure

### Quiz JSON Format

The quiz data files (`quiz.json`, `quiz2.json`) contain an array of question objects with the following structure:

```json
{
  "question": "Question text in French",
  "choix": [
    {
      "intitule": "Answer choice text",
      "est_correct": true/false
    }
  ]
}
```

- `question`: The quiz question text
- `choix`: Array of possible answers
- `intitule`: Text of the answer choice
- `est_correct`: Boolean indicating if this choice is correct (can have multiple correct answers)

### Extension Data

The extension embeds the quiz data directly in `popup.js` as a JavaScript array (same structure as JSON files but without quotes on keys).

## Browser Extension

### Architecture

The extension provides a search interface to quickly find correct answers from the quiz data:

1. **manifest.json**: Defines the extension as Manifest V3 with a popup action
2. **popup.html**: Simple form with text input and content display area
3. **popup.js**:
   - Embeds complete quiz data
   - Listens for keydown events on input field
   - Searches questions using case-insensitive substring matching
   - Displays matching questions with their correct answers

### Key Functions

- `getResponse(response)`: Searches the data array for questions containing the input string, returns array of objects with correct answers and their questions

### Usage

Users type keywords in the input field, and the extension instantly displays all questions containing that keyword along with their correct answers.

## Development Notes

### Working with Quiz Data

- Both `quiz.json` and `quiz2.json` have identical content (25+ questions)
- Questions cover French-language educational content about sustainability
- The `popup.js` data should be kept in sync with JSON files if quiz data is updated

### Important Considerations

When modifying the extension:
- The data in `popup.js` is hardcoded - any changes to quiz questions require updating both JSON files and the JS array
- The search is performed on every keydown event (no debouncing) - consider adding debouncing for performance
- Currently searches only the `question` field, not answer choices

### Common Tasks

**Update quiz data:**
1. Modify `quiz.json` and/or `quiz2.json`
2. Update the `data` array in `Extension/popup.js` to match
3. Ensure JSON syntax is valid (no trailing commas)

**Load the extension in browser:**
1. Navigate to chrome://extensions/ (or equivalent)
2. Enable "Developer mode"
3. Click "Load unpacked"
4. Select the `Extension/` directory

**Test extension functionality:**
- Type keywords like "low tech", "énergie", "durabilité" to search questions
- Verify correct answers are displayed
- Check that multiple correct answers for the same question are all shown
