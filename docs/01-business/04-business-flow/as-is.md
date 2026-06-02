# AS-IS Business Process Analysis

## 1. Executive Overview

The Indonesian "Jastip" (Jasa Titip / Personal Shopper) ecosystem currently operates as an informal, decentralized, and highly fragmented social commerce network. Driven by travel mobility, digital connectivity, and consumer demand for inaccessible or price-arbitraged foreign and local goods, individuals (Travelers/Jastipers) leverage their personal trips to purchase items on behalf of others (Customers/Shoppers). This grassroots economy relies heavily on legacy social media platforms and standard messaging apps for discovery, communication, and transaction coordination, creating a vibrant but unstructured marketplace that blends travel with commerce.

---

## 2. Ecosystem Overview

*   **Customers / Shoppers:** Individuals seeking specific products from destinations they cannot currently visit. They rely on social media discovery and personal networks to find reliable travelers willing to purchase on their behalf.
*   **Travelers / Jastipers:** Individuals traveling domestically or internationally who monetize their luggage space and time by acting as personal shoppers. They range from casual travelers doing it to subsidize trip costs, to professional jastipers doing it as a primary business.
*   **Content Creators:** Influencers and reviewers who showcase international trends, unique products, or travel destinations, inadvertently or intentionally driving demand for jastip services by raising awareness.
*   **Payment Providers:** Traditional banks and digital E-Wallets (like GoPay, OVO, Dana) that facilitate direct peer-to-peer transfers for deposits and final payments.
*   **Logistics Providers:** Third-party domestic couriers (JNE, SiCepat, Paxel, GoSend) used by Jastipers to deliver the purchased goods to the final Customer upon return.
*   **Social Media Platforms:** Instagram, TikTok, and Facebook serve as the primary storefronts, discovery engines, and community hubs where Jastipers promote open slots and Customers browse available trips.

These stakeholders interact through a fragmented web of disconnected tools. A Customer might discover a product on TikTok, find a Jastiper on Instagram, negotiate on WhatsApp, pay via Bank Transfer, and track delivery via a courier's standalone app.

---

## 3. Current Business Model

