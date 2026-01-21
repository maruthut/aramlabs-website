# Cloudflare Pages Deployment Guide for aramailabs.com

## ✅ Step 1: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `aramlabs-website`
3. Description: "Official landing page for Aram AI Labs LLC"
4. **Keep it PUBLIC** (required for Cloudflare Pages free tier)
5. **DO NOT** initialize with README (we already have one)
6. Click "Create repository"

## ✅ Step 2: Push to GitHub

Run these commands in PowerShell:

```powershell
cd C:\Maruthu\Projects\aramlabs-website
git remote add origin https://github.com/YOUR_USERNAME/aramlabs-website.git
git branch -M main
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username.

## ✅ Step 3: Connect Cloudflare Pages

1. **Log in to Cloudflare**: https://dash.cloudflare.com/
2. Click **"Workers & Pages"** in left sidebar
3. Click **"Create application"** → **"Pages"** tab
4. Click **"Connect to Git"**
5. Authorize Cloudflare to access your GitHub
6. Select repository: `aramlabs-website`

## ✅ Step 4: Configure Build Settings

**IMPORTANT:** Cloudflare Pages automatically deploys static files!

**Framework preset:** None (Static HTML)

**Build settings:**
- **Build command:** `echo "No build required"`
- **Build output directory:** `.` (current directory - this is where your HTML files are)
- **Root directory:** (leave empty or `/`)

**OR if that doesn't work:**
- **Build command:** Leave empty and skip if it keeps spinning
- Try changing **Build output directory** to just `.` instead of `/`

Click **"Save and Deploy"**

### 🔧 If you already deployed with wrong settings:

1. Go to your Pages project in Cloudflare
2. Click **"Settings"** → **"Builds & deployments"**
3. Scroll to **"Build configuration"**
4. Click **"Edit configuration"**
5. **Build command:** Delete everything, leave it empty
6. **Build output directory:** Change to `/`
7. Click **"Save"**
8. Go to **"Deployments"** tab → Click **"Retry deployment"**

## ✅ Step 5: Connect Custom Domain (aramailabs.com)

1. After first deployment, go to **"Custom domains"** tab
2. Click **"Set up a custom domain"**
3. Enter: `aramailabs.com`
4. Cloudflare will show DNS records to add

**Since your domain is already on Cloudflare:**
- It will automatically add the CNAME record
- Should work immediately (no waiting for DNS)

5. Also add `www.aramailabs.com` as an alias:
   - Click "Set up a custom domain" again
   - Enter: `www.aramailabs.com`
   - Enable "Redirect to primary domain"

## ✅ Step 6: Verify Deployment

1. Wait 1-2 minutes for initial deployment
2. Test the Cloudflare URL (e.g., `aramlabs-website.pages.dev`)
3. Test your custom domain: https://aramailabs.com
4. Verify HTTPS is working (automatic with Cloudflare)

## 🔄 Future Updates

Every time you push to GitHub main branch, Cloudflare auto-deploys:

```powershell
cd C:\Maruthu\Projects\aramlabs-website
# Make changes to files
git add .
git commit -m "Update landing page"
git push
```

Cloudflare deploys in ~30 seconds! 🚀

## 📊 Important Settings to Configure

After deployment:
1. **Analytics**: Enable Web Analytics in Pages dashboard
2. **Security Headers**: Already configured in Cloudflare
3. **SSL/TLS**: Ensure set to "Full (strict)"
4. **Always Use HTTPS**: Enable under SSL/TLS → Edge Certificates

## ✅ What You Get

- ✅ Free hosting (unlimited bandwidth)
- ✅ Global CDN (fast worldwide)
- ✅ Automatic HTTPS
- ✅ Auto-deploy on git push
- ✅ DDoS protection
- ✅ 99.99% uptime

---

**Questions?** Run these checks after deployment:
- Test form submission: https://aramailabs.com → Early Access form
- Check privacy link: https://aramailabs.com/privacy.html
- Check terms link: https://aramailabs.com/terms.html
- Verify mobile responsive: Open on phone
