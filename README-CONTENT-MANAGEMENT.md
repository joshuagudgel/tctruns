# Event Content Management Guide

This guide explains how to manage race event information for the TCTRuns website.

## Two-File System

Each race event consists of **two files**:

1. **Structured Data**: `/data/events.yml` - Basic event info, pricing, logistics
2. **Rich Content**: `/content/event-details/{event-id}.md` - Detailed descriptions, course info, directions

## Adding a New Event

### Step 1: Add Basic Data

Add event details to `data/events.yml`:

```yaml
- id: "my-new-race" # Unique identifier (no spaces, lowercase)
  name: "My New Race" # Display name
  date: "2026-08-15" # YYYY-MM-DD format
  location: "City Park" # Event location

  # Card display
  primary_distance: "5K" # Main distance shown on cards
  registration_status: "open" # open, coming-soon, closed
  registration_url: "https://..." # Registration link
  featured: true # Show on homepage?

  # Organization & filtering
  year: 2026
  season: "summer" # spring, summer, fall, winter
  terrain: "road" # road, trail, mixed
  difficulty: "beginner" # beginner, intermediate, advanced
  series: "Summer Series" # Optional series name
  tags: ["5K", "family", "park"] # Search/filter tags

  # Pricing (multiple distances)
  distances:
    - distance: "5K"
      early_bird_price: 25
      regular_price: 35
      race_day_price: 45
      description: "Family-friendly distance"

  # Event logistics
  time: "08:00 AM"
  contact_email: "race@tctruns.com"
  # ... other basic fields
```

### Step 2: Create Rich Content

Create `/content/event-details/my-new-race.md`:

```markdown
---
title: "My New Race Details"
event_id: "my-new-race" # Must match ID from events.yml
---

## About This Race

Write a compelling description of your race here. You can use:

- **Bold text**
- _Italic text_
- [Links](https://example.com)
- Lists and bullet points

## Course Information

### Course Details

- **Distance:** 5K certified course
- **Surface:** Paved park pathways
- **Elevation:** Mostly flat with gentle hills

### Route Highlights

1. Start at City Park pavilion
2. Loop around the lake
3. Finish back at pavilion

## Registration Details

### What's Included

- Finisher medal
- Race t-shirt (optional)
- Post-race refreshments

## Directions & Parking

### Getting There

**Address:** City Park, 123 Park Avenue

### Parking

- Free parking in park lot (200 spaces)
- Overflow street parking available
```

## Content Writing Tips

### Use Clear Headings

Structure your content with consistent headings:

- `## About This Race`
- `## Course Information`
- `## Registration Details`
- `## Directions & Parking`

### Write for Runners

- Include practical details runners need to know
- Use bullet points for easy scanning
- Bold important information
- Include specific times, locations, and requirements

### Keep It Updated

- Update registration status in `events.yml`
- Add results/photos links after events
- Archive old events by changing `featured: false`

## File Organization

```
data/
  events.yml                         # All event structured data

content/event-details/              # Rich content per event
  spring-5k-challenge.md
  summer-trail-series-1.md
  fall-half-marathon.md
  winter-wonderland-5k.md
```

## Benefits of This System

✅ **Easy Writing**: Use familiar markdown instead of YAML  
✅ **Live Preview**: See formatting while you write  
✅ **Better Organization**: Data separate from content  
✅ **Scalable**: Add unlimited events without file bloat  
✅ **Version Control**: Clean diffs when content changes

## Questions?

Contact the development team or refer to existing event files for examples!
