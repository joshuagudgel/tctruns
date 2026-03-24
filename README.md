# TCTRuns Race Event Management Theme

A Hugo theme specifically designed for running event organizations, featuring data-driven content management that's friendly for non-technical website managers.

## 🎯 **Features**

- **Data-Driven Architecture**: Events and FAQs managed through simple YAML files
- **Responsive Design**: Mobile-first, accessible design
- **Event Management**: Automatic event sorting, status tracking, and registration management
- **FAQ System**: Searchable, categorized FAQ system with collapsible items
- **Homepage Features**: Dynamic featured events, quick stats, and community highlights
- **SEO Optimized**: Clean URLs, proper meta tags, and structured data ready

## 🏗️ **Theme Structure**

```
themes/simple-clean/
├── assets/
│   └── css/
│       ├── main.css              # Comprehensive race event styling
│       └── components/
│           ├── header.css
│           └── footer.css
├── layouts/
│   ├── baseof.html              # Base template
│   ├── home.html                # Homepage with featured events
│   ├── events/
│   │   ├── list.html            # Events listing page
│   │   └── single.html          # Individual event details
│   ├── _default/
│   │   └── faq.html             # FAQ page with search
│   └── partials/
│       ├── event-card.html      # Reusable event card component
│       ├── event-status.html    # Event status badges
│       ├── registration-button.html  # Dynamic registration buttons
│       └── faq-item.html        # FAQ item component
└── data/                        # Content managed here
    ├── events.yml               # All race event data
    └── faqs.yml                 # All FAQ content
```

## 📊 **Data Structure**

### **Events Data (`data/events.yml`)**

Each event contains:

- Basic info (name, date, time, location, distance)
- Registration details (URL, status, pricing)
- Course information (map, description)
- Post-race data (results, photos)
- Logistics (parking, packet pickup)
- Sponsors and awards

### **FAQ Data (`data/faqs.yml`)**

FAQs organized by:

- Category (Registration, Race Day, Training, etc.)
- Order within category
- Question and detailed answer

## 🚀 **Getting Started**

### **Prerequisites**

- Hugo Extended (v0.100+)
- Git

### **Setup**

1. Clone or download this theme
2. Update `hugo.toml` to use theme: `theme = 'simple-clean'`
3. Configure site title and baseURL
4. Add sample content to data files
5. Run `hugo server` for development

### **Content Management**

**For Non-Technical Users**: See [README-MANAGEMENT.md](README-MANAGEMENT.md) for detailed instructions on managing events and FAQs.

**For Developers**:

- Events are processed from `data/events.yml`
- FAQs are processed from `data/faqs.yml`
- All layouts use Hugo's data functions to render content
- Responsive design uses CSS Grid and Flexbox
- JavaScript enhances search and filtering

## 🎨 **Customization**

### **Colors and Styling**

Update CSS custom properties in `assets/css/main.css`:

```css
:root {
  --primary-color: #2563eb; /* Main brand color */
  --secondary-color: #f59e0b; /* Accent color */
  --success-color: #10b981; /* Success states */
  /* ... more variables */
}
```

### **Layout Modifications**

- Homepage: Edit `layouts/home.html`
- Events: Edit `layouts/events/list.html` and `layouts/events/single.html`
- FAQ: Edit `layouts/_default/faq.html`

### **Adding New Event Fields**

1. Add field to event template in YAML
2. Update `layouts/partials/event-card.html`
3. Update `layouts/events/single.html`
4. Add styling in `assets/css/main.css`

## 📱 **Responsive Design**

The theme is mobile-first with breakpoints:

- Mobile: < 768px (single column, stacked layout)
- Tablet: 768px+ (grid layouts, larger text)
- Desktop: 1200px+ (full grid layouts, optimal spacing)

## ♿ **Accessibility**

- Semantic HTML structure
- ARIA labels and roles where appropriate
- Keyboard navigation support
- High contrast color ratios
- Screen reader friendly
- Focus management for interactive elements

## 🔧 **Technical Details**

### **Hugo Features Used**

- Data files for content management
- Partials for component reusability
- Asset pipeline for CSS processing
- Date functions for event sorting
- Conditional logic for event status
- String functions for URL generation

### **JavaScript Features**

- FAQ search and filtering
- Event category filtering
- Collapsible FAQ items
- Registration click tracking
- Responsive navigation

### **Performance**

- Minimal JavaScript (< 5KB)
- Optimized CSS (mobile-first)
- No external dependencies
- Fast Hugo build times
- SEO optimized markup

## 🛠️ **Development**

### **Local Development**

```bash
# Start Hugo development server
hugo server -D

# Build for production
hugo --minify
```

### **CSS Development**

- Main styles: `assets/css/main.css`
- Component styles: `assets/css/components/`
- Uses CSS custom properties (variables)
- Mobile-first responsive design
- No CSS framework dependencies

### **Adding New Features**

1. Create new partial if reusable
2. Update data structure if needed
3. Add corresponding CSS styling
4. Test responsive behavior
5. Update documentation

## 📝 **Content Guidelines**

### **Event Management Best Practices**

- Use consistent date formatting (YYYY-MM-DD)
- Keep descriptions concise (150-200 characters)
- Update registration status regularly
- Add results/photos promptly after races
- Limit featured events to 2-3 at a time

### **FAQ Management**

- Group related questions by category
- Write clear, complete answers
- Use consistent tone and voice
- Update content seasonally
- Monitor which questions are searched most

## 🔗 **Integration**

### **Registration Systems**

Theme supports links to external registration platforms:

- RunSignUp
- Active.com
- Eventbrite
- Custom registration systems

### **Results Systems**

Post-race integration with:

- RunSignUp results
- ChronoTrack
- Custom results pages

### **Analytics**

- Google Analytics ready
- Event registration click tracking
- Newsletter signup tracking
- FAQ search analytics

## 📄 **License**

This theme is built for TCTRuns but can be adapted for other running organizations. Please maintain attribution in code comments.

## 🤝 **Support**

- **Content Management**: See README-MANAGEMENT.md
- **Technical Issues**: Contact webmaster@tctruns.com
- **Feature Requests**: Submit via GitHub issues

---

**Built with Hugo | Designed for Race Event Management | Mobile-First & Accessible**
