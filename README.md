# 🐟 Fish Express - Premium Frozen Fish Fillets

[![Deploy to GitHub Pages](https://github.com/hawariakbarr/fish-express-landing-page/actions/workflows/deploy-pages.yml/badge.svg)](https://github.com/hawariakbarr/fish-express-landing-page/actions/workflows/deploy-pages.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Premium frozen fish fillets website for Fish Express Bandung - serving families and businesses since 2014.

## 🌐 Live Demo

**[View Website](https://hawariakbarr.github.io/fish-express-landing-page/)**

## ✨ Features

- 📱 **Fully Responsive** - Optimized for mobile, tablet, and desktop
- 🎨 **Modern UI/UX** - Clean design with smooth animations
- 🌓 **Dark Mode** - Built-in theme switcher
- 🌍 **Bilingual** - Indonesian (ID) and English (EN) support
- ♿ **Accessible** - WCAG 2.1 compliant touch targets
- ⚡ **Fast** - Lazy loading images, optimized assets
- 🎯 **SEO Ready** - Meta tags and semantic HTML

## 🚀 Quick Start

### View Locally

Simply open the HTML file in your browser:

```bash
# On Linux/Mac
xdg-open fishexpress-website.html  # Linux
open fishexpress-website.html      # Mac

# On Windows
start fishexpress-website.html
```

### Deploy to GitHub Pages

1. Fork this repository
2. Go to **Settings** → **Pages**
3. Select **Deploy from a branch** → **master** → **root**
4. Click **Save**
5. Your site will be live at `https://yourusername.github.io/fish-express-landing-page/`

### Deploy to Netlify

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/hawariakbarr/fish-express-landing-page)

1. Click the button above
2. Connect your GitHub account
3. Deploy!

### Deploy to Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/hawariakbarr/fish-express-landing-page)

1. Click the button above
2. Import your repository
3. Deploy!

## 🛠️ Tech Stack

- **HTML5** - Semantic structure
- **CSS3** - Custom styles with CSS variables
- **JavaScript (Vanilla)** - No frameworks, pure JS
- **Google Fonts** - Fraunces & Plus Jakarta Sans

## 📱 Mobile Optimization

- ✅ 44px minimum touch targets (WCAG 2.1)
- ✅ 4 responsive breakpoints (1024px, 968px, 560px, 400px)
- ✅ Lazy loading images
- ✅ Reduced motion support
- ✅ Mobile-first navigation

## 🎨 Customization

### Change Colors

Edit the CSS variables in `<style>` section:

```css
:root[data-theme="light"] {
  --teal: #0FA3B1;        /* Primary brand color */
  --yellow: #F5C842;      /* Accent color */
  --cream: #FFF8E7;       /* Light background */
  --ink: #1A1B1F;         /* Text color */
}
```

### Update Content

All text content is in the `i18n` object in the `<script>` section:

```javascript
const i18n = {
  id: {
    'hero.title': 'Filet ikan <em>premium</em>...',
    // ...
  },
  en: {
    'hero.title': 'Premium fish <em>fillets</em>...',
    // ...
  }
};
```

### Update Contact Info

Search and replace:
- WhatsApp: `https://wa.me/628112210830`
- Instagram: `https://instagram.com/fishexpress_id`

## 📊 Performance

| Metric | Score |
|--------|-------|
| Lighthouse | 95+ |
| Mobile Friendly | ✅ |
| Touch Targets | ✅ WCAG 2.1 |
| Lazy Loading | ✅ |

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**hawariakbarr**

- GitHub: [@hawariakbarr](https://github.com/hawariakbarr)
- Fish Express: [@fishexpress_id](https://instagram.com/fishexpress_id)

## 🙏 Acknowledgments

- Google Fonts for beautiful typography
- GitHub Pages for free hosting
- Fish Express Bandung for the business

---

<p align="center">Made with 🐟 in Bandung, Indonesia</p>
