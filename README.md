# TRUESIP USA LLC - Corporate Website

Professional website for TRUESIP USA LLC, a wholesale voice termination provider.

## Company Information

- **Company**: TRUESIP USA LLC
- **Address**: 1209 Mountain Road Pl NE Ste R, Albuquerque, NM 87110
- **Email**: noc@truesip.net
- **Phone**: +1 (505) 376-1293

## Website Structure

```
truesip/
├── index.html              # Homepage
├── services.html           # Services page
├── about.html              # About page
├── contact.html            # Contact page
├── assets/
│   └── css/
│       └── styles.css      # Main stylesheet
└── policies/
    ├── index.html                      # Policies overview
    ├── acceptable-use-policy.html      # AUP
    ├── privacy-policy.html             # Privacy Policy
    ├── terms-of-service.html           # Terms of Service
    └── compliance-policy.html          # Compliance Policy
```

## Features

- Responsive design for mobile and desktop
- Professional branding with custom color scheme
- Comprehensive policy documentation
- Contact forms and NOC information
- Service descriptions for wholesale voice termination

## Deployment to DigitalOcean App Platform

### Option 1: GitHub Deployment (Recommended)

1. **Create a GitHub repository**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: TRUESIP website"
   git branch -M main
   git remote add origin <your-repo-url>
   git push -u origin main
   ```

2. **Deploy on DigitalOcean**:
   - Log in to DigitalOcean
   - Go to App Platform
   - Click "Create App"
   - Select GitHub as the source
   - Choose your repository
   - Configure as a Static Site
   - Set build command: (leave empty)
   - Set output directory: `/`
   - Deploy!

### Option 2: Direct Upload

1. **Prepare files**:
   - Ensure all files are in the `truesip` directory
   - No build step required (static HTML/CSS)

2. **Deploy on DigitalOcean**:
   - Log in to DigitalOcean
   - Go to App Platform
   - Click "Create App"
   - Choose "Static Site"
   - Upload your files or connect to your repository
   - Deploy!

### App Platform Configuration

For DigitalOcean App Platform, you may need an `.app.yaml` configuration file:

```yaml
name: truesip-website
static_sites:
  - name: web
    github:
      repo: your-username/truesip
      branch: main
    routes:
      - path: /
```

## Local Development

To test locally, you can use any static web server:

**Python 3**:
```bash
python -m http.server 8000
```

**Node.js (http-server)**:
```bash
npx http-server -p 8000
```

Then visit `http://localhost:8000` in your browser.

## Technologies Used

- HTML5
- CSS3 (with CSS Variables)
- Responsive Grid Layout
- No JavaScript dependencies (static site)

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Customization

To customize the site:

1. **Colors**: Edit CSS variables in `assets/css/styles.css`:
   ```css
   :root {
     --primary: #0a4f7e;
     --secondary: #00a8cc;
     --accent: #f26522;
   }
   ```

2. **Content**: Edit the HTML files directly
3. **Styles**: Modify `assets/css/styles.css`

## License

© 2026 TRUESIP USA LLC. All rights reserved.