*   **How customers discover jastip services:** Customers typically find Jastipers through Instagram/TikTok searches (e.g., using hashtags like #jastipjapan, #jastipkorea), algorithmic recommendations, or word-of-mouth within closed WhatsApp/Telegram communities.
*   **How jastipers promote products:** Jastipers post "Open PO" (Pre-Order) announcements indicating their destination and travel dates. They post photos or videos of specific items (store displays, catalogues) on Instagram Stories/Feeds or TikTok, often taking live requests while at a physical store.
*   **How transactions occur:** Transactions are highly manual. Customers send direct messages containing screenshots of desired products. Prices are quoted individually, including the item cost, a jastip fee (service charge), and estimated shipping.
*   **How payments are processed:** Payments are processed via direct, un-escrowed peer-to-peer bank transfers. Typically, a 50% to 100% upfront deposit (DP) is required before the Jastiper purchases the item, with the remainder paid before final delivery.
*   **How deliveries are handled:** Upon returning from the trip, the Jastiper sorts, repacks, and dispatches the items using domestic logistics providers. Tracking numbers are manually shared via messaging apps.

---

## 4. Current Customer Journey (AS-IS)

1.  **Product Discovery:** The Customer discovers a desirable product unavailable locally or cheaper abroad through social media, influencers, or personal research.
2.  **Product Request:** The Customer actively searches for a Jastiper traveling to the required destination or spots an "Open PO" post. They send a Direct Message (DM) with a screenshot or description of the product.
3.  **Price Confirmation:** The Customer waits for the Jastiper to confirm availability, calculate the exchange rate, add the jastip service fee, and provide a total quote.
4.  **Payment:** The Customer transfers a Down Payment (DP) or full amount directly to the Jastiper's personal bank account and sends a screenshot of the transfer receipt as proof.
5.  **Purchase:** The Customer waits while the Jastiper executes the trip, potentially receiving updates or alternative options via chat if the original item is out of stock.
6.  **Shipping:** Once the Jastiper returns, the Customer pays any remaining balance plus local shipping fees.
7.  **Delivery:** The Customer receives a courier tracking number manually from the Jastiper and waits for the package to arrive.
8.  **Review:** The Customer might post a "thank you" story on Instagram tagging the Jastiper as informal social proof, though structured reviews are rare.

---

## 5. Current Jastiper Journey (AS-IS)

1.  **Trip Planning:** The Jastiper plans a trip and assesses available luggage capacity. They announce "Open PO" on their social media channels to attract requests.
2.  **Product Promotion:** Before and during the trip, the Jastiper visits stores, takes photos/videos of trending items, and posts them to social media to generate impulse requests.
3.  **Customer Communication:** The Jastiper manages an influx of DMs across multiple platforms (Instagram, WhatsApp), answering queries, confirming prices, and managing expectations.
4.  **Order Collection:** The Jastiper manually compiles orders, addresses, and payment statuses into informal tools like spreadsheets or phone notes.
5.  **Purchase Execution:** The Jastiper physically navigates stores, hunts for requested items, purchases them with personal funds (backed by Customer DPs), and coordinates real-time substitutions if necessary.
6.  **Delivery Coordination:** Upon returning, the Jastiper unpacks, sorts items by customer, packs them for domestic shipping, creates shipping labels manually, and drops them off at a courier.
7.  **Customer Follow-Up:** The Jastiper chases pending final payments, distributes tracking numbers, and handles any post-delivery complaints or issues.

---

## 6. Current Business Process Flow

| Step | Actor | Activity | Channel/Tool |
| :--- | :--- | :--- | :--- |
| 1 | Jastiper | Announces upcoming trip & opens Pre-Order (PO) | Instagram, TikTok, WhatsApp Status |
| 2 | Shopper | Discovers trip/products and sends request with images | Instagram DM, WhatsApp |
| 3 | Jastiper | Calculates cost, fee, and provides quote | WhatsApp, Line |
| 4 | Shopper | Agrees to quote and transfers Down Payment (DP) | Mobile Banking, E-Wallet |
| 5 | Shopper | Sends screenshot of transfer receipt | WhatsApp |
| 6 | Jastiper | Manually records order details and payment status | Excel, Google Sheets, Notes App |
| 7 | Jastiper | Travels, visits stores, and purchases items | Physical Stores |
| 8 | Jastiper | (Optional) Updates shopper on item status/alternatives | WhatsApp (Live Chat/Call) |
| 9 | Jastiper | Returns home, sorts, and repacks items | Physical Location |
| 10 | Jastiper | Calculates final local shipping cost & bills shopper | WhatsApp |
| 11 | Shopper | Transfers final payment & sends proof | Mobile Banking, E-Wallet |
| 12 | Jastiper | Dispatches package to logistics provider | JNE, SiCepat, GoSend |
| 13 | Jastiper | Manually shares tracking receipt | WhatsApp |
| 14 | Shopper | Receives goods and (optionally) provides social proof | Physical Location, Instagram Story |

---

## 7. Current Technology Landscape

*   **Instagram & TikTok:** Serve as the primary "storefront" and discovery engine. Used for broadcasting trips, showcasing products via Stories/Feeds/Live, and building social proof.
*   **WhatsApp & Telegram:** Act as the CRM and communication backbone. Used for 1-on-1 negotiations, customer service, sending receipts, and managing closed community groups.
*   **Bank Transfer (BCA, Mandiri, etc.):** The dominant method for financial transactions. Requires manual verification of receipts by the Jastiper.
*   **E-Wallet (GoPay, OVO, ShopeePay):** Used similarly to bank transfers, often for smaller transactions or domestic jastip.
*   **Logistics Services (JNE, SiCepat, Paxel):** Standalone applications or physical counters used for the final mile delivery to the Customer.
*   **Spreadsheets/Notes:** Used by Jastipers to manually cobble together order management systems.

These tools are powerful individually but operate in silos, requiring the user to manually bridge the gaps between discovery, communication, payment, and tracking.

---

## 8. Current Challenges

### Trust Challenges
*   Lack of secure, escrowed payment systems leads to hesitation from new Customers.
*   Absence of a standardized, verified review or rating system makes it hard to distinguish reliable Jastipers from scammers.
*   No guarantees on product authenticity or condition upon arrival.

### Operational Challenges
*   Manual order tracking using spreadsheets is prone to human error, missed orders, and incorrect pricing.
*   Managing luggage capacity versus order volume is a complex, informal calculation.
*   Sorting and packing upon return is highly labor-intensive and chaotic.

### Communication Challenges
*   Fragmented communication across multiple apps (Instagram DM, WhatsApp, Line) leads to lost messages and delayed responses.
*   Time-zone differences complicate real-time approvals for item substitutions while the Jastiper is in-store.

### Transaction Challenges
*   Manual verification of transfer receipts is tedious and susceptible to fake receipt fraud.
*   Managing varying exchange rates dynamically is difficult and often results in pricing disputes or eroded margins for the Jastiper.

### Scalability Challenges
*   A Jastiper's capacity is strictly limited by their personal time to reply to DMs and their physical luggage allowance.
*   The business model relies entirely on individual hustle rather than system-driven efficiencies.

---

## 9. Pain Points by Stakeholder

| Stakeholder | Pain Point | Business Impact |
| :--- | :--- | :--- |
| **Shoppers** | Fear of being scammed after sending deposit; lack of transparency in pricing and item status. | High barrier to entry; limits transactions to trusted circles only. |
| **Travelers (Jastipers)** | Overwhelming manual administration (chatting, logging orders, verifying payments) detracts from the travel experience. | Burnout; limits the number of orders they can handle per trip. |
| **Creators** | Drive product trends but have no direct way to monetize the demand they generate within the jastip ecosystem. | Lost revenue opportunities; disconnection from the commerce loop. |
| **Logistics Providers** | Receive unoptimized, fragmented shipments from individual Jastipers rather than aggregated volume. | Inefficient first-mile pickup; lost potential for B2B partnerships. |
| **Payment Providers** | Transactions occur as standard peer-to-peer transfers, missing out on e-commerce specific transaction fees or escrow value-adds. | Lost revenue on specialized financial services. |

---

## 10. Business Risks

*   **Fraud:** Customers are vulnerable to "hit and run" Jastipers who abscond with deposits. Jastipers face fake transfer receipts from Customers.
*   **Payment Disputes:** Disagreements over final pricing due to fluctuating exchange rates, hidden customs fees, or unexpected shipping costs.
*   **Lost/Damaged Orders:** Items can be confiscated by customs, lost in transit, or damaged in luggage, with no clear insurance or liability framework.
*   **Miscommunication:** Purchasing the wrong variant, size, or color due to informal chat-based ordering.
*   **Reputation Damage:** A single bad trip or delayed delivery can permanently destroy a Jastiper's social media credibility.
*   **Regulatory Issues:** Navigating complex and changing customs regulations and import taxes on personal goods.

---

## 11. Process Inefficiencies

*   **Manual Processes:** Recording orders from chat to spreadsheets, verifying payments via screenshots, and manually typing out shipping labels.
*   **Duplicate Work:** Customers repeatedly sending their address to different Jastipers; Jastipers repeatedly explaining their terms and conditions.
*   **Time-Consuming Activities:** Real-time, 1-on-1 chatting to confirm prices and availability while physically standing in an overseas store.
*   **Lack of Automation:** No automated notifications for order status, payment receipts, or shipping updates.
*   **Information Fragmentation:** Discovery happens on Instagram, negotiation on WhatsApp, and payment on a banking app, creating a disjointed user journey.

---

## 12. Opportunity Areas

*   **Trust:** Introducing escrow mechanisms, verified profiles, and standardized review systems to formalize reputation and secure transactions.
*   **Community:** Creating dedicated spaces where shoppers can request items and travelers can crowd-source demand before planning a trip.
*   **Commerce:** Streamlining the cataloging process so Jastipers can easily list items and Customers can "add to cart" rather than initiating a chat.
*   **Travel Planning:** Integrating the commerce aspect directly into trip planning, allowing travelers to offset costs by matching with requests along their route.
*   **Discovery:** Centralizing product discovery so Customers can browse trending international items and immediately connect with travelers heading to those destinations.
*   **Transparency:** Providing clear, automated breakdowns of item costs, service fees, exchange rates, and shipping, removing the need for manual quoting.

---

## 13. AS-IS Summary

The current Indonesian Jastip ecosystem is a testament to consumer resourcefulness and the power of social networks, thriving despite significant friction.

*   **Current Ecosystem Strengths:** It is highly adaptable, deeply community-driven, and excels at hyper-local or niche product discovery that traditional cross-border e-commerce cannot quickly fulfill. It leverages existing, ubiquitous digital tools (Instagram, WhatsApp) ensuring a low learning curve for participation.
*   **Current Ecosystem Weaknesses:** The reliance on informal communication and un-escrowed payments creates profound trust deficits. Operational scaling is nearly impossible due to extreme manual administrative burdens, fragmented workflows, and a lack of integrated commerce infrastructure.
*   **Business Opportunities for Transformation:** There is a massive opportunity to build a unified platform that acts as the missing infrastructure layer. By replacing siloed apps with a cohesive Social Commerce and Travel Commerce platform, "My Trip My Titipan" can automate administrative burdens, secure transactions via escrow, and foster a trusted, scalable community where travel planning natively intersects with cross-border shopping.
