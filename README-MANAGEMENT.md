# TCTRuns Website Management Guide

A comprehensive guide for non-technical website managers to update race events, FAQs, and content on the TCTRuns website.

## 🎯 **Quick Start**

This website is designed to be easy to manage without technical knowledge. Most content updates involve editing simple text files with clear instructions.

### **What You Can Manage:**

- ✅ Race events (dates, details, registration)
- ✅ Frequently Asked Questions
- ✅ Event status (open/closed/coming soon)
- ✅ Pricing information
- ✅ Event descriptions and details

### **What's Automatic:**

- ✅ Event sorting by date
- ✅ Past vs. upcoming event organization
- ✅ Registration status displays
- ✅ Mobile-responsive design
- ✅ Search functionality

## 📅 **Managing Race Events**

### **Adding a New Event**

1. Open the file: `data/events.yml`
2. Copy the template below and paste it at the end of the events list
3. Update all the details for your new event
4. Save the file

#### **Event Template:**

```yaml
- name: "Your Race Name Here"
  date: "2026-MM-DD" # Use YYYY-MM-DD format
  time: "07:00 AM"
  location: "Race Location"
  distance: "5K, 10K, Half Marathon" # List all available distances
  registration_url: "https://your-registration-link.com"
  registration_status: "open" # Options: open, closed, coming-soon
  early_bird_price: "$25"
  regular_price: "$35"
  description: "Brief description of your event that will appear on the website"
  course_map_url: "https://link-to-course-map.pdf"
  results_url: "" # Leave empty until after race
  photos_url: "" # Leave empty until after race
  awards: "Description of awards given"
  packet_pickup: "When and where participants can pick up packets"
  parking: "Parking information and instructions"
  contact_email: "youremail@tctruns.com"
  featured: true # Set to true for homepage spotlight, false for normal listing
  sponsors: ["Sponsor 1", "Sponsor 2", "Sponsor 3"]
```

### **Field Explanations**

| Field                 | Required    | Description                           | Example                                   |
| --------------------- | ----------- | ------------------------------------- | ----------------------------------------- |
| `name`                | ✅ Required | Event name as it appears on website   | "Spring 5K Challenge"                     |
| `date`                | ✅ Required | Event date in YYYY-MM-DD format       | "2026-04-15"                              |
| `time`                | ✅ Required | Race start time                       | "07:00 AM"                                |
| `location`            | ✅ Required | Where the race takes place            | "Riverside Park, Downtown"                |
| `distance`            | ✅ Required | Available race distances              | "5K" or "5K, 10K, Half Marathon"          |
| `registration_url`    | Optional    | Link to registration page             | "https://register.tctruns.com/spring-5k"  |
| `registration_status` | ✅ Required | Current registration status           | "open", "closed", or "coming-soon"        |
| `early_bird_price`    | Optional    | Early registration price              | "$25"                                     |
| `regular_price`       | ✅ Required | Regular registration price            | "$35"                                     |
| `description`         | ✅ Required | Event description (2-3 sentences)     | "Join us for our..."                      |
| `course_map_url`      | Optional    | Link to course map PDF                | "https://tctruns.com/maps/spring-5k.pdf"  |
| `results_url`         | Optional    | Link to race results (add after race) | "https://tctruns.com/results/spring-2026" |
| `photos_url`          | Optional    | Link to race photos (add after race)  | "https://tctruns.com/photos/spring-2026"  |
| `awards`              | Optional    | Description of awards                 | "Overall winners, age group awards"       |
| `packet_pickup`       | Optional    | Packet pickup information             | "Friday 5-7 PM, Race day 6:30-7:45 AM"    |
| `parking`             | Optional    | Parking instructions                  | "Free parking at venue"                   |
| `contact_email`       | ✅ Required | Contact email for event               | "spring5k@tctruns.com"                    |
| `featured`            | Optional    | Show on homepage?                     | true or false                             |
| `sponsors`            | Optional    | List of event sponsors                | ["Sponsor 1", "Sponsor 2"]                |

