# TCTRuns Website Management Guide

A comprehensive guide for non-technical website managers to update race events, FAQs, and content on the TCTRuns website.

## 🎯 **Quick Start**

This website uses a two-part system for managing race events:

1. **Event Data**: Basic information stored in `data/events.yml` (required)
2. **Event Details**: Rich content added to files in `content/events/` (optional)

### **What You Can Manage:**

- ✅ Race events (dates, pricing, registration)
- ✅ Detailed event descriptions and course information
- ✅ Multiple distance options with individual pricing
- ✅ Frequently Asked Questions
- ✅ Event status and registration links

### **What's Automatic:**

- ✅ Event sorting by date and season
- ✅ Past vs. upcoming event organization
- ✅ Registration status displays
- ✅ Mobile-responsive design
- ✅ Event filtering and search

## 📅 **Managing Race Events**

### **Two-Part Event System**

Each race event consists of:

1. **Basic Data** in `data/events.yml` - Required information like dates, pricing, logistics
2. **Detailed Content** in `content/events/{event-id}.md` - Optional rich descriptions, course details, directions

### **Step 1: Adding Event Data (Required)**

1. Open the file: `data/events.yml`
2. Find the `events:` section
3. Add your new event using the template below
4. Save the file

#### **Event Data Template:**

```yaml
- id: "my-spring-5k" # Unique ID (lowercase, no spaces)
  name: "My Spring 5K" # Display name
  date: "2026-05-15" # YYYY-MM-DD format
  location: "City Park" # Event location

  # Card display
  primary_distance: "5K" # Main distance shown on event cards
  registration_status: "open" # open, closed, coming-soon
  registration_url: "https://register.example.com"
  featured: true # Show on homepage? (true/false)

  # Organization & filtering
  year: 2026
  season: "spring" # spring, summer, fall, winter
  terrain: "road" # road, trail, mixed
  difficulty: "beginner" # beginner, intermediate, advanced
  tags: ["5K", "family", "park"] # Search/filter tags

  # Distance options and pricing
  distances:
    - distance: "5K"
      early_bird_price: 25 # Numbers only (no $ sign)
      regular_price: 35
      race_day_price: 45
      description: "Perfect for beginners and families"

  # Event logistics
  time: "08:00 AM"
  contact_email: "race@tctruns.com"
  awards: "Overall winners and age group awards"
  packet_pickup: "Friday 5-7 PM at Sports Store"
  parking: "Free parking at City Park"
  course_map_url: "" # Add PDF link if available
  results_url: "" # Add after race
  photos_url: "" # Add after race
  sponsors: ["Local Business", "Sports Store"]
```

### **Step 2: Adding Detailed Content (Optional)**

For races that need detailed descriptions, course information, or directions:

1. Create file: `content/events/{event-id}.md` (use same ID as Step 1)
2. Add the content using the template below
3. Save the file

#### **Event Content Template:**

```markdown
---
title: "My Spring 5K"
date: 2026-05-15
event_id: "my-spring-5k" # Must match ID from events.yml
layout: "single"
---

## About This Race

Write a compelling description of your race here. Explain what makes this event special, who should participate, and what the experience will be like.

## Course Information

### Course Details

- **Distance:** USATF certified 5K course
- **Surface:** Paved city streets and park paths
- **Terrain:** Mostly flat with gentle rolling hills
- **Start/Finish:** City Park Main Pavilion

### Route Highlights

1. Start at City Park pavilion
2. Loop through historic downtown (mile 1)
3. Return via scenic riverfront path (miles 2-3)
4. Finish back at pavilion with crowd support

## Registration Information

### What's Included

- Finisher medal
- Technical race t-shirt
- Post-race refreshments
- Professional timing and results

### Registration Deadlines

- **Early Bird:** Through April 15th
- **Regular:** April 16th - May 10th
- **Race Day:** Available until 7:45 AM (if not sold out)

## Race Day Information

### Schedule

- 7:00 AM - Packet pickup opens
- 7:45 AM - Final announcements
- 8:00 AM - Race start
- 9:30 AM - Awards ceremony

### Getting There

**Address:** City Park, 123 Main Street

**Parking:** Free parking in park lot. Overflow parking at Community Center (2 blocks).

**Public Transit:** Bus route 15 stops at Park Avenue entrance.
```

## 📊 **Field Reference Guide**

### **Required Fields (events.yml)**

| Field | Description | Example |
|-------|-------------|---------||
| `id` | Unique identifier (lowercase, no spaces) | `"spring-5k-2026"` |
| `name` | Event display name | `"Spring 5K Challenge"` |
| `date` | Event date (YYYY-MM-DD) | `"2026-04-15"` |
| `location` | Event location | `"Riverside Park"` |
| `primary_distance` | Main distance for cards | `"5K"` |
| `registration_status` | Current status | `"open"` |
| `year` | Event year | `2026` |
| `season` | Event season | `"spring"` |
| `distances` | Distance/pricing options | See template |
| `time` | Race start time | `"08:00 AM"` |

