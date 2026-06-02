# Email Development – Interview Q&A

## 📌 BASIC

### 1. What is email development?

**Answer:** Creating HTML emails for email marketing, notifications, transactional messages. Different from web development. Limited CSS support, inline styles required. Must work across email clients (Gmail, Outlook, Apple).

### 2. What are common email clients?

**Answer:** Web-based: Gmail, Yahoo, Outlook.com. Desktop: Outlook, Apple Mail, Thunderbird. Mobile: Gmail app, Apple Mail, Samsung Mail. Each has different CSS support. Testing required.

### 3. What is the difference between email HTML and web HTML?

**Answer:** Emails use tables for layout (not divs). Inline CSS only (style attribute). Limited CSS support (no flexbox, grid). No JavaScript. Must be self-contained. Image blocking common, use alt text.

### 4. Why use tables for email layout?

**Answer:** Better email client support. Divs and CSS floats unreliable. Tables predictable, widely supported. Standard practice despite semantic HTML concerns. Email-specific requirement.

### 5. What are email templates?

**Answer:** Pre-built HTML structure for emails. Contains header, body, footer sections. Responsive design for mobile. Reusable for multiple campaigns. MJML, Cerberus frameworks provide templates.

### 6. What is inline CSS?

**Answer:** Styles applied directly in HTML tags. `<td style="color: red;">`. Required for email. Most reliable across clients. Alternative to external/internal stylesheets (often stripped).

### 7. Why is inline CSS important for emails?

**Answer:** External stylesheets often stripped by email clients. Internal `<style>` tags sometimes removed. Inline styles most reliable. Required for mail client compatibility. Best practice for email.

### 8. What is email responsiveness?

**Answer:** Emails adapt to different screen sizes. Mobile-first design. Media queries limited support but helpful. Fallback layouts for non-supporting clients. Critical for mobile users (60%+ of opens).

### 9. What is mobile-first email design?

**Answer:** Design for mobile first. Single column layout. Large text. Thumb-friendly buttons. Desktop version enhanced (multi-column). Improved experience for mobile users.

### 10. What is alt text in emails?

**Answer:** Description for images. Many clients block images by default. Alt text shows instead. Improves accessibility. Essential for images carrying message content.

### 11. What is call-to-action (CTA)?

**Answer:** Interactive button/link encouraging user action. Color, size, contrast important. Should be obvious, clickable. Examples: "Shop Now", "Confirm Order", "Read More". Higher conversion if effective.

### 12. What is email authentication?

**Answer:** SPF, DKIM, DMARC protocols. Prove email legitimacy. Prevent spoofing/phishing. Required for good deliverability. Configured via DNS records. Improves inbox placement.

---

## 📌 INTERMEDIATE

### 1. What is MJML framework?

**Answer:** Markup Language for Email. Simplifies email HTML creation. Abstracts complexity of responsive tables. Compiles to HTML. Built-in components: navbar, hero, button. Faster development.

### 2. What is Cerberus framework?

**Answer:** Responsive email framework. CSS for common patterns. Mobile-responsive templates. Starts with solid foundation. More manual than MJML. Good for custom designs.

### 3. What is email client testing?

**Answer:** Test emails across clients before sending. Services: Litmus, Email on Acid. Test rendering, links, responsiveness. Catch issues early. Many clients behave differently.

### 4. What is preheader text?

**Answer:** Small text shown in inbox preview before email opens. First 40-50 characters important. Should add value, entice opens. Example: "10% off ends tonight" instead of "View in browser".

### 5. What are email segments?

**Answer:** Dividing email list by characteristics. Demographics, behavior, preferences. Send targeted content. Higher engagement than batch sends. Improves conversion.

### 6. What is A/B testing in emails?

**Answer:** Test two versions. Change subject line, CTA text, color, layout. Measure performance. Data-driven improvement. Essential for optimization. 10-20% improvement common.

### 7. What is send time optimization?

**Answer:** Send emails when user most likely to open. Analyze open times. Send at optimal times per user. Improves open rates. Reduces unsubscribes. Advanced segmentation.

### 8. What is email personalization?

**Answer:** Include user data in email. Name, location, purchase history. {{firstName}} template tags. Higher engagement rates. More relevant content improves conversions.

### 9. What is email animation?

