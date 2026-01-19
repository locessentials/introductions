# Setup Guide for Instructors

This guide walks you through setting up the LocEssentials Introductions site for your course.

## Initial Setup

### 1. Create GitHub Repository

```bash
# Create new repository on GitHub
# Name it: introductions or locessentials-introductions

# Clone to your computer
git clone https://github.com/YOUR_USERNAME/introductions.git
cd introductions

# Copy all project files to this directory
```

### 2. Add Required Assets

You need to add these image files to `/assets/images/`:

1. **LocCapTransparentTilted.png** - Main logo (tilted cap)
2. **LocCapLogoTransparent.png** - Alternative logo
3. **favicon.png** - Browser tab icon
4. **Course badges**:
   - badge-google-classroom.png
   - badge-uic.png
   - badge-uwm.png
   - badge-open-source.png

### 3. Configure GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** > **Pages**
3. Under "Source", select:
   - Branch: **main**
   - Folder: **/ (root)**
4. Click **Save**
5. Your site will be available at: `https://YOUR_USERNAME.github.io/introductions/`

### 4. Add Custom Domain (Optional)

If you want to use `introductions.locessentials.com`:

1. In your DNS settings, add a CNAME record:
   - Name: `introductions`
   - Value: `YOUR_USERNAME.github.io`
2. In GitHub Pages settings, add custom domain: `introductions.locessentials.com`
3. Enable "Enforce HTTPS" (wait a few minutes for certificate)

## Adding Students

### Method 1: Manual Entry

1. Open `_data/students.json`
2. Copy the sample entry structure
3. Fill in student information
4. Add student photos to `/assets/images/` with naming convention:
   - Real life: `firstname-lastname.jpg`
   - Alter ego: `firstname-lastname-alter-ego.jpg`
5. Add pronunciation files to `/assets/audio/`:
   - Format: `firstname-lastname.mp3`
6. Commit and push changes

### Method 2: Form Submission (Manual Processing)

Students can submit via the form at `/submit.html`, but you'll need to manually process submissions:

1. Student fills out form and emails you the data
2. You receive photos and audio files
3. You manually add entry to `students.json`
4. Upload assets and commit changes

### Method 3: Future Automated System

In the future, we can add:
- GitHub API integration for automatic pull requests
- MongoDB for student login and editing
- Email notifications when forms are submitted

## Student Data Structure

Each student entry requires:

```json
{
  "id": "unique-id-123",              // Generate unique ID
  "submission_date": "2025-01-13",    // Date of submission
  "public_display_consent": true,     // Privacy setting
  "language": "en",                   // "en" or "es"
  
  // Real Life Info
  "full_name": "Jane Doe",
  "preferred_name": "Jane",
  "pronunciation_file": "/assets/audio/jane-doe.mp3",  // Optional
  "photo": "/assets/images/jane-doe.jpg",
  "photo_alt": "Jane smiling at camera",
  "pronouns": "she/her",
  "languages_spoken": ["English", "Spanish"],
  "social_media": {
    "linkedin": "https://linkedin.com/in/janedoe"      // Optional
  },
  "role": "Translator",
  "organization": "Translation Co",                     // Optional
  "about": "Passionate about language and culture...",
  "previous_experience": "5 years in technical translation",
  
  // Course Info
  "course": "Loc101: Introduction to Localization",
  "course_badge": "google-classroom",  // google-classroom, uic, uwm, or open-source
  "section": "2025-1",
  "enrollment_reason": "To expand my skills...",
  "learning_goals": "Master CAT tools and terminology",
  "team": "",                          // Leave blank initially
  
  // Alter Ego Info
  "alter_ego": {
    "name": "The Polyglot",
    "photo": "/assets/images/jane-doe-alter-ego.jpg",
    "photo_alt": "Superhero character with cape",
    "photo_credits": "Created using MidJourney",
    "job_title": "Global Communication Champion",
    "organization": "Language League",
    "about": "Fighting miscommunication across galaxies...",
    "subject_fields": "Technology, Healthcare, Legal",
    "hobbies": "Reading sci-fi, international travel, learning new languages"
  },
  
  "anything_else": ""                  // Optional
}
```

## Assigning Teams

To assign students to teams:

1. Open `_data/students.json`
2. Add team name to student entries:
   ```json
   "team": "Team Alpha"
   ```
3. Team filter will automatically appear on the site

## Managing Privacy

Students control whether their profile appears publicly after the course:

- `"public_display_consent": true` - Profile visible to everyone
- `"public_display_consent": false` - Profile only visible during course

During the course, all students see each other regardless of this setting.

## Course Badge Mapping

Set `course_badge` to match your course type:

| Badge Type | Use For | Icon |
|------------|---------|------|
| `google-classroom` | Google Classroom courses | Globe |
| `uic` | Universidad Intercontinental | Eagle |
| `uwm` | UW-Milwaukee SCE | Panther |
| `open-source` | Open source courses | Mangrove |

## Customization

### Colors

Edit `/assets/css/styles.css` to change colors:

```css
:root {
  --pink: #ef91c6;
  --light-blue: #50A5E6;
  --medium-blue: #2b7bb9;
  --dark-blue: #1c6399;
}
```

### Languages

To add more languages:

1. Edit `/assets/js/form-translations.js`
2. Add new language object to `translations`
3. Update language toggle buttons

### Courses

To add new courses:

1. Edit course dropdown in `/submit.html`
2. Add new option:
   ```html
   <option value="Loc201: Advanced Localization">Loc201: Advanced Localization</option>
   ```

## Troubleshooting

### Site not updating after push
- Check GitHub Actions tab for deployment status
- Wait 2-3 minutes for deployment to complete
- Hard refresh browser (Ctrl+F5 or Cmd+Shift+R)

### Images not displaying
- Verify file paths are correct in JSON
- Check that files are committed to repository
- Ensure file names match exactly (case-sensitive)

### Filters not working
- Check browser console for JavaScript errors
- Verify students.json is valid JSON (use JSONLint.com)
- Clear browser cache

### Custom domain not working
- Wait 24-48 hours for DNS propagation
- Verify CNAME record in DNS settings
- Check GitHub Pages settings

## Support

For questions or issues:
- Email: alaina@locessentials.com
- Review README.md for technical details
- Check GitHub Issues for known problems

## Backup

Regularly backup your `students.json` file:

```bash
# Create backup
cp _data/students.json _data/students-backup-$(date +%Y%m%d).json

# Commit backup
git add _data/students-backup-*.json
git commit -m "Backup student data"
git push
```

## Best Practices

1. **Test locally** before pushing changes
2. **Backup data** before major edits
3. **Verify images** are properly sized (max 1MB recommended)
4. **Use consistent naming** for files
5. **Check privacy settings** before making profiles public
6. **Review submissions** for appropriate content
7. **Update course badges** to match your program
8. **Keep README updated** with any custom changes
