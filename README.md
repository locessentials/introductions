# LocEssentials Introductions

A bilingual (English/Spanish) web application for LocEssentials course participants to share their profiles and play a "Guess Who" matching game with alter egos.

## Features

- **Bilingual Support**: Full English and Spanish interface
- **Profile Directory**: Filterable directory of student profiles with real-life and alter ego personas
- **Guess Who Game**: Interactive matching game to connect students with their alter egos
- **Answer Key**: Complete reference showing all matches
- **Submission Form**: Bilingual form for students to submit their profiles
- **Privacy Controls**: Students can opt-in/out of public display after course completion
- **Course Badges**: Visual indicators for different course programs
- **Team Assignments**: Optional team filtering for group activities

## Project Structure

```
introductions/
├── index.html              # Main filterable directory page
├── game.html               # Guess Who interactive game
├── answer-key.html         # Shows all profile matches
├── submit.html             # Bilingual submission form
├── assets/
│   ├── css/
│   │   └── styles.css      # Main stylesheet with LocEssentials branding
│   ├── js/
│   │   ├── main.js         # Core functionality and filtering
│   │   └── form-translations.js  # Form translation strings
│   ├── images/             # Logo, photos, badges, favicon
│   └── audio/              # Name pronunciation files
├── _data/
│   └── students.json       # Student profile data
└── profiles/               # Individual profile pages (auto-generated)
```

## Setup

### Prerequisites
- GitHub Pages enabled on your repository
- Custom domain configured (optional): `introductions.locessentials.com`

### Installation

1. **Clone or create repository**
   ```bash
   git clone https://github.com/locessentials/introductions.git
   cd introductions
   ```

2. **Add required assets**
   - Add `LocCapTransparentTilted.png` to `/assets/images/`
   - Add `favicon.png` to `/assets/images/`
   - Add course badge images:
     - `badge-google-classroom.png`
     - `badge-uic.png`
     - `badge-uwm.png`
     - `badge-open-source.png`

3. **Configure GitHub Pages**
   - Go to repository Settings > Pages
   - Set source to main branch, root directory
   - Add custom domain if desired

4. **Deploy**
   - Push changes to main branch
   - Site will be live at your GitHub Pages URL

## Data Structure

Student profiles are stored in `_data/students.json`. Each entry contains:

```json
{
  "id": "unique-id",
  "submission_date": "2025-01-13",
  "public_display_consent": true,
  "language": "en",
  "full_name": "Jane Doe",
  "preferred_name": "Jane",
  "pronunciation_file": "/assets/audio/jane-doe.mp3",
  "photo": "/assets/images/jane-doe.jpg",
  "photo_alt": "Jane smiling at camera",
  "pronouns": "she/her",
  "languages_spoken": ["English", "Spanish"],
  "social_media": {
    "linkedin": "https://linkedin.com/in/janedoe"
  },
  "role": "Translator",
  "organization": "Translation Co",
  "about": "Passionate about language...",
  "previous_experience": "5 years in technical translation",
  "course": "Loc101: Introduction to Localization",
  "course_badge": "google-classroom",
  "section": "2025-1",
  "enrollment_reason": "To expand my skills...",
  "learning_goals": "Master CAT tools",
  "team": "Team Alpha",
  "alter_ego": {
    "name": "The Polyglot",
    "photo": "/assets/images/jane-doe-alter-ego.jpg",
    "photo_alt": "Superhero character",
    "photo_credits": "Created using MidJourney",
    "job_title": "Global Communication Champion",
    "organization": "Language League",
    "about": "Fighting miscommunication...",
    "subject_fields": "Technology, Healthcare",
    "hobbies": "Reading, Travel"
  },
  "anything_else": ""
}
```

## Adding New Students

### Manual Method
1. Edit `_data/students.json`
2. Add student photos to `/assets/images/`
3. Add pronunciation files (if any) to `/assets/audio/`
4. Commit and push changes

### Future: Automated Submission
- Form submissions will create pull requests
- Instructor reviews and merges
- Site automatically rebuilds

## Filtering System

Students can be filtered by:
- **Type**: All Introductions, Real Life, Alter Egos
- **Course**: Loc101 (EN/ES), Loc501, etc.
- **Section**: 2025-1, 2024-1, 2023-1
- **Team**: (if assigned)
- **Language**: English or Spanish

## Course Badges

Badge mapping in `course_badge` field:
- `google-classroom`: Google Classroom courses (Globe icon)
- `uic`: Universidad Intercontinental courses (Eagle icon)
- `uwm`: UW-Milwaukee courses (Panther icon)
- `open-source`: Open source courses (Mangrove icon)

## Branding

### Colors
- Pink: `#ef91c6`
- Light Blue: `#50A5E6`
- Medium Blue: `#2b7bb9`
- Dark Blue: `#1c6399`
- Background: `#F5F7F9` (Alabaster)

### Typography
- Font: Inter (Google Fonts)
- Premium feel through generous spacing
- Minimal headers and clean layout

## Privacy & Consent

- Students control public visibility via `public_display_consent` toggle
- During course: All students visible to cohort
- After course: Only consenting students visible publicly
- Privacy setting can be updated by editing JSON

## Game Mechanics

The "Guess Who" game:
1. Displays shuffled real-life and alter ego cards
2. Students select a real-life card, then an alter ego card
3. Correct matches turn green and lock
4. Incorrect matches shake and reset
5. Victory message appears when all matched
6. Can filter by course/section for targeted practice

## Language Support

Currently supports:
- English (default)
- Spanish (Español)

Toggle switches between languages on:
- Main directory
- Submission form
- All interface text

## Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile responsive design
- Audio player for pronunciation files
- File upload for photos and audio

## Future Enhancements

- [ ] MongoDB integration for profile editing
- [ ] User authentication for students
- [ ] Automated pull request creation from form submissions
- [ ] Individual profile pages with full details
- [ ] Export/import functionality
- [ ] Admin dashboard for instructors
- [ ] Email notifications
- [ ] Analytics tracking

## Contributing

This is a private project for LocEssentials courses. If you're an instructor or want to adapt this for your program, feel free to fork and customize.

## License

© 2025 LocEssentials. All rights reserved.

## Contact

For questions or issues, contact Alaina Brandt at LocEssentials.

## Acknowledgments

- Course badge designs inspired by institutional partnerships
- Built with vanilla JavaScript for simplicity and performance
- Hosted on GitHub Pages for ease of deployment