**Answer:** Moving elements in email. Limited support (Outlook doesn't support). Use static fallback. Animated GIFs work better. AMP for email enables interactivity.

### 10. What is dark mode in emails?

**Answer:** Email clients applying dark theme. Text may become unreadable if not prepared. Test backgrounds, text colors. Support dark mode version. Growing user preference.

### 11. What is CSS media queries in email?

**Answer:** `@media` queries in style tags. Limited support (Gmail doesn't support). Works in most clients. Media query for mobile adjustments. Fallback for non-supporting clients.

### 12. What is CSS resets for email?

**Answer:** Remove email client default styles. Reset margins, padding, cell padding/spacing. Ensure consistent rendering. Necessary for predictable layouts. Standard practice.

### 13. What is VML (Vector Markup Language)?

**Answer:** Older Microsoft format for shapes. Outlook uses VML for rounded corners, gradients. Required for Outlook support. Complex, rarely used in modern emails. Consider Outlook fallbacks.

### 14. Real-life (Indian e-commerce): Design transactional order email?

**Answer:** Confirm order received. Show order details (items, total). Tracking link. Support contact info. Responsive layout for mobile. Brand consistency. Clear CTA (track order).

### 15. Real-life: Create email marketing campaign template?

**Answer:** Hero image, headline, body text, CTA button. Multi-section newsletter. Unsubscribe footer. Preheader text. Mobile responsive. Trackable links. Brand guidelines compliance.

---

## 📌 ADVANCED

**Q:** Explain email rendering challenges?
**A:** Email clients render differently than browsers. No standardized rendering engine. CSS support varies wildly. Images may be blocked. JavaScript not supported. VML for Outlook. Must test thoroughly.

**Q:** What is MJML component hierarchy?
**A:** Structure: `mj-container` → `mj-section` → `mj-column` → `mj-text`/`mj-image`. Components compile to responsive HTML tables. Attributes control responsive behavior, styling.

**Q:** How do you handle image blocking?
**A:** Use alt text for all images. Important message text shouldn't rely on images. Use CSS for backgrounds if possible. Testing: send to Gmail with images disabled.

**Q:** What is AMP for Email?
**A:** Dynamic, interactive emails. Updates without opening multiple times. Only supported by Gmail, Yahoo, Mail.ru. Progressive enhancement. Regular HTML fallback for unsupported clients.

**Q:** How do you optimize email delivery?
**A:** Clean list (remove bounces). SPF/DKIM/DMARC authentication. Monitor bounce rates. Honor unsubscribes. Send from recognizable address. Test spam filters. Avoid spam words.

**Q:** What is bounce rate and types?
**A:** Hard bounce: permanent delivery failure (invalid address). Soft bounce: temporary (mailbox full). Remove hard bounces. Retry soft bounces. Monitor bounces for list health. High bounces harm sender reputation.

**Q:** What is unsubscribe rate?
**A:** Percentage of recipients unsubscribing. Measure email relevance. High rate indicates poor segmentation/targeting. Legal requirement: CAN-SPAM, GDPR. One-click unsubscribe important.

**Q:** How do you implement footer links in email?
**A:** Unsubscribe link required. Privacy policy link. Company info/address. Social media links. Preference center link. All trackable, compliant. Example: "You're receiving this because you subscribed to our newsletter."

**Q:** What is email frequency capping?
**A:** Limit emails to same person. Prevents fatigue, unsubscribes. User preferences for frequency. Balance engagement with relevance. Too many: unsubscribe. Too few: forgotten.

**Q:** How do you test email accessibility?
**A:** Screen reader testing (NVDA, JAWS). Check semantic HTML. Alternative text for images. Color contrast. Font sizes readable. Semantic heading hierarchy. ARIA labels if needed.

**Q:** Real-life (Indian SaaS): Create onboarding email sequence?
**A:** Email 1: Welcome, quick tips. Email 2: Feature highlight (3 days later). Email 3: Success story (7 days). Email 4: Support info (14 days). Timed sequence, progressive information, build relationship.

**Q:** Real-life: Implement abandoned cart email?
**A:** Trigger: item added to cart, 1 hour no purchase. Show item image, price. CTA: "Complete Purchase". Single email effective. A/B test discount offer. Track conversion rate.

**Q:** Real-life: Troubleshoot poor email deliverability?
**A:** Check SPF/DKIM/DMARC records. Monitor bounce rates. Review bounce reasons. Verify email list quality. Test spam score. Check sender reputation. Avoid common spam triggers. Monitor feedback loops.

**Q:** Calculation: Email campaign to 100,000 subscribers. 20% open rate = 20,000 opens. 5% click rate = 1,000 clicks. 2% conversion rate = 20 sales. ROI: 20 × $50 (avg) = $1,000 revenue from 100K emails (~$0.01 per email cost = $1,000 cost, but $1,000 revenue, depending on platform).

**Q:** Calculation: List growth: 5,000 existing + 500 new per month (10% growth) - 250 unsubscribes (5% monthly churn) = 5,250 net growth. In 12 months: 5,000 × 1.05^12 = ~11,000 (assuming 5% net monthly growth). Importance of list building and churn reduction.

---

## 📋 Quick Reference

| Framework         | Purpose                    |
| ----------------- | -------------------------- |
| MJML              | Simplify email development |
| Cerberus          | Responsive templates       |
| Foundation Emails | Professional emails        |
| Stripo            | Visual builder             |

| Protocol | Purpose                |
| -------- | ---------------------- |
| SPF      | Sender verification    |
| DKIM     | Message authentication |
| DMARC    | Authentication policy  |

| Testing        | Service                |
| -------------- | ---------------------- |
| Client Testing | Litmus, Email on Acid  |
| Spam Check     | MXToolbox, Return Path |
| Preview        | Dyspatch, Stripo       |

| Metric           | Goal                  |
| ---------------- | --------------------- |
| Open Rate        | 15-25% (industry avg) |
| Click Rate       | 2-5% (industry avg)   |
| Conversion Rate  | 0.5-2% (industry avg) |
| Bounce Rate      | <2% (health)          |
| Unsubscribe Rate | <0.5% (health)        |
