# Grant Heimer Personal Website - Complete Project Plan

## Project Overview
A modern, dynamic personal website featuring an interactive dual-strand timeline showcasing Grant's educational journey, career progression, and geographic locations from 2009 to present.

---

## Design Philosophy
- **Industry Context:** Tech with creative elements (finance background, tech career)
- **Target Audience:** Potential employers, business partners, general audience interested in Grant's story
- **Desired Feel:** Innovative, bold, unique, classic (not minimalist)
- **Visual Style:** Modern, tech-forward, glassmorphic design elements

---

## Color Scheme

### Primary Palette
- **Deep Navy/Charcoal Background:** #0a0f1e to #1a1f2e
- **Electric Cyan:** #00d9ff (Work/Education strand primary)
- **Vibrant Orange:** #ff6b35 (Cities strand primary)
- **Cool Teal:** #00b4a6 (Year markers and accents)
- **White/Off-White:** #f5f5f5 (Text content)

### Color Application
- Work/College icons: Electric Cyan with orange highlights on hover
- Cities icons: Vibrant Orange with cyan highlights on hover
- Year markers: Subtle teal
- Background: Deep navy with subtle teal/cyan gradient shifts (parallax effect)
- Text: White for titles, light gray for body text in modals
- Active/centered items: Brightest, most saturated versions

### Excluded Colors
- No purple, pink, or yellow

---

## Website Structure

### Navigation Bar
- **Fixed top bar** with transparency and blur effect
- **Left side:** "Grant Heimer" logo/name
- **Right side:** "Home" | "About" links
- **Home page:** Timeline (main page)
- **About page:** Simple page with bio paragraph and contact information

### Hero Section (Home/Timeline Page)
- Full viewport height
- Large animated gradient text: "Grant Heimer"
- Subtle animated background with parallax elements
- Scroll indicator pointing down to timeline

### Timeline Section (Main Content)

#### Layout Structure
- Two vertical strands touching each other, centered down the middle of the screen
- **Left strand:** Cities (orange location pins 📍)
- **Right strand:** Education/Work (cyan graduation caps 🎓 and briefcases 💼)
- Year markers positioned ABOVE both strands, centered
- Timeline runs from 2009 to 2026, ending with "To be continued..."

