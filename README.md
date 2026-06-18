AtliQ Hotels — Revenue Intelligence Dashboard

A Power BI dashboard built for AtliQ Grands, a five-star hotel chain operating across India, to help their revenue management team recover market share and revenue in the luxury and business hotel segments through data-driven decision-making.



Business Problem

AtliQ Grands has been a major player in the Indian hospitality industry for two decades, but recent competitive pressure and gaps in data-backed decision-making have caused them to lose market share and revenue, particularly in their luxury and business hotel categories. With no in-house data analytics team, the revenue management team needed an external, structured view into their operational and financial performance to start making informed pricing, occupancy, and platform decisions.

This project was built to address that gap: turning raw booking and property data into a single, actionable revenue intelligence dashboard.

What the Dashboard Covers

The dashboard is built around the core metrics the revenue management team needs to track performance at both a portfolio and property level:


Revenue — total revenue across all properties (₹1.69bn)
RevPAR (Revenue per Available Room)
Occupancy %
ADR (Average Daily Rate)
DSRN (Daily Sellable Room Nights)
Realisation % — how much of the listed rate is actually realized as revenue
Cancellation % and Average Rating per property


It's sliceable by City, Room type, and Week, and breaks performance down by:


Property (12 hotels across Bangalore, Mumbai, Hyderabad, and Delhi)
Category (Luxury vs. Business)
Day type (Weekday vs. Weekend)
Booking platform (logtrip, journey, direct online, direct offline, others, makeyourtrip, tripster)
Week-over-week trend (Weeks 19–32, spanning May–July)


Key Insights

Beyond the requested metrics, a few patterns emerged from the data that are directly actionable for the revenue management team:

1. Guest satisfaction tracks occupancy, not just price — and it cuts across both categories.
Every property with an average rating above 3.0 also has occupancy above 53%. The four lowest-rated properties (Atliq Grands Bangalore, Atliq Seasons Mumbai, Atliq Exotica Hyderabad, and Atliq Bay Mumbai — all rated 2.30–2.37) are also the four lowest-occupancy properties in the portfolio (44.3–44.9%). Critically, this split includes both Luxury and Business properties on both sides — so it isn't a category effect. It suggests service quality and demand are reinforcing each other at the property level, and underperforming properties may need an operational review rather than just a pricing fix.

2. Weekends consistently outperform weekdays across every metric.
RevPAR (₹7,971.63 vs ₹7,082.53), occupancy (62.64% vs 55.85%), ADR (₹12,725.49 vs ₹12,682.41), and realisation (70.59% vs 69.94%) are all higher on weekends. This points toward an opportunity for dynamic weekday pricing or weekday-specific promotions to close the gap.

3. Booking platforms show a pricing-vs-conversion tradeoff.
Platforms with the highest realisation % (logtrip at 70.57%) tend to have lower ADR, while platforms with the highest ADR (tripster) show the lowest realisation % (69.80%) among the group. This implies the highest "listed" rate isn't necessarily the most profitable channel once realisation is factored in — useful for channel-mix decisions.

4. Revenue is concentrated in Luxury, but Business is structurally more efficient at the city level.
Luxury accounts for 61.62% of total revenue vs. 38.38% for Business, but several Business-category properties (e.g., Atliq City Delhi, Atliq Grands Mumbai) post occupancy and realisation rates on par with or above some Luxury properties — suggesting Business hotels may be undervalued relative to their operational performance.

Data Model

The dashboard is built on a star schema with one fact table at the booking level, one pre-aggregated fact table for performance, and three dimension tables:

TableDescriptionRowsfact_bookings.csvBooking-level grain — one row per booking, with check-in/checkout dates, guests, platform, status, revenue generated vs. realized, and ratings~134,590fact_aggregated_bookings.csvPre-aggregated daily bookings by property and room category (successful bookings vs. capacity) — used for faster occupancy/RevPAR calculations~9,200dim_date.csvDate dimension with month-year, week number, and weekday/weekend flag92dim_hotels.csvProperty dimension — property ID, name, category (Luxury/Business), and city25dim_rooms.csvRoom dimension — room type ID mapped to room class (Standard, Elite, Premium, etc.)4

fact_bookings joins to dim_hotels on property_id, to dim_rooms on room_category/room_id, and to dim_date on check_in_date. This structure is what powers the WoW trends, day-type splits, and platform-level realisation metrics in the dashboard.

Tools Used


Power BI Desktop — data modeling, DAX measures, and dashboard build
DAX — custom measures for RevPAR, Realisation %, WoW change %, and category splits
Star-schema data modeling (1 booking-level fact table, 1 aggregated fact table, 3 dimension tables)

How to Use


Clone the repo
Open hospitality_dashboard.pbix in Power BI Desktop
Explore the dashboard using the City, Rooms, and Weeks filters in the top right


Author

Built as a portfolio project applying business and data intelligence to a real-world hospitality revenue management scenario.
