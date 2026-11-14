# Awesome-Promotion-Coupon-Discount-Management

# Awesome Promotion, Coupon & Discount Management

> A curated list of top Promotion, Coupon and Discount Management platforms — both SaaS/Hosted commercial promotion engines and open-source alternatives for building discount rules, coupon codes, and campaign logic.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Chargebee Coupons & Discounts](#chargebee-coupons--discounts)
  - [Voucherify](#voucherify)
  - [Talon.One](#talonone)
  - [SaaSquatch](#saasquatch)
  - [Open Loyalty](#open-loyalty)
  - [Antavo](#antavo)
  - [SessionM](#sessionm)
- [Open-Source Software](#-open-source-software)
  - [Django Coupons](#django-coupons)
  - [Loyalty Card Service](#loyalty-card-service)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Promotion, Coupon and Discount Management platforms. These are not open-source but are included as reference points for feature comparison.

### Chargebee Coupons & Discounts
**Type:** Billing-native coupon and discount engine with strict application order
Chargebee provides a native coupon and discount system tightly integrated with subscription billing. Coupons can be fixed-amount or percentage-based, applied at the line-item or invoice level [citation:1]. A critical differentiator is the **defined order of application** when multiple coupons and discounts stack: line-level fixed coupons apply first, then line-level fixed discounts, then line-level percentage coupons and discounts, followed by invoice-level fixed coupons, invoice-level fixed discounts, and finally invoice-level percentage coupons and discounts [citation:1]. For example, a 1% off addon coupon applies before a flat $2 invoice coupon, which applies before a flat $5 invoice discount [citation:1]. Redemption limits can be enforced per customer (by Customer ID or Email, locked after first save), with server-side checks blocking checkout if the limit is exceeded [citation:11]. Eligibility can target New Customers or Existing Customers (Beta) [citation:11].
**Best for:** Chargebee billing customers wanting native coupon logic with predictable, documented stacking order and server-side redemption enforcement.

### Voucherify
**Type:** API-first promotion engine with agentic commerce support
Voucherify is an API-first promotion engine covering auto-applied rule-based promos, BOGOs, bundles, strikethrough pricing, and gift cards [citation:2]. Promotions can trigger based on location, behavior, cart contents, or any custom data point, with sub-50ms response times for real-time validation [citation:2]. It includes a **qualification API** that returns all possible redeemables a customer can use, enabling homepage promotion displays and checkout upselling [citation:2]. Promotion tiers can be added to campaigns with hierarchy control, activation windows, and day-of-week/hours validity for happy-hour scenarios [citation:12]. A built-in agent (**Vincent**) builds campaigns from natural language descriptions and benchmarks incentive performance [citation:2]. Fraud controls include redemption caps, channel restrictions, budget limits, and segment targeting [citation:2].
**Best for:** Developers and product teams wanting a composable, API-first promotion engine with complex eligibility logic and agentic campaign building.

### Talon.One
**Type:** Headless loyalty and promotion engine with gamification
Talon.One provides a headless, no-code platform for building promotions and gamified loyalty programs by clicking together triggers and effects [citation:3][citation:13]. It covers coupons, referrals, discounts, product bundling, markdown pricing, and **gamification mechanics**: challenges (one-time or recurring), leaderboards, progress trackers, milestones, and badges [citation:3]. Campaigns can be built and optimized in real time, with strikethrough pricing support for SKU-level promotions [citation:13]. The engine emphasizes automated scaling for peak traffic and EU Price Indication Directive compliance.
**Best for:** E-commerce teams wanting a real-time promotion engine with strong gamification and pricing compliance features, particularly those running high-volume promotional calendars.

### SaaSquatch
**Type:** Referral and loyalty engine with calculated fields
SaaSquatch specializes in referral and loyalty programs with **calculated fields** that track events, apply calculations, and store results on participant profiles dynamically [citation:4]. This enables complex cumulative reward rules (e.g., "reward participants who make 3+ purchases of at least $50 in the month after a referral") with fixed or rolling tracking windows. The platform includes a Rewards Catalog, Reward Units, Fuel Tank codes for bulk redemption, user segmentation, and fraud flagging based on custom fields [citation:4][citation:14]. Analytics reports can be bulk-exported in CSV/XLSX [citation:4].
**Best for:** Teams building referral and loyalty programs that require event-driven, cumulative reward logic beyond simple coupon codes.

### Open Loyalty
**Type:** Loyalty platform with event-driven rewards and audit controls
Open Loyalty provides loyalty program management with **campaign expression language** now supporting milestone progress (rewards fire as members reach each milestone, not only on completion) [citation:5]. Challenges can be duplicated between tenants, and a dedicated **tier performance analytics dashboard** tracks average/median time in each tier and member movement between tiers [citation:5]. Unit transfer records now carry custom attributes (campaign type, source, budget category), with bulk expiration date changes on filtered transfers [citation:5]. **Audit logging is enforced** for configuration changes across campaigns, rewards, wallets, and member records, recording which administrator made each change [citation:5]. An **MCP server** connects AI assistants to members, points, rewards, campaigns, and analytics [citation:15].
**Best for:** Organizations running loyalty programs that need event-driven integrations, milestone rewards, and enterprise-grade audit traceability.

### Antavo
**Type:** Enterprise loyalty with deep Shopify integration and segmentation
Antavo's Q2 2026 release deepened its **Shopify integration** with bidirectional data flow, checkout widgets for point redemption, and "claim past purchases" to convert anonymous checkouts into known members [citation:6]. **Audiences** provides segmentation from a data lake or CDP that can ingest millions of customers in seconds, with segment-of-one personalization planned [citation:6]. **Upsell messaging** triggers based on basket thresholds on product listing, detail, or cart pages [citation:6]. Product Hub represents the catalog accurately for discounts and loyalty benefits [citation:6].
**Best for:** Shopify-centric brands wanting deep loyalty integration with sophisticated segmentation and gamification, particularly multi-market deployments.

### SessionM
**Type:** Earn-and-burn loyalty with configurable points
SessionM (Capillary Technologies) provides points-based loyalty programs with configurable point accounts, point sources, expiration policies, and redemption at point of sale or through a rewards store [citation:7]. Campaigns can be scheduled and triggered across channels from a self-service hub, with daily dashboards for program performance [citation:7].
**Best for:** Enterprises wanting a traditional earn-and-burn loyalty program with flexible points configuration and in-store redemption.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Promotion, Coupon and Discount Management tools. The open-source ecosystem is **very limited** — available projects are framework-specific libraries rather than full promotion engines.

### Django Coupons
**Stack:** Python / Django | **License:** MIT
Django Coupons is a reusable Django app for managing promotional codes, discount rules, and coupon validation [citation:9]. Key features include percentage or fixed-amount discounts, user-specific or global coupons, usage limits (max total, per-user, or unlimited), expiration and active/inactive rules, Django Admin integration with bulk actions (reset usage, delete expired), and a simple validation API (`validate_coupon()`) returning `{'valid': True}` or a human-readable error message [citation:9]. Coupon codes auto-generate with configurable length via `DSC_COUPON_CODE_LENGTH` [citation:9]. It includes a REST API example for Django REST Framework integration [citation:9].
**Best for:** Django developers needing a lightweight, MIT-licensed coupon system embedded directly in their application, accepting that it covers coupon validation and usage tracking but not campaign orchestration or loyalty.

### Loyalty Card Service
**Stack:** Go / Fiber / GORM | **License:** GPLv3
Loyalty Card Service is an open-source RESTful backend for managing loyalty programs, guests, scores, and tags [citation:10]. It provides a modular Go codebase with Swagger/OpenAPI documentation, Docker support, PostgreSQL/SQLite via GORM, and CLI support via Cobra [citation:10]. API endpoints cover guest creation, score creation and usage, and tag management [citation:10]. It is a **loyalty points backend** rather than a coupon or promotion engine — it handles points/scores but not discount codes or campaign rules.
**Best for:** Go developers wanting a self-hosted loyalty points backend with a clean REST API, accepting that promotion and coupon logic must be built separately.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Coupon Codes | Stacking Order | Loyalty/Points | Self-Hosted | Best For |
|----------|---------|-------|--------------|----------------|----------------|-------------|----------|
| **Chargebee** | Proprietary | Cloud | ✅ Full | ✅ Documented 8-step | ❌ | ❌ | Billing-native coupons |
| **Voucherify** | Proprietary | Cloud | ✅ Full | ✅ Tier hierarchy | ✅ | ❌ | API-first promotion engine |
| **Talon.One** | Proprietary | Cloud | ✅ | (Campaign rules) | ✅ Gamification | ❌ | Real-time + gamified loyalty |
| **SaaSquatch** | Proprietary | Cloud | (Referral) | (Calculated fields) | ✅ | ❌ | Event-driven referrals |
| **Open Loyalty** | Proprietary | Cloud | (Check) | (Campaign rules) | ✅ Milestones | ❌ | Audit-ready loyalty |
| **Antavo** | Proprietary | Cloud | (Check) | (Campaign rules) | ✅ Shopify | ❌ | Shopify loyalty + segments |
| **Django Coupons** | MIT | Django | ✅ | (Basic rules) | ❌ | ✅ | Django coupon validation |
| **Loyalty Card** | GPLv3 | Go/Fiber | ❌ | ❌ | ✅ Scores | ✅ | Go loyalty points backend |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Promotion, Coupon or Discount Management tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem for **full promotion engines** is **very limited and fragmented**. **Django Coupons** is the most practical open-source option for coupon code validation within a Django application [citation:9], while **Loyalty Card Service** provides a Go-based loyalty points backend [citation:10]. No open-source project replicates the full breadth of Chargebee's documented stacking order, Voucherify's qualification API, or Talon.One's gamification engine — commercial platforms remain the only viable option for production-grade promotion orchestration at scale.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