### **Registration Status Options**

- **`"open"`** - Registration currently available
- **`"coming-soon"`** - Registration will open later
- **`"closed"`** - Registration has ended

### **Season Options**

- `"spring"`, `"summer"`, `"fall"`, `"winter"`

### **Terrain Options**

- `"road"` - Paved roads/paths
- `"trail"` - Natural trails
- `"mixed"` - Combination

### **Difficulty Options**

- `"beginner"` - Easy for new runners
- `"intermediate"` - Moderate challenge
- `"advanced"` - Challenging course

## ❓ **Managing FAQs**

### **Adding a New FAQ**

1. Open the file: `data/faqs.yml`
2. Find the appropriate category or create a new one
3. Add your new FAQ using this format:

```yaml
- category: "Category Name"
  question: "Your question here?"
  answer: "Your detailed answer here. You can include multiple sentences and even basic formatting."
  order: 1
```

### **FAQ Categories**

Existing categories (use these when possible):

- `Registration`
- `Race Day`
- `Course & Training`
- `Results & Awards`
- `General`
- `Volunteering`

### **FAQ Field Explanations**

| Field      | Description                                 | Example                               |
| ---------- | ------------------------------------------- | ------------------------------------- |
| `category` | Group FAQs by topic                         | "Registration"                        |
| `question` | The question people are asking              | "How do I register?"                  |
| `answer`   | Complete answer (can be multiple sentences) | "Registration is available online..." |
| `order`    | Display order within category (1, 2, 3...)  | 1                                     |

### **Updating Existing FAQs**

1. Find the FAQ in `data/faqs.yml`
2. Update the `question` or `answer` text
3. Save the file

## 🔧 **Common Tasks**

### **Opening Registration**

1. Update `registration_status: "open"`
2. Add the `registration_url`
3. Verify all event details are correct

### **After Race Completion**

1. Change `registration_status: "closed"`
2. Add `results_url` when available
3. Add `photos_url` when available
4. Optionally set `featured: false`

### **Multiple Distance Events**

```yaml
distances:
  - distance: "5K"
    early_bird_price: 25
    regular_price: 35
    race_day_price: 45
    description: "Perfect for beginners"
  - distance: "10K"
    early_bird_price: 35
    regular_price: 45
    race_day_price: 55
    description: "Intermediate challenge"
```

## ⚠️ **Important Guidelines**

### **File Format Rules**

- **Indentation**: Use 2 spaces per level
- **Quotes**: Always use quotes around text
- **Dates**: Use YYYY-MM-DD format only
- **Prices**: Use numbers only (no $ signs)
- **Lists**: Use `["item1", "item2"]` format

### **File Locations**

- **Event Data**: `data/events.yml`
- **Event Details**: `content/events/{event-id}.md`
- **FAQs**: `data/faqs.yml`

### **Testing Changes**

After making changes:

1. Save all files
2. Check the website preview
3. Verify event displays correctly
4. Test registration links

## 🚀 **Publishing Changes**

### **Local Development**

If working locally:

1. Save your changes to the data files
2. The website will automatically update

### **Live Website**

Changes to data files will automatically appear on the live website within a few minutes.

## 📞 **Getting Help**

### **Technical Issues**

- Email: `webmaster@tctruns.com`
- Include: What you were trying to do, what went wrong, and any error messages

### **Content Questions**

- Email: `info@tctruns.com`
- For questions about event details, FAQs, or website content

### **Emergency Contact**

- Phone: `(555) 123-4567`
- For urgent website issues during race registration periods

## 📋 **Quick Reference**

### **Sample Complete Event (YAML)**

```yaml
- id: "summer-5k-2026"
  name: "Summer 5K Fun Run"
  date: "2026-07-04"
  location: "City Park"

  primary_distance: "5K"
  registration_status: "open"
  registration_url: "https://register.tctruns.com/summer-5k"
  featured: true

  year: 2026
  season: "summer"
  terrain: "road"
  difficulty: "beginner"
  tags: ["5K", "family", "patriotic"]

  distances:
    - distance: "5K"
      early_bird_price: 20
      regular_price: 30
      race_day_price: 40
      description: "Patriotic fun run with post-race BBQ"

  time: "08:00 AM"
  contact_email: "summer5k@tctruns.com"
  awards: "Overall winners, kids medals"
  packet_pickup: "July 3rd 5-7 PM, Race day 7:00-7:45 AM"
  parking: "Free parking at City Park"
  sponsors: ["City Sports", "Healthy Living"]
```

---

_Last updated: March 2026_
_For website issues, contact webmaster@tctruns.com_
