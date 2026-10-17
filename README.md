# Real-Estate-Market-Analytics

Analyze property prices, market liquidity, and investment potential across European countries and cities to support data-driven real estate decisions.

## I. Introduction

### 1. Dataset

The dataset represents a European real estate listing platform, containing 5,000 property listings across 10 countries (France, Netherlands, Germany, Spain, Italy, Austria, Portugal, Poland, Czech Republic, Belgium) and their major cities.

#### Real Estate Listings Table

| Column Name | Data Type | Description |
|---|---|---|
| property_id | STRING | Unique property identifier |
| country / city | STRING | Property location |
| property_type | STRING | Apartment, Office, Retail, Villa, Townhouse, Warehouse, Mixed-Use |
| listing_type | STRING | Sale or Rental |
| sale_price_eur | FLOAT | Sale price in EUR |
| monthly_rent_eur | FLOAT | Monthly rent in EUR |
| price_per_sqm | FLOAT | Price per square meter |
| square_meters | FLOAT | Property size |
| bedrooms / bathrooms | INTEGER | Room counts |
| furnishing_status | STRING | Furnished, Semi-Furnished, Unfurnished, Unspecified |
| energy_rating | STRING | Energy efficiency rating (A-G) |
| elevator / gym / swimming_pool | STRING | Amenity flags (Yes/No) |
| floor_number | INTEGER | Floor level |
| parking_spots | INTEGER | Number of parking spots |
| year_built | INTEGER | Construction year |
| days_on_market | INTEGER | Days the listing has been active |
| Capital Gain % | FLOAT | Pre-calculated capital appreciation estimate |

### 2. Problem to Be Solved

Build a decision-making report for real estate analysts, property investors, and marketplace product teams to:
- Understand how prices vary across locations and property characteristics
- Identify which properties stay longest on the market and why
- Spot locations with high value but weak liquidity
- Rank cities by investment attractiveness (yield and capital growth combined)
Key Questions to Explore
-	How do property prices and price per square meter vary across countries and cities?
-	Which locations and property types have the highest average listing values?
-	How do property characteristics such as size, bedrooms, bathrooms, and building age influence pricing?
- Do properties with premium amenities (parking, elevators, gyms, pools) command higher prices?
- Which properties stay longest on the market ?
- Are there locations that show high property values but lower market activity?
- Which cities might present the most attractive opportunities for real estate investors?


## II. Design Thinking

### STEP 1: Empathize
<img width="2280" height="690" alt="Designer (4)" src="https://github.com/user-attachments/assets/66db4dc6-707b-4de4-b869-a5422ecf206e" />


### STEP 2: Define POV

North star metric
- Summary: Total Listing
- Market Liquidity: Average days on market
- Investor Opportunities: Perccentage of Average Capital Gain (%), Percentage of Gross Rental Yield (%)
- Property value drivers: Price per square meter

### STEP 3: Ideate

Four report pages were planned: Overview (market pulse), Price Drivers (what influences value), Market Liquidity (what slows sales down), Investor Opportunities (where to invest) and Property Deepdive (Explorer - find and compare properties easily)

### STEP 4: Prototype and Review

Chart types were chosen to match each question's data structure: bar charts for mutually exclusive categories, matrix/heatmap for two-dimensional combinations, scatter plots for continuous relationships, and composite scoring tables for investment ranking.

## III. Visualization

### OVERVIEW
Overview - what does the market look like?
- How have listings changed over time?
- Are there locations with high property values but lower market activity?
- What types of properties dominate the market?
- Which size band has the most sale and rental listings?
- How do amenities and furnishing show up across listings?

<img width="1053" height="672" alt="image" src="https://github.com/user-attachments/assets/5a4f29c4-0912-4683-bb37-93046260ac97" />


Insights
- Quarterly listings fluctuate cyclically (~215-285 per quarter) with no long-term upward or downward trend. The deepest trough is around Q3 2022.
- Listing volume is fairly even across countries (0.3K-0.7K). The most expensive countries (France €5.2K/sqm, Netherlands €4.8K/sqm) are not the least active.
- Closest exception to "high value, low activity": Belgium. It has the fewest listings (305) at a mid-range price (€2.8K/sqm), the same price as Italy and Austria, which have ~530-536 listings (Belgium ~42% fewer).
- Residential dominates the market (3.2K of 5K listings), followed by Commercial (1.4K) and Mixed Use (0.4K).
- Medium (100-200 sqm) dominates both sale (1,261) and rental (851) listings. Rental listings sit below sale listings in every size band.
- 1,775 listings (~35%) have bathrooms unspecified, the largest group, ahead of 2 bathrooms (1,661) and 1 bathroom (1,280).

### PRICE DRIVERS
Price Drivers - what influences property value?
- Do amenities like gyms or pools increase value?
- Does size band influence price?
- Are bigger properties always more expensive per sqm?
- Is energy efficiency more expensive per sqm?
- Does age influence price?
- Does floor level make a difference?
- How do bedrooms and bathrooms combine to influence price?

<img width="1422" height="713" alt="image" src="https://github.com/user-attachments/assets/e2fa0c0a-07b7-43f3-a4f3-4e125b3fedc6" />

