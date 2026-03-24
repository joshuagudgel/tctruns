---
name: race-events-hugo-theme
description: "HUGO THEME DEVELOPMENT — Build a race event management theme for Hugo that combines structured data (YAML) with rich content (markdown) for flexible event management. Use when: creating Hugo themes, setting up hybrid content management, building race/event websites, working with YAML data files and markdown content, creating scalable content workflows for Hugo."
---

# Race Event Management Theme Development

You are an expert Hugo theme developer creating a comprehensive race event management theme. Focus on simplifying content management for non-technical website managers using a hybrid data + content approach.

## 🎯 **Primary Goals**

### **Hybrid Content Management**

- Events managed through structured data (`data/events.yml`) + rich content (`content/events/`)
- FAQs managed through single YAML file (`data/faqs.yml`)
- Structured data for filtering, pricing, logistics + markdown for detailed descriptions
- Clear documentation for both data and content management

### **Scalable Architecture**

- YAML data files for structured information (dates, pricing, metadata)
- Individual markdown files for rich content (course details, directions, training tips)
- Template-based rendering with hybrid data sources
- Automatic sorting, filtering, and indexing
- Dynamic event status (upcoming/past/registration open)

### **Website Manager Friendly**

- Structured data in centralized YAML files
- Rich content in individual markdown files per event
- Clear field names and examples for both data types
- Separation of concerns (data vs. narrative content)
- Simple two-step workflow for adding events

## 🗂️ **Current Data Structures**

### **Events Data Format** (`data/events.yml`)

```yaml
events:
  - id: "spring-5k-challenge" # Unique identifier (lowercase, no spaces)
    name: "Spring 5K Challenge" # Display name
    date: "2026-04-15" # YYYY-MM-DD format
    location: "Riverside Park, Downtown" # Event location

    # Card display data
    primary_distance: "5K" # Main distance shown on event cards
    registration_status: "open" # open, closed, coming-soon
    registration_url: "https://register.tctruns.com/spring-5k"
    featured: true # Show on homepage

    # Indexing & filtering
    year: 2026
    season: "spring" # spring, summer, fall, winter
    terrain: "road" # road, trail, mixed
    difficulty: "beginner" # beginner, intermediate, advanced
    tags: ["5K", "flat", "PR-friendly", "family", "park"]

    # Distance options & pricing
    distances:
      - distance: "5K"
        early_bird_price: 25 # Numbers only (no $ signs)
        regular_price: 35
        race_day_price: 45
        description: "Flat, fast course perfect for PRs and beginners"

    # Event logistics
    time: "07:00 AM"
    contact_email: "spring5k@tctruns.com"
    awards: "Overall winners, age group awards"
    packet_pickup: "Friday 5-7 PM at Fleet Feet, Race day 6:30-7:45 AM"
    parking: "Free parking at Riverside Park, overflow at City Hall"
    course_map_url: "https://tctruns.com/maps/spring-5k.pdf"
    results_url: "" # Add after race
    photos_url: "" # Add after race
    sponsors: ["Fleet Feet Sports", "Medical Center", "Local Bank"]
```

### **Event Content Format** (`content/events/{event-id}.md`)

```markdown
---
title: "Spring 5K Challenge"
date: 2026-04-15
event_id: "spring-5k-challenge" # Must match ID in events.yml
layout: "single"
---

## About This Race

Join us for our signature spring race through beautiful Riverside Park.

## Course Information

### Course Details

- **Distance:** USATF certified 5K course
- **Surface:** Paved park pathways
- **Terrain:** Flat with gentle rolling hills

## Race Day Information

### Schedule

- 6:30 AM - Packet pickup opens
- 7:00 AM - Race start
- 8:30 AM - Awards ceremony
```

### **FAQ Data Format** (`data/faqs.yml`)

