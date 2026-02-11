# TRUESIP Website - Deployment Guide

## Quick Start: Deploy to DigitalOcean App Platform

### Prerequisites
- DigitalOcean account
- Git installed on your machine
- GitHub account (recommended)

### Step 1: Initialize Git Repository

```bash
cd C:\Users\damio\Desktop\truesip
git init
git add .
git commit -m "Initial commit: TRUESIP USA LLC website"
```

### Step 2: Push to GitHub

1. Create a new repository on GitHub (e.g., `truesip-website`)
2. Push your code:

```bash
git remote add origin https://github.com/YOUR-USERNAME/truesip-website.git
git branch -M main
git push -u origin main
```

### Step 3: Deploy on DigitalOcean

1. **Log in to DigitalOcean**: https://cloud.digitalocean.com/
2. **Navigate to App Platform**: Click "Apps" in the left sidebar
3. **Create New App**: Click "Create App" button
4. **Connect GitHub**:
   - Select "GitHub" as the source
   - Authorize DigitalOcean to access your repositories
   - Select your `truesip-website` repository
   - Choose the `main` branch
5. **Configure the App**:
   - **Type**: Static Site
   - **Name**: truesip-website
   - **Build Command**: (leave empty)
   - **Output Directory**: `/`
   - **HTTP Port**: (auto-detected)
6. **Select Region**: Choose closest to your users (e.g., NYC)
7. **Choose Plan**: 
   - Basic (Free tier available for static sites)
   - $0/month for static sites with fair usage
8. **Review & Deploy**: Click "Create Resources"

### Step 4: Configure Custom Domain (Optional)

After deployment:

1. Go to your app settings
2. Click "Domains"
3. Click "Add Domain"
4. Enter your domain (e.g., `truesip.com` or `www.truesip.com`)
5. Add the DNS records shown to your domain registrar:
   - **CNAME record**: Point your domain to the provided DigitalOcean URL
6. Wait for DNS propagation (can take up to 48 hours)

### Automatic Deployments

Once connected to GitHub, DigitalOcean will automatically redeploy your site whenever you push changes to the `main` branch:

```bash
# Make changes to your files
git add .
git commit -m "Update content"
git push origin main
# DigitalOcean will automatically rebuild and deploy!
```

## Alternative: Deploy without GitHub

If you prefer not to use GitHub:

1. Create a `.zip` file of your website
2. In DigitalOcean App Platform, choose "Upload Source Code"
3. Upload your `.zip` file
4. Configure as a Static Site
5. Deploy

**Note**: Without GitHub integration, you'll need to manually upload new versions.

## Environment Configuration

The `.do/app.yaml` file is already configured for you:

```yaml
name: truesip-website
region: nyc

static_sites:
  - name: web
    source_dir: /
    index_document: index.html
    error_document: index.html
    catchall_document: index.html
    routes:
      - path: /
```

## Testing Before Deployment

Test locally with Python:

```bash
cd C:\Users\damio\Desktop\truesip
python -m http.server 8000
```

Visit: http://localhost:8000

## Post-Deployment Checklist

- [ ] Website loads correctly at the provided URL
- [ ] All pages are accessible (Home, Services, About, Contact, Policies)
- [ ] All internal links work
- [ ] Contact information is correct
- [ ] Policy pages display properly
- [ ] Mobile responsiveness works
- [ ] Custom domain configured (if applicable)
- [ ] SSL/HTTPS is enabled (automatic with DigitalOcean)

## Estimated Costs

- **Static Site Hosting**: $0/month (with fair usage limits)
- **Custom Domain** (if needed): $12-15/year from registrar
- **Bandwidth**: Included with static site plan

## Support

- DigitalOcean Docs: https://docs.digitalocean.com/products/app-platform/
- DigitalOcean Support: Available through your dashboard
- TRUESIP NOC: noc@truesip.net

## Troubleshooting

### Site Not Loading
- Check deployment logs in DigitalOcean dashboard
- Ensure all files are committed to Git
- Verify branch name is correct

### CSS Not Loading
- Check that file paths are correct (relative paths)
- Ensure `assets/css/styles.css` is in the repository
- Clear browser cache

### 404 Errors
- Verify `index_document` is set to `index.html` in app.yaml
- Check that all referenced files exist in the repository

## Making Updates

1. Edit files locally
2. Test changes with local server
3. Commit and push to GitHub:
   ```bash
   git add .
   git commit -m "Description of changes"
   git push origin main
   ```
4. DigitalOcean auto-deploys within 2-3 minutes

---

**Ready to deploy!** Follow the steps above and your TRUESIP website will be live in minutes.
