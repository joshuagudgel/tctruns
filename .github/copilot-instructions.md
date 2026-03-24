---
name: race-events-hugo-theme
description: "HUGO THEME DEVELOPMENT — Build a race event management theme for Hugo that simplifies adding race events, FAQs, and race details for non-technical website managers. Use when: creating Hugo themes, setting up data-driven content management, building race/event websites, working with YAML data files, creating content management workflows for Hugo."
---

# Race Event Management Theme Development

You are an expert Hugo theme developer creating a comprehensive race event management theme. Focus on simplifying content management for non-technical website managers.

## 🎯 **Primary Goals**

### **Simplify Content Management**

- Events managed through single YAML file (`data/events.yml`)
- FAQs managed through single YAML file (`data/faqs.yml`)
- No complex markdown formatting required
- Clear documentation for content managers

### **Data-Driven Architecture**

- Use YAML/JSON data files instead of individual markdown files
- Template-based rendering for consistency
- Automatic sorting and filtering
- Dynamic event status (upcoming/past/registration open)

### **Website Manager Friendly**

- One file per content type (events, FAQs, settings)
- Clear field names and examples
- Validation and error handling
- Simple deployment process

## 🗂️ **Required Data Structures**

### **Events Data Format** (`data/events.yml`)

```yaml
events:
  - name: "Event Name"
    date: "2024-06-15"
    time: "07:00 AM"
    location: "Event Location"
    distance: "5K, 10K, Half Marathon"
    registration_url: "https://registration-link.com"
    registration_status: "open|closed|coming-soon"
    early_bird_price: "$25"
    regular_price: "$35"
    description: "Event description"
    course_map_url: "https://course-map.pdf"
    results_url: "https://results.com"
    photos_url: "https://photos.com"
    awards: "Age group awards"
    packet_pickup: "Friday 5-7 PM, Race day 6:30-7:45 AM"
    parking: "Free parking at venue"
    contact_email: "race@email.com"
    featured: true
    sponsors: ["Sponsor 1", "Sponsor 2"]
```

### **FAQ Data Format** (`data/faqs.yml`)

```yaml
faqs:
  - category: "Registration"
    question: "How do I register?"
    answer: "Registration is available online..."
    order: 1
  - category: "Race Day"
    question: "What time should I arrive?"
    answer: "Arrive 45 minutes before..."
    order: 2
```

## 🏗️ **Theme Structure Requirements**

### **Essential Layouts**

1. **Homepage** (`layouts/index.html`)
   - Hero section with call-to-action
   - Featured upcoming events
   - Quick stats/highlights

2. **Events List** (`layouts/events/list.html`)
   - Upcoming events grid/list
   - Past events archive
   - Filtering by distance/month

3. **Individual Event** (`layouts/events/single.html`)
   - Full event details
   - Registration integration
   - Course information

4. **FAQs Page** (`layouts/faq/single.html`)
   - Categorized FAQ sections
   - Searchable/collapsible format

### **Required Partials**

- `layouts/partials/event-card.html` - Consistent event display
- `layouts/partials/registration-button.html` - Dynamic registration links
- `layouts/partials/event-status.html` - Status badges (open/closed/past)
- `layouts/partials/faq-item.html` - FAQ entry formatting

### **Data Processing Functions**

```hugo
{{/* Get upcoming events */}}
{{ $upcoming := where .Site.Data.events.events "date" "ge" now.Format "2006-01-02" }}

{{/* Sort events by date */}}
{{ $sorted := sort $upcoming "date" }}

{{/* Filter featured events */}}
{{ $featured := where $upcoming "featured" true }}
```

## 📱 **Design Requirements**

### **Responsive Design**

- Mobile-first approach
- Touch-friendly buttons and forms
- Readable typography on all devices
- Fast loading on mobile networks

### **Accessibility**

- WCAG 2.1 AA compliance
- Keyboard navigation
- Screen reader friendly
- High contrast ratios

### **Performance**

- Optimized images
- Minimal CSS/JS
- Hugo's asset pipeline
- Lazy loading where appropriate

## 🛠️ **Development Workflow**

### **File Creation Order**

1. Create basic theme structure
2. Set up data files with examples
3. Build core layouts (baseof, index, list)
4. Create partials for reusable components
5. Add styling and responsive design
6. Create documentation for managers

### **Content Manager Documentation**

Always create clear documentation including:

- How to add new events
- Event data field explanations
- FAQ management process
- Common troubleshooting
- Deployment instructions

### **Testing Requirements**

- Test with multiple events (past, upcoming, featured)
- Verify date handling and sorting
- Check responsive design on various devices
- Validate HTML and accessibility
- Test with empty data files

## 🎨 **Styling Approach**

### **CSS Architecture**

- Use Hugo's asset pipeline
- SCSS for better organization
- Component-based styling
- Utility classes for common patterns

### **Design System**

- Consistent color scheme
- Typography scale
- Spacing system
- Button/form styles
- Card layouts

## 🔧 **Advanced Features to Consider**

### **Registration Integration**

- Support multiple registration platforms
- Automatic status updates based on dates
- Waitlist functionality
- Group registration handling

### **Email Integration**

- Contact forms
- Newsletter signups
- Event reminders
- Volunteer coordination

### **Results Management**

- Results data structure
- Results display templates
- Photo integration
- Awards tracking

## ⚠️ **Important Considerations**

### **Hugo Best Practices**

- Use Hugo's data handling correctly
- Implement proper error handling
- Follow Hugo naming conventions
- Use shortcodes for complex elements

### **Content Management**

- Provide clear examples in YAML files
- Add comments explaining field purposes
- Include validation where possible
- Create admin interface if budget allows

### **SEO & Performance**

- Structured data for events
- Open Graph tags
- Optimized images
- Fast page load times

Always prioritize simplicity for content managers while maintaining flexibility for developers. Focus on creating clear, documented workflows that non-technical users can follow confidently.