### **Registration Status Options**

- **`open`**: Registration is currently available
- **`closed`**: Registration has closed
- **`coming-soon`**: Registration will open soon

### **Important Date Format**

Always use `YYYY-MM-DD` format for dates:

- ✅ Correct: `"2026-04-15"`
- ❌ Wrong: `"April 15, 2026"` or `"4/15/2026"`

### **Updating Existing Events**

1. Find the event in `data/events.yml`
2. Update the specific field you need to change
3. Save the file

**Common Updates:**

- Change `registration_status` from `"coming-soon"` to `"open"`
- Add `registration_url` when registration opens
- Add `results_url` and `photos_url` after the race
- Change `registration_status` to `"closed"` when registration fills up

### **After Race Completion**

1. Change `registration_status` to `"closed"`
2. Add `results_url` if results are available
3. Add `photos_url` if photos are available
4. Set `featured` to `false` (optional)

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

### **Opening Registration for a New Event**

1. Update the event's `registration_status` to `"open"`
2. Add the `registration_url` with the actual registration link
3. Double-check the `date`, `time`, and `location` are correct

### **Closing Registration**

1. Change `registration_status` to `"closed"`
2. Optionally update the event description to mention registration is closed

### **Featuring an Event on Homepage**

1. Set `featured: true` for the event
2. Limit to 2-3 featured events at most for best display

### **Adding Race Results**

1. Add the `results_url` with link to results page
2. Add the `photos_url` with link to photo gallery
3. Update FAQ if needed with new result information

## ⚠️ **Important Guidelines**

### **File Format Rules**

1. **Indentation Matters**: Use 2 spaces for each level of indentation
2. **Quotes**: Always put text in quotes (`"like this"`)
3. **Lists**: Use square brackets and quotes (`["item 1", "item 2"]`)
4. **True/False**: Use lowercase (`true`, not `True`)
5. **Backup**: Always keep a backup copy before making changes

### **Testing Changes**

After making changes:

1. Save the file
2. Check the website preview
3. Verify all events display correctly
4. Test registration links work
5. Check FAQ search functionality

### **Common Mistakes to Avoid**

❌ **Don't:**

- Remove the dashes (`-`) at the start of new events/FAQs
- Change the indentation
- Use tabs instead of spaces
- Forget quotes around text
- Use wrong date format

✅ **Do:**

- Keep consistent formatting
- Test registration links before publishing
- Update contact emails for each event
- Keep descriptions concise but informative
- Backup files before major changes

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

### **File Locations**

- Events: `data/events.yml`
- FAQs: `data/faqs.yml`

### **Date Format**

- Always use: `"YYYY-MM-DD"`
- Example: `"2026-12-25"`

### **Registration Status Options**

- `"open"` - Currently accepting registrations
- `"closed"` - Registration closed
- `"coming-soon"` - Registration opens later

### **Boolean Values**

- Featured event: `featured: true`
- Not featured: `featured: false`

### **Sample Complete Event**

```yaml
- name: "Summer 5K Fun Run"
  date: "2026-07-04"
  time: "08:00 AM"
  location: "City Park"
  distance: "5K"
  registration_url: "https://register.tctruns.com/summer-5k"
  registration_status: "open"
  early_bird_price: "$20"
  regular_price: "$30"
  description: "Join us for a patriotic 5K run through beautiful City Park with post-race BBQ!"
  course_map_url: "https://tctruns.com/maps/summer-5k.pdf"
  results_url: ""
  photos_url: ""
  awards: "Overall male/female winners, kids fun run medals"
  packet_pickup: "July 3rd 5-7 PM at Sports Store, Race day 7:00-7:45 AM"
  parking: "Free parking at City Park, overflow at Community Center"
  contact_email: "summer5k@tctruns.com"
  featured: true
  sponsors: ["City Sports", "Healthy Living", "Local Bank"]
```

---

_Last updated: March 2026_
_For website issues, contact webmaster@tctruns.com_
