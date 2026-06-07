# User Personas

> **Status**: 📝 Draft
> **Last Updated**: 2026-06-06

Based on the Business Discovery analysis, My Trip My Titipan operates as a Travel-Based Social Commerce ecosystem. The success of the platform relies on balancing demand (Shoppers) with supply (Travelers) through verified trust mechanisms. 

The following personas represent the individual actors required to build this ecosystem.

---

## 1. Lifestyle Shopper (The Demand)

### Persona Overview
* **Persona Name**: Sarah "The Trend Seeker"
* **Persona Type**: Consumer / Buyer
* **Priority**: Primary Persona (MVP)
* **Age Range**: 18–35
* **Occupation**: Marketing Executive / College Student
* **Location**: Jakarta, Indonesia
* **Digital Behavior**: Highly active on Instagram and TikTok. Actively follows beauty influencers and lifestyle creators. Comfortable with e-wallets.
* **Discovery Behavior**: Usually discovers travelers through:
  - Instagram links
  - TikTok content
  - Community recommendations
  - Shared Trip links
  *(Since MVP does not have an internal feed).*

### Goals
* Securely purchase international or limited-edition products (e.g., Japanese skincare, Korean merchandise) that are unavailable locally. She often already knows exactly what she wants (has a screenshot or URL ready).
* Know exactly when the item will arrive and exactly how much it will cost upfront.

### Pain Points
* **The "Hit and Run" Fear:** Highly anxious about transferring money directly to a stranger's bank account.
* **Hidden Costs:** Frustrated by unexpected customs or shipping fees added after the purchase.
* **Communication Chaos:** Hates the back-and-forth negotiation on WhatsApp and the lack of tracking updates.

### Needs
* **Functional:** Escrow payment system, clear price breakdowns, real-time tracking, structured product request forms (to easily upload her screenshot/URL).
* **Trust:** Traveler verification badges on traveler profiles. *(Note: "Success Rates" are explicitly hidden during MVP to avoid showing "0 completed trips" in a new marketplace).*

### Success Criteria
* Product received successfully.
* Final cost matches quoted price.
* Transaction completed without fraud concerns.

---

## 2. Trusted Traveler (The Supply)

### Persona Overview
* **Persona Name**: Budi "The Route Specialist"
* **Persona Type**: Service Provider / Supplier
* **Priority**: Primary Persona (MVP Focus)
* **Age Range**: 25–40
* **Occupation**: Corporate Employee / Flight Attendant
* **Location**: Urban centers (frequent flyer to JP, KR, SG)
* **Digital Behavior**: Uses travel aggregator apps, navigates airports easily, posts aesthetic travel stories on Instagram. **Distribution:** Shares jastip offerings in 3-5 active WhatsApp/Telegram groups (alumni, hobbies, office Slack) to ensure he gets requests.
* **Note**: During MVP, travelers may include both frequent travelers and casual travelers who wish to offset travel expenses through occasional jastip opportunities.

### Goals
* Subsidize his expensive international travel costs by monetizing available luggage capacity during international trips.
* Manage jastip orders efficiently without letting the administrative burden ruin his actual vacation.

### Pain Points
* **Admin Overload:** Managing 50 different WhatsApp chats, matching bank transfer screenshots, and updating Excel spreadsheets is a nightmare.
* **Flaky Buyers:** Buyers who request an item but "ghost" him when he asks for the deposit, wasting his time.
* **Customs Uncertainty:** Unsure which products can be carried, how much can be declared, and how customs regulations affect profitability.

### Needs
* **Functional:** Trip Publisher to get a shareable link, structured quoting tools, centralized order management dashboard.
* **Trust:** Upfront Escrow funding so he *knows* the buyer is committed before he spends his own money abroad.

### Success Criteria
* Orders fulfilled successfully.
* No financial losses.
* Administrative workload reduced significantly.

---

## 3. Creator Traveler (The Amplifier)

### Persona Overview
* **Persona Name**: Rina "The Niche Expert"
* **Persona Type**: Content Creator & Commerce Curator
* **Priority**: Out of Scope for MVP (V2 Focus only - to protect engineering bandwidth)
* **Age Range**: 22–35
* **Occupation**: Full-time Content Creator (TikTok/Instagram)
* **Location**: Jakarta / Bali
* **Digital Behavior**: Lives on TikTok and Instagram. Creates highly engaging video reviews, unboxings, and store tours.

### Goals
* Monetize her engaged audience directly through commerce, rather than relying solely on unpredictable brand sponsorships.
* Provide a seamless, professional shopping experience for her followers.

### Pain Points
* **High Drop-off Rates:** Sending followers from a viral TikTok video to a messy WhatsApp link-in-bio results in massive conversion drop-offs.
* **Reputation Risk:** If an order gets messed up due to manual tracking errors, her public reputation is severely damaged.

### Needs
* **Functional:** Dedicated storefront tools, ability to link specific products directly from her content to a platform checkout.
* **Trust:** Leveraging the platform's Escrow and verification systems to instantly establish trust with new followers.

### Success Criteria
* Audience converts into transactions.
* Followers trust the recommendation.
* Commerce activity scales without manual coordination.

---

## Persona Prioritization

### MVP Priority

1. **Trusted Traveler**
2. **Lifestyle Shopper**

**Rationale:**
A travel-based marketplace requires active supply before demand can be fulfilled. Without active travelers publishing trips, shoppers cannot submit meaningful requests.
* **Strategic MVP Decision**: We are proceeding with **Option A (Traveler publishes trip → Shopper submits request)**. We are explicitly excluding "Orphaned Requests" (Shoppers requesting items without an assigned traveler) for the MVP to minimize matching complexity and ensure guaranteed fulfillment paths.

### Growth Stage

3. **Creator Traveler**

**Rationale:**
Creators act as demand amplifiers once the core transaction loop has been validated.
