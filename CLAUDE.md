# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Start development server (includes draft content)
hugo server -D

# Build for production
hugo --minify
```

Hugo Extended v0.100+ is required.

## Architecture

This is a Hugo static site ("Troy's California Trail Runs") using a custom theme at `themes/simple-clean/`. It uses a **hybrid content model**: structured event metadata lives in YAML data files, while rich narrative content lives in Markdown files.

### Content Flow for Events

Adding an event requires two files:

1. **Structured data** — add an entry to `data/events.yml` with a unique `id` (lowercase, hyphenated, e.g. `spring-5k-challenge`)
2. **Rich content** — create `content/events/{event-id}.md` with front matter field `event_id` matching the YAML `id`

The event single page template (`themes/simple-clean/layouts/events/single.html`) joins these at render time: it looks up the event by `event_id` from `.Params` in `data/events.yml`, then renders `.Content` from the markdown body.

### Data Files

- `data/events.yml` — all event metadata: dates, distances, pricing, registration status/URL, logistics, sponsors
- `data/faqs.yml` — FAQ entries with `category`, `question`, `answer`, `order`

### Key `events.yml` Fields

| Field | Notes |
|---|---|
| `id` | Must match the markdown filename and `event_id` front matter |
| `registration_status` | `open`, `closed`, or `coming-soon` |
| `featured` | `true` to show on homepage |
| `terrain` | `road`, `trail`, or `mixed` |
| `distances[].regular_price` | Numbers only, no `$` sign |
| `results_url` / `photos_url` | Add after the race; shown only for past events |

### Theme Layouts

- `themes/simple-clean/layouts/home.html` — homepage with featured events hero
- `themes/simple-clean/layouts/events/list.html` — events listing (upcoming + past)
- `themes/simple-clean/layouts/events/single.html` — individual event (hybrid YAML + markdown)
- `themes/simple-clean/layouts/_default/faq.html` — FAQ page with search
- `themes/simple-clean/layouts/partials/` — reusable components: `event-card.html`, `event-status.html`, `registration-button.html`, `faq-item.html`

### Styling

CSS is in `themes/simple-clean/assets/css/main.css` (processed by Hugo's asset pipeline). Brand colors and spacing are defined as CSS custom properties in `:root`. Component-specific styles are in `assets/css/components/`.

### Hugo Data Patterns Used in Templates

```hugo
{{ $events := .Site.Data.events.events }}
{{ $upcoming := where $events "date" "ge" (now.Format "2006-01-02") }}
{{ $event := index (where $events "id" $eventId) 0 }}
```

Past vs. upcoming is determined by comparing `$event.date` (string `YYYY-MM-DD`) against `now.Format "2006-01-02"`.