Insights
- Amenities do not add value cumulatively. Elevator + gym + pool averages the lowest price/sqm (€2.5K), below no amenities (€3.0K). Elevator + Pool is the highest pairing (€3.5K). Hypothesis (untested): amenities signal a market segment rather than cause higher prices.
- Price/sqm rises with size band: Extra Large €4.0K, Large €3.5K, Medium €3.1K, Small €2.8K, Micro €2.4K. Medium has the most listings; Extra Large has the fewest. Most listings fall in the 50-200 sqm range.
- Energy rating shows no clear pattern. A-rated properties are not priced highest (B is highest, ~€3.4K/sqm).
- Newer buildings carry a premium: <11 years €4.2K/sqm, 11-20 years €3.7K, versus ~€3.1K-3.3K for older bands.
- Floor number has no visible relationship with price/sqm.
- Price/sqm ranges roughly €2.5K-3.7K across bedroom/bathroom combinations with no clear monotonic pattern. The highest cell (~€3.7K) is in the 4-bathroom row, which has only 61 listings.
- Residential Extra Large has the highest price/sqm (€6.55K) and the longest days on market (265 vs 172 overall), a high-value, slow-selling segment.

### MARKET LIQUIDITY
How fast are properties selling?
- How many listings sit in each days-on-market band?
- Which countries sell fastest, and at what price level?
- Which properties stay longest on the market?

<img width="1212" height="580" alt="image" src="https://github.com/user-attachments/assets/387acdc1-630f-4c1e-9db4-185518ed9cfe" />

Insights
- The whole market is slow. All 10 countries average 162-183 days on market, nearly double the 90-day benchmark.
- Country barely matters. Fastest (Czech Republic, 162) vs slowest (Netherlands, 183) differ by only ~21 days.
- The problem is long-tail listings: ~44% sit 180+ days and only ~28% are at 90 days or less.
- Property type barely matters either. Retail is slowest (178), Villa fastest (164).
- Price does not track speed. Czech Republic is cheap and fast, Netherlands expensive and slow, France expensive but average.

### INVESTOR OPPORTUNITIES
Investor opportunities finder
- Which cities offer the most attractive opportunities?
- Which countries have the highest average capital gain %?
- Which property type offers the best mix of rental income and price growth?
- Which cities combine high rental yield and strong capital growth?

<img width="1185" height="565" alt="image" src="https://github.com/user-attachments/assets/4a375b24-f066-441b-9802-6579adbbf64d" />

Insights
- Vienna and Berlin are the most attractive cities: highest rental yield (5.2%, 5.0%) and top Investor Score.
- Higher price does not mean higher yield. Paris (€5.2K/sqm) is the highest-value city but has the lowest yield (3.6%, tied with Rome). Amsterdam (€4.8K/sqm) yields 4.0%.
- Brussels is the growth pick: highest capital gain (116.9%) with a 4.6% yield, but a lower Investor Score than Berlin and Vienna.
- Residential is the most balanced: highest capital gain (~100%) and a solid yield (4.5%).
- Mixed Use has the highest yield (4.8%) but the lowest capital gain (~57%). Commercial trails Residential on both (3.8% yield, ~68% gain).

### EXPLORE - FIND AND COMPARE PROPERTIES EASILY
Browse and compare individual properties in every dimension.

<img width="1133" height="638" alt="image" src="https://github.com/user-attachments/assets/7b303ddd-0fb6-4f7d-b1b4-68a25feb17d2" />

## IV. Insight and Recommendation

| Page | Insight | Recommendation |
|---|---|---|
| Overview | ~35% of listings have bathrooms unspecified | Make bathrooms a required field on the platform, and report the Unspecified share in any bathroom analysis |
| Price Drivers | Amenities do not add value cumulatively: elevator + gym + pool has the lowest price/sqm (€2.5K) | Do not use amenity count as a price proxy. Control for property type and location in valuation models |
| Price Drivers | Price/sqm rises with size band (€2.4K to €4.0K), and buildings under 20 years carry a premium (€4.2K, €3.7K vs ~€3.1-3.3K) | Benchmark within size and age band, not only by city average. Check the age premium holds after controlling for city |
| Price Drivers | Residential Extra Large: €6.55K/sqm and 265 days on market | High value, low liquidity. Test price reductions here first (small sample, validate before acting) |
| Market Liquidity | The whole market is slow (162-183 days) and ~44% of listings sit 180+ days, while country and property type explain little | Add stale-listing indicators and repricing prompts past 90 days. Look at listing-level drivers (price vs comparables, condition), not country or type |
| Market Liquidity | Price level does not track speed | A/B test price reductions before assuming discounting speeds up sales |
| Investor Opportunities | Vienna and Berlin lead on yield and Investor Score; Paris and Amsterdam are priciest but low-yield | Shortlist Vienna and Berlin and check liquidity before committing. Do not treat high price as a quality signal for income |
| Investor Opportunities | Brussels has the highest capital gain (116.9%) | Treat as a lead to validate, not a pick: Capital Gain % is a pre-calculated estimate |
| Investor Opportunities | Residential balances growth and yield; Mixed Use leads on yield only (~7% of listings) | Residential for balanced returns. Mixed Use as a niche income play, with small-sample caution |
