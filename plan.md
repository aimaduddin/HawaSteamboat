# Implementation Plan
## Hawa Steamboat House – WhatsApp Booking Sales Page

---

## Tech Stack

- **HTML5** – Semantic structure
- **TailwindCSS** – Utility-first styling (CDN)
- **AlpineJS** – Lightweight reactivity (CDN)

---

## File Structure

```
/
├── index.html          # Single page application
├── plan.md             # This file
└── assets/
    └── images/         # Food photos, hero background
```

---

## Implementation Phases

### Phase 1: Project Setup

- [ ] Create `index.html` with HTML5 boilerplate
- [ ] Add TailwindCSS CDN
- [ ] Add AlpineJS CDN
- [ ] Configure Tailwind for custom colors (warm tones for F&B)
- [ ] Set up meta tags for SEO and social sharing

---

### Phase 2: Hero Section

- [ ] Full-screen background with food image
- [ ] Dark overlay for text readability
- [ ] Headline: Bold, benefit-driven copy
- [ ] Subheadline: Positioning statement
- [ ] Primary CTA button → scrolls to booking form
- [ ] Mobile responsive (vh units, proper scaling)

**Copy Draft:**
- Headline: "Steamboat & BBQ Paling Best di Kuching"
- Sub: "Daging segar, pilihan banyak, sesuai untuk family & kawan-kawan"
- CTA: "Book Your Table Now"

---

### Phase 3: Why People Love Hawa

- [ ] 4-column grid (desktop) → 2x2 (tablet) → stacked (mobile)
- [ ] Icon + short text per block
- [ ] Blocks:
  1. Fresh Marinated Meat
  2. 50+ Menu Choices
  3. Family-Friendly Space
  4. Comfortable AC Dining

---

### Phase 4: Food Gallery

- [ ] Responsive image grid
- [ ] 3 columns desktop, 2 columns mobile
- [ ] Categories:
  - Beef slices
  - Lamb
  - Chicken
  - Seafood platter
  - Soup bases
  - Vegetables & sides
- [ ] Lazy loading for performance
- [ ] Optional: Lightbox on click

---

### Phase 5: Social Proof

- [ ] Star rating display (5 stars visual)
- [ ] 2-3 customer testimonials (cards)
- [ ] Trust badge: "500+ families dine with us weekly"
- [ ] Optional: Google review snippet

**Testimonial Template:**
```
"[Quote]"
– [Name], [Location]
```

---

### Phase 6: Booking Form

- [ ] AlpineJS x-data initialization
- [ ] Form fields:
  - Name (text, required)
  - Date (date picker, required)
  - Time (select dropdown, required)
  - Pax (number, required, min 1)
  - Notes (textarea, optional)
- [ ] Real-time validation with error messages
- [ ] Form contained within one mobile viewport

**Time Options:**
- 5:00 PM
- 5:30 PM
- 6:00 PM
- 6:30 PM
- 7:00 PM
- 7:30 PM
- 8:00 PM
- 8:30 PM
- 9:00 PM

---

### Phase 7: WhatsApp Integration

- [ ] Computed property for message generation
- [ ] URL encoding for special characters
- [ ] Dynamic link construction
- [ ] Button opens `wa.me` link

**AlpineJS Logic:**
```javascript
x-data="{
  name: '',
  date: '',
  time: '',
  pax: '',
  notes: '',
  
  get isValid() {
    return this.name && this.date && this.time && this.pax
  },
  
  get whatsappMessage() {
    return `Hi Hawa Steamboat House,
I want to book a table.