#### Year Markers
- Years: 2009, 2010, 2011... 2024, 2025, 2026
- Faded teal color (#00b4a6)
- Subtle, non-distracting appearance
- Evenly spaced vertically
- Final marker: "To be continued..." after 2026

#### Icon Positioning
- **Cities (left strand):** Icon on strand, title text to the LEFT of icon
- **Education/Work (right strand):** Icon on strand, title text to the RIGHT of icon

#### Click Indicators
- Small "+" icon overlaid on bottom-right of each timeline icon
- Subtle pulse animation
- Becomes more prominent on hover
- Icon glows slightly on hover
- Clearly indicates interactivity

---

## Timeline Content

### Cities Timeline (Left Strand - Orange 📍)

1. **Dallas, TX** (mid 2009 - mid 2010)
2. **Austin, TX** (mid 2010 - mid 2014)
3. **Dallas, TX** (mid 2014 - mid 2016)
4. **Denver, CO** (mid 2016 - end 2018)
5. **Charleston, SC** (2019)
6. **Austin, TX** (2020 - present)

### Education/Work Timeline (Right Strand - Cyan 🎓/💼)

#### 2009
- 🎓 **HS Graduation** (mid 2009)
- 🎓 **SMU - BBA Scholars** (mid 2009 - mid 2010)
  - Business honors program

#### 2010
- 💼 **City of Dallas Mayor's Office - Analyst Intern** (Jan - May 2010)
- 💼 **Hodges Capital Management - Analyst Intern** (summer 2010)
- 🎓 **The University of Texas at Austin** (mid 2010 - mid 2014)
  - Finance Major, Marketing Minor
  - **Modal includes:** Co-founded and led the Longhorn Entrepreneurship Agency, the largest student organization devoted to entrepreneurship at the university

#### 2012
- 🎓 **Australian National University - Study Abroad** (first half 2012)
  - Canberra, Australia
- 💼 **Owner Resource Group - Analyst Intern** (mid 2012 - May 2013)
  - Private equity group

#### 2013
- 💼 **AMD - Intern** (summer 2013)

#### 2014
- 💼 **Allegro Development - Software Implementation** (mid 2014 - end 2016)

#### 2017
- 💼 **Failed Startup Attempt** (first half 2017)
- 💼 **GHX - Sales** (mid 2017 - mid 2021)
  - **Modal includes:** Top seller of Market Intelligence vs. all reps during tenure

#### 2021
- 💼 **Cake - Director of Business Development** (mid 2021 - mid 2022)
  - **Modal includes:** 10-person venture-backed startup

#### 2022
- 💼 **IMO Health - Sales** (mid 2022 - present)
  - **Modal includes:** Top seller in 2024

---

## Interactive Elements

### Scroll Animations

#### 1. Scale on Center Effect
- Icons and titles at viewport center: 100% scale (full size)
- Icons and titles at viewport edges: 60% scale
- Smooth easing transitions as user scrolls
- Both icon and associated title scale proportionally together

#### 2. Parallax Background Effect
- Subtle floating geometric shapes (circles, thin lines)
- Faded teal gradient waves moving at 0.3x scroll speed
- Barely visible year numbers in background at 0.5x speed
- Creates depth without distraction
- All elements in muted teal/dark cyan tones

### Modal Popup System

#### Trigger
- Click on any timeline icon OR its associated title

#### Animation
- Smooth fade-in effect
- Scale animation (grows from center)

#### Design
- Centered on screen
- Dark navy background card (#0a0f1e)
- Glowing border:
  - Cyan glow for work/education entries
  - Orange glow for city entries
- Semi-transparent backdrop with blur effect

#### Content Structure
- **Top bar:** Entry title in large text
- **Content area:** Free-text description with dates, achievements, and personal stories
- **X button:** Top-right corner, white with hover effect

#### Close Actions
- Click X button
- Click outside modal (on backdrop)

---

## Icon Design System

### Icon Types
- **📍 Location Pin:** Cities (orange #ff6b35)
- **🎓 Graduation Cap:** Education entries (cyan #00d9ff)
- **💼 Briefcase:** Work/internship entries (cyan #00d9ff)

### Visual Style
- Glassmorphic effect (frosted glass appearance)
- Semi-transparent backgrounds
- Subtle inner glow
- Thin stroke outline
- Modern, tech-forward aesthetic

### Click Indicator
- Small white "+" symbol
- Positioned bottom-right of each icon
- Subtle pulse animation (1.5s cycle)
- Increases in prominence on hover

---

## About Page

### Layout
- Same color scheme and background as timeline page
- Centered content container (max-width: 800px)
- Consistent navigation bar

### Content Structure
1. **Heading:** "About Grant"
2. **Biography paragraph:** [Placeholder for Grant's story and background]
3. **Contact Section:**
   - Email: email@example.com
   - LinkedIn: linkedin.com/in/yourprofile
   - Instagram: @yourhandle
   - Twitter: @yourhandle

### Design
- Clean, readable typography
- Professional appearance
- Simple, focused layout

---

## Footer

### Content
- Centered text: "© 2025 Grant Heimer. All rights reserved."

### Legal Note
- Copyright symbol (©) can be used without formal registration
- By default, Grant owns copyright to his creative work (the website)
- The © symbol makes ownership explicit

---

## Responsive Design

### Desktop (1200px+)
- Full dual-strand centered layout
- Titles positioned on opposite sides of respective strands
- Optimal spacing and readability

### Tablet (768px - 1199px)
- Strands positioned slightly closer together
- Smaller title text
- Maintained dual-strand layout

### Mobile (< 768px)
- Vertical single-strand layout OR
- Alternating left/right layout OR
- Stacked layout
- Touch-optimized click targets
- Adjusted text sizes for readability

---

## Technical Specifications

### Technology Stack
- **Single HTML file** with embedded CSS and JavaScript
- No external dependencies
- Self-contained and portable
- Fast loading times

### Hosting Platform
- **Vercel** (recommended)
- Free tier sufficient
- Automatic HTTPS/SSL
- Global CDN
- Zero configuration deployment
- Custom domain support

### Version Control
- **GitHub** repository
- Git for version control
- Automatic deployment from GitHub to Vercel

### Domain
- Existing URL to be connected to Vercel
- DNS configuration required

---

## Security & Performance

### Built-in Features (via Vercel)
- ✅ HTTPS/SSL (automatic, free, secure)
- ✅ DDoS protection (built-in)
- ✅ Global CDN (fast worldwide)
- ✅ Automatic compression (optimized delivery)
- ✅ Edge caching (lightning fast load times)

### Performance Optimizations
- Single file architecture (minimal HTTP requests)
- Embedded styles and scripts (no external dependencies)
- Optimized animations (GPU-accelerated where possible)
- Lazy loading considerations for modals

---

## Development Workflow

### Initial Setup
1. Generate HTML file
2. Create new folder on local computer
3. Initialize Git repository
4. Create GitHub repository
5. Push code to GitHub
6. Connect GitHub repository to Vercel
7. Configure custom domain

### Making Edits (with Cursor)
1. Open project in Cursor
2. Make desired changes
3. Git commit changes
4. Push to GitHub
5. Vercel automatically detects and deploys
6. Changes live in ~30 seconds

---

## Design Principles Applied

### Visual Hierarchy
- Center-focused design draws eye to current timeline position
- Scaling effect emphasizes relevant content
- Color coding differentiates categories

### User Experience
- Clear click indicators prevent confusion
- Smooth animations enhance, not distract
- Intuitive navigation
- Accessible on all devices

### Brand Identity
- Professional yet creative
- Tech-forward aesthetic
- Bold color choices reflect personality
- Unique dual-strand concept tells comprehensive story

### Storytelling
- Chronological progression easy to follow
- Geographic context adds dimension
- Expandable details allow depth without clutter
- "To be continued..." invites future engagement

---

## Project Goals

### Primary Objectives
1. **Impress potential employers and business partners**
   - Professional presentation
   - Clear career progression
   - Demonstrated achievements

2. **Enable storytelling**
   - Comprehensive view of journey
   - Personal details in modals
   - Geographic context adds richness

3. **Showcase technical capability**
   - Modern web design
   - Interactive elements
   - Attention to detail

### Success Metrics
- Visitor engagement (time on page)
- Modal interactions (clicks on timeline entries)
- Professional inquiries generated
- Positive feedback from viewers

---

## Future Enhancement Possibilities

### Potential Additions
- Analytics integration (Google Analytics)
- Blog section
- Project portfolio showcase
- Testimonials/recommendations
- Downloadable resume
- Dark/light mode toggle
- Additional animation effects
- Video or image galleries in modals

### Scalability Considerations
- Easy to add new timeline entries
- Modal content fully customizable
- Color scheme variables for quick theme changes
- Modular code structure for feature additions

---

## Project Timeline

### Phase 1: Development
- Code generation
- Initial testing
- Content population

### Phase 2: Deployment
- GitHub repository setup
- Vercel connection
- Domain configuration
- SSL certificate verification

### Phase 3: Refinement
- Content refinement in modals
- About page bio writing
- Contact information updates
- Final testing across devices

### Phase 4: Launch
- Go live with custom domain
- Share with network
- Monitor performance
- Gather feedback

---

## Contact & Questions

For any questions or clarifications during development, refer back to this document for the agreed-upon specifications.

**Project Owner:** Grant Heimer  
**Development Start Date:** December 2025  
**Target Completion:** TBD

---

*End of Project Plan Document*