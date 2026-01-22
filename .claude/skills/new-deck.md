# new-deck

Add a new student to the Student Ideation Portal with their project ideas.

## Usage

```
/new-deck <student_name> <major> <project1>, <project2>, ...
```

Example:
```
/new-deck Ethan "Data Science" ScriptSense, PianoEmotion AI, TubeInsight
```

## Instructions

When this skill is invoked, perform the following steps:

### 1. Parse Input
- Extract the student name (first argument)
- Extract the major (second argument, may be quoted if contains spaces)
- Extract the list of project names (comma-separated after the major)

### 2. Fetch Project Details
- Use WebFetch to retrieve project information from https://design-hub-pro.github.io/
- For each project name provided, find:
  - The exact project URL (href) - these follow patterns like `project_name/index.html`
  - The project description
  - Relevant tags/categories (e.g., AI/ML, Data Science, NLP, etc.)

### 3. Create Student Details Page
- Create directory: `student/<lowercase_student_name>/`
- Create `index.html` following the same template as existing student pages (e.g., `student/rosie/index.html`)
- Include:
  - Hero section with student name and major
  - Section header with "Project Ideas" and a relevant subtitle
  - Project cards for each project with:
    - Project number
    - Project name
    - Project description
    - Relevant tags
    - Link to the project page on design-hub-pro.github.io (use the exact URL found in step 2)
    - Arrow icon

### 4. Update Main Index Page
- Edit `index.html` to add a new table row in the `<tbody>` section
- Include:
  - Student name
  - Major badge(s)
  - Link to view ideas (e.g., "View 3 Ideas" with correct count)

### 5. Push to GitHub
- Stage the changes: `git add index.html student/<student_name>/`
- Commit with message: "Add <student_name>'s project page with <major> projects"
- Push to origin: `git push`

### 6. Confirm Completion
- Report the commit hash
- Confirm the files that were created/modified
- Optionally open the student page in the browser

## Template Reference

Use `student/rosie/index.html` or `student/ethan/index.html` as the template for the student details page. Key elements:
- Same CSS styling (embedded in `<style>` tag)
- Hero gradient background
- Project cards with hover effects
- Responsive design for mobile

## Project URL Pattern

Project URLs on design-hub-pro.github.io typically follow this pattern:
```
https://design-hub-pro.github.io/<project_folder>/index.html
```

Always verify the exact URL by fetching from the main page to ensure accuracy.