Name: ${this.name}
Date: ${this.date}
Time: ${this.time}
Guests: ${this.pax}
Notes: ${this.notes || 'None'}`
  },
  
  get whatsappLink() {
    return `https://wa.me/60XXXXXXXXX?text=${encodeURIComponent(this.whatsappMessage)}`
  }
}"
```

---

### Phase 8: FAQ Section

- [ ] Accordion component (AlpineJS toggle)
- [ ] 5 FAQs:
  1. What are the opening hours?
  2. Is parking available?
  3. Can I book for large groups?
  4. Is the food halal?
  5. What time is peak hour?

---

### Phase 9: Footer

- [ ] Restaurant address
- [ ] Google Maps embed or link
- [ ] Instagram link (icon)
- [ ] WhatsApp button (secondary CTA)
- [ ] Copyright notice

---

### Phase 10: Sticky WhatsApp Bar

- [ ] Fixed bottom bar on mobile
- [ ] Shows after scroll (past hero)
- [ ] WhatsApp icon + "Book Now" text
- [ ] High contrast green (#25D366)

---

### Phase 11: Polish & Optimization

- [ ] Test on mobile devices (iOS Safari, Android Chrome)
- [ ] Verify WhatsApp deep link works on both platforms
- [ ] Image optimization (WebP format, compressed)
- [ ] Lighthouse audit (Performance, SEO, Accessibility)
- [ ] Add favicon
- [ ] Test form validation edge cases

---

## Design Tokens (Tailwind Config)

```javascript
colors: {
  primary: '#E53935',      // Hot red (appetite trigger)
  secondary: '#FF8F00',    // Warm orange
  dark: '#1A1A1A',         // Background dark
  light: '#FAFAFA',        // Light text bg
  whatsapp: '#25D366',     // WhatsApp green
}

fontFamily: {
  display: ['Poppins', 'sans-serif'],
  body: ['Inter', 'sans-serif'],
}
```

---

## Assets Needed

| Asset | Purpose | Size |
|-------|---------|------|
| hero-bg.jpg | Hero background | 1920x1080 |
| beef.jpg | Gallery | 600x400 |
| lamb.jpg | Gallery | 600x400 |
| chicken.jpg | Gallery | 600x400 |
| seafood.jpg | Gallery | 600x400 |
| soup.jpg | Gallery | 600x400 |
| logo.png | Header/Footer | 200x80 |
| favicon.ico | Browser tab | 32x32 |

---

## WhatsApp Configuration

- **Phone Number:** `60XXXXXXXXX` (to be provided)
- **Business Hours:** 5:00 PM – 10:00 PM daily
- **Response expectation:** Within 30 minutes during operating hours

---

## Testing Checklist

- [ ] Hero displays correctly on iPhone SE (smallest common screen)
- [ ] Form submits valid WhatsApp link
- [ ] All required fields show validation errors when empty
- [ ] WhatsApp opens correctly on iOS
- [ ] WhatsApp opens correctly on Android
- [ ] Images load within 3 seconds on 4G
- [ ] Sticky bar appears/disappears correctly
- [ ] FAQ accordions work
- [ ] All links work (Maps, Instagram, WhatsApp)

---

## Success Criteria

| Metric | Target |
|--------|--------|
| Page Load Time | < 3 seconds |
| Mobile Lighthouse Score | > 90 |
| WhatsApp Click Rate | Track via UTM |
| Form Completion | > 70% of starters |

---

## Out of Scope (Confirmed)

- ❌ Payment processing
- ❌ Online ordering system
- ❌ Table management backend
- ❌ Admin dashboard
- ❌ User accounts/login
- ❌ Multi-language support (Phase 1)

---

## Timeline Estimate

| Phase | Effort |
|-------|--------|
| Setup + Hero | 1 hour |
| Why Hawa + Gallery | 1 hour |
| Social Proof | 30 min |
| Booking Form + WhatsApp | 1.5 hours |
| FAQ + Footer | 45 min |
| Sticky Bar + Polish | 45 min |
| Testing | 1 hour |
| **Total** | **~6-7 hours** |

---

## Notes

- All copy should be reviewed for Malay/English mix appropriate for Kuching audience
- Phone number must be confirmed before deployment
- Images should feature actual restaurant food (not stock photos) for authenticity
- Consider A/B testing headline variations post-launch