```yaml
faqs:
  - category: "Registration"
    question: "How many aid stations will there be and what kinds of food can I expect?"
    answer: "There will always be AT LEAST one fully stocked aid station at all our races. We will always have water, Gatorade and soda in stock for you. We also stock up on chips, chocolates, candy, power bars, sandwiches, and fruit, while ensuring that vegetarian and vegan options are always available.\n\nWe strongly encourage all longer distance runners with special dietary needs to prepare their own nutrition and place it in a drop bag that can be checked in with staff the morning of the race."
    order: 1
  - category: "Race Day"
    question: "Where do I park my car?"
    answer: "All races are conveniently located within a short walk from parking lots. We ensure that you don't have to pay to park for the majority of our races, but please car pool if you can!"
    order: 1
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
   - Hybrid data display (YAML + markdown content)
   - Full event details with structured logistics
   - Registration integration
   - Rich course information from markdown
   - Dynamic content sections

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
{{ $upcoming := where .Site.Data.events.events "date" "ge" (now.Format "2006-01-02") }}

{{/* Sort events by date */}}
{{ $sorted := sort $upcoming "date" }}

{{/* Filter featured events */}}
{{ $featured := where $upcoming "featured" true }}

{{/* Get event by ID for content pages */}}
{{ $eventId := .Params.event_id }}
{{ $event := index (where .Site.Data.events.events "id" $eventId) 0 }}

{{/* Filter by season/terrain/difficulty */}}
{{ $springEvents := where .Site.Data.events.events "season" "spring" }}
{{ $trailEvents := where .Site.Data.events.events "terrain" "trail" }}
{{ $beginnerEvents := where .Site.Data.events.events "difficulty" "beginner" }}
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

- How to add new events (2-step process: YAML + markdown)
- Event data field explanations and examples
- Content writing guidelines for markdown files
- FAQ management process
- Event lifecycle management (registration → race → results)
- Common troubleshooting
- Deployment instructions

### **Hybrid Content Workflow**

1. **Add Event Data**: Create structured entry in `data/events.yml`
2. **Create Content File**: Add rich content to `content/events/{event-id}.md`
3. **Templates**: Process both data sources in event templates
4. **Testing**: Verify both structured data and content render correctly

### **Testing Requirements**

- Test with multiple events (past, upcoming, featured)
- Verify date handling and sorting with indexing fields
- Test filtering by season, terrain, difficulty, and tags
- Check responsive design on various devices
- Validate structured data + markdown content integration
- Test with empty content files (YAML-only events)
- Validate HTML and accessibility
- Test event lifecycle (registration → active → past)

## 🎨 **Styling Approach**

### **CSS Architecture**

- Use Hugo's asset pipeline
- SCSS for better organization
- Component-based styling
- Utility classes for common patterns
- Support for both data-driven and content-driven layouts

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

- Use Hugo's data handling for structured content
- Use content files for rich narrative content
- Implement proper error handling for missing data/content
- Follow Hugo naming conventions
- Use shortcodes for complex elements
- Leverage Hugo's indexing and filtering capabilities

### **Content Management**

- Provide clear examples in both YAML and markdown formats
- Add comments explaining field purposes in YAML files
- Include validation where possible
- Document the two-file workflow clearly
- Show relationship between YAML IDs and markdown filenames

### **SEO & Performance**

- Structured data for events
- Open Graph tags
- Optimized images
- Fast page load times

Always prioritize simplicity for content managers while maintaining flexibility for developers. Focus on creating clear, documented workflows that non-technical users can follow confidently. The hybrid approach allows structured data management for filtering/sorting while enabling rich content creation for detailed event descriptions.

## 📂 **File Organization**

```
data/
  events.yml                    # Structured event data
  faqs.yml                     # FAQ data

content/events/               # Rich event content
  spring-5k-challenge.md      # Event ID: spring-5k-challenge
  summer-trail-series-1.md    # Event ID: summer-trail-series-1
  fall-half-marathon.md       # Event ID: fall-half-marathon
  _index.md                   # Events section page

layouts/events/
  list.html                   # Events listing page
  single.html                 # Individual event pages (hybrid data)

layouts/partials/
  event-card.html            # Event card component
  event-status.html          # Status badges
  registration-button.html   # Registration CTA
  faq-item.html             # FAQ display
```
