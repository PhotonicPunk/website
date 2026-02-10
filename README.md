# John Gerald Cormier - Personal Website

A personal website built with [Astro](https://astro.build), featuring a blog, professional experience, publications, and patents.

## Local Development

### Prerequisites

- [Node.js](https://nodejs.org/) (v18 or higher)
- npm (comes with Node.js)

### Getting Started

1. Install dependencies:
   ```bash
   npm install
   ```

2. Start the development server:
   ```bash
   npm run dev
   ```

3. Open your browser to `http://localhost:4321`

### Available Commands

| Command           | Action                                       |
| :---------------- | :------------------------------------------- |
| `npm install`     | Install dependencies                         |
| `npm run dev`     | Start local dev server at `localhost:4321`   |
| `npm run build`   | Build production site to `./dist/`           |
| `npm run preview` | Preview build locally before deploying       |

## Adding Blog Posts

Create new markdown files in `src/content/blog/` with the following frontmatter:

```markdown
---
title: "Your Post Title"
description: "A brief description of your post"
pubDate: 2026-01-28
tags: ["tag1", "tag2"]
---

Your content here...
```

## Deploying to GitHub Pages

### Step 1: Create a GitHub Repository

1. Go to [GitHub](https://github.com) and sign in (or create an account)

2. Click the **+** icon in the top-right corner and select **New repository**

3. Name your repository (e.g., `website` or `johncormier.github.io`)
   - If you name it `yourusername.github.io`, your site will be available at `https://yourusername.github.io`
   - If you use any other name (e.g., `website`), your site will be at `https://yourusername.github.io/website`

4. Keep the repository **Public** (required for free GitHub Pages)

5. Do NOT initialize with README, .gitignore, or license (we already have these)

6. Click **Create repository**

### Step 2: Update the Astro Configuration

Edit `astro.config.mjs` to match your GitHub username and repository name:

```javascript
export default defineConfig({
  site: 'https://YOUR_GITHUB_USERNAME.github.io',
  base: '/YOUR_REPO_NAME',  // Remove this line if repo is named yourusername.github.io
  output: 'static',
});
```

For example:
- If your username is `johncormier` and repo is `website`:
  ```javascript
  site: 'https://johncormier.github.io',
  base: '/website',
  ```
- If your repo is `johncormier.github.io`:
  ```javascript
  site: 'https://johncormier.github.io',
  // No base needed
  ```

### Step 3: Initialize Git and Push to GitHub

Open a terminal in the `website` directory and run:

```bash
# Initialize a new git repository
git init

# Add all files to git
git add .

# Create your first commit
git commit -m "Initial commit: Personal website with Astro"

# Rename the default branch to main
git branch -M main

# Add your GitHub repository as a remote
# Replace YOUR_USERNAME and YOUR_REPO with your actual values
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git

# Push your code to GitHub
git push -u origin main
```

### Step 4: Enable GitHub Pages

1. Go to your repository on GitHub

2. Click **Settings** (tab near the top)

3. In the left sidebar, click **Pages**

4. Under **Source**, select **GitHub Actions**

5. The deployment will start automatically when you push to the `main` branch

### Step 5: Verify Deployment

1. After pushing, go to the **Actions** tab in your repository

2. You should see a workflow running called "Deploy to GitHub Pages"

3. Once it completes (green checkmark), your site will be live at:
   - `https://YOUR_USERNAME.github.io/YOUR_REPO/`
   - Or `https://YOUR_USERNAME.github.io/` if you named the repo `yourusername.github.io`

### Making Updates

After the initial setup, updating your site is simple:

```bash
# Make your changes, then:
git add .
git commit -m "Description of your changes"
git push
```

GitHub Actions will automatically rebuild and deploy your site.

## Troubleshooting

### Site shows 404

- Make sure the `base` in `astro.config.mjs` matches your repository name
- Check that GitHub Pages source is set to "GitHub Actions" in Settings > Pages
- Wait a few minutes after deployment for DNS propagation

### Build fails

- Check the Actions tab for error messages
- Ensure all dependencies are in `package.json`
- Verify markdown frontmatter is valid YAML

### Images or links are broken

- Use relative paths from the `public/` folder: `/image.png`
- For links, use Astro's `base` path handling or absolute paths

## Project Structure

```
website/
├── public/              # Static assets (images, etc.)
├── src/
│   ├── content/
│   │   └── blog/        # Blog posts (markdown)
│   ├── layouts/
│   │   └── BaseLayout.astro
│   └── pages/
│       ├── index.astro  # Home page
│       └── blog/
│           ├── index.astro      # Blog listing
│           └── [...slug].astro  # Individual posts
├── astro.config.mjs
├── package.json
└── README.md
```

## Customization

### Changing Colors

Edit the CSS variables in `src/layouts/BaseLayout.astro`:

```css
:root {
  --color-bg: #0a0a0f;
  --color-accent: #3b82f6;
  /* ... */
}
```

### Adding New Pages

Create new `.astro` files in `src/pages/`. The file path becomes the URL route.

### Adding a Profile Photo

1. Add your photo to the `public/` folder (e.g., `public/profile.jpg`)
2. Reference it in your pages with `/profile.jpg`

## License

Personal website - All rights reserved.
