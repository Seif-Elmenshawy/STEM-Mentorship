# STEM Mentorship Platform

A modern educational platform providing comprehensive STEM resources, practice tests, and mentorship programs.

## 🚀 Features

- **Modern UI/UX**: Responsive design with smooth animations
- **Resource Library**: Subject-organized PDFs with download tracking
- **Contact Management**: Social media integration and contact forms
- **Performance Optimized**: Fast loading with fallback mechanisms
- **Mobile Friendly**: Responsive design for all devices
- **Bilingual Support**: Arabic/English language switching
- **Serverless Architecture**: Vercel deployment with edge functions

## 🛠️ Technical Stack

- **Backend**: Node.js with Express.js
- **Frontend**: EJS templating with modern CSS
- **Deployment**: Vercel serverless functions
- **Styling**: Custom CSS with animations (AOS)

## 🔧 Local Development

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Start development server:**
   ```bash
   npm run dev
   ```

3. **Start production server:**
   ```bash
   npm start
   ```

4. **Check for syntax errors:**
   ```bash
   node -c app.js
   ```

## 🌐 Deployment (Vercel)

### Automatic Deployment
1. Connect your GitHub repository to Vercel
2. Vercel will automatically deploy on push to main branch
3. Environment: Node.js 18.x

### Manual Deployment
```bash
npx vercel --prod
```

### Deployment Configuration

**vercel.json features:**
- 25-second function timeout (before Vercel's 30s limit)
- Static file serving for `/public` routes
- Fallback routing to Express app
- Favicon handling

### Troubleshooting Deployment Issues

#### 504 Gateway Timeout
- **Cause**: EJS rendering taking too long
- **Solution**: App includes 8-second EJS timeout with HTML fallbacks
- **Fallback**: Static `index.html` serves if Node.js fails

#### Infinite Loading
- **Cause**: EJS view errors or missing dependencies
- **Solution**: All routes have try/catch with HTML fallbacks
- **Monitoring**: Check Vercel function logs

## 🚨 Error Handling

### Built-in Safeguards
1. **Global Request Timeout**: 25-second limit per request
2. **EJS Render Timeout**: 8-second limit with fallback HTML
3. **Static Fallback**: `public/index.html` as last resort
4. **Error Pages**: Custom 404 and 500 error pages
5. **API Fallbacks**: All API routes return valid JSON

### Health Monitoring
- `/health` - JSON health check endpoint
- `/test` - Detailed server status page
- Console logging for all requests and errors
   ```
   vercel login
   ```

3. Deploy to Vercel:
   ```
   vercel
   ```

4. For production deployment:
   ```
   vercel --prod
   ```

### Using Vercel Dashboard

1. Push your code to a Git repository (GitHub, GitLab, or Bitbucket)
2. Import your project in the Vercel dashboard
3. Select the repository and configure build settings if needed
4. Deploy

## Project Structure

- `/public` - Static assets (CSS, JS, images)
- `/views` - EJS templates
  - `/partials` - Reusable EJS components
- `/api` - Serverless API functions
- `app.js` - Express application setup
- `vercel.json` - Vercel deployment configuration