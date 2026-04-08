
# Taxitrip-Data-Exploratory-Data-Analysis
Apply EDA to 2023 NYC taxi data to derive strategic insights for optimizing fleet operations and enhancing business profitability.

## Objective
This assignment aims to give you an idea of applying EDA in real-world scenarios. In addition to using the techniques that you have learnt in the EDA module, you will develop a basic understanding of analytics for real-world situations, how to integrate them into a narrative and draw usable insights. 

## Business Value
In this case study, you will learn about exploratory data analytics with the help of a data set on yellow taxi rides in New York City. Taxis play a crucial role in New York City’s urban transport network. With the city’s dynamic environment, taxi companies need to continuously adapt and optimize their operations to meet changing demand patterns, ensure profitability and enhance customer satisfaction.

In this project, the 2023 taxi trip data is analyzed to uncover insights that could help optimize taxi operations. The goal is to analyze patterns in the data that can inform strategic decisions to improve service efficiency, maximize revenue and enhance passenger experience.

## Dataset Overview
### Context
The yellow taxi trip records include fields capturing details of the trips taken every day by yellow taxis in New York City. The data is stored in Parquet format (.*parquet*). The data set is from 2009 to 2024. However, we will only be using the data from 2023. The data for each month is present in a different Parquet file. You will receive 12 files, one for each of the months in 2023. The data was collected and provided to the NYC Taxi and Limousine Commission (TLC) by technology providers such as vendors and taxi-hailing apps.

### Content
1. The dataset contains a set of 12 Parquet files having records on attributes such as vendor ID, time and locations of pick-up and drop-off, payment type, fare amount and tips.
2. Apart from the trip data, you will find a zipped folder taxi_zones. This folder has a *[shapefile](https://doc.arcgis.com/en/arcgis-online/reference/shapefiles.htm)* containing geometric data about the taxi zones. You will learn more about this while attempting the assignment.

You can find the data dictionary [here](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf) and with the dataset provided on the platform.

## Conclusion
### Final Insights and Recommendations
*Recommendations to optimize routing and dispatching based on demand patterns and operational inefficiencies.*

To maximize revenue and minimize downtime, the fleet must follow a "Dynamic Hub-and-Spoke" strategy that shifts based on the temporal data uncovered in our analysis.

1. Strategic Positioning Recommendations
Prioritize Transit "sources" for Inbound Waves: Cabs should be staged at JFK, LGA, and Penn Station during the early morning and late night.

   *Justification*: Section 3.2.6 (Source/Sink Analysis) showed East Elmhurst and JFK as massive source zones (ratios up to 9.1). Because these are "one-way" demand hubs, supply must be manually replenished rather than relying on natural drop-offs.

3. The "Leisure Triangle" Weekend Shift: From 11 PM to 5 AM on Fridays and Saturdays, drivers should move away from the Financial District and Midtown toward the East Village, West Village, and Lower East Side.

   *Justification*: Section 3.2.7 (Night-Time Hotspots) proved these are the top night-time pickup zones. By positioning here, drivers catch the "Social Surge" where passenger counts are higher (Section 3.2.14) and tipping behavior is more generous during leisure hours (Section 3.2.13).

4. Strategic Avoidance of "Sink" Traps: Limit dispatches to residential zones in Staten Island and the Bronx unless a high-value fare is guaranteed.

     *Justification*: Section 3.2.6 identified these as "Zero-Ratio" zones (0.0). Every trip to these locations results in "deadheading" (empty miles) back to a hub, which destroys the "Fare per Mile" efficiency calculated in Section 3.2.10.

4. Rush-Hour Bypass Strategy: During peak windows (8 AM and 5 PM), cabs should be positioned in Lower Manhattan (Village/SoHo) rather than navigating the Sunnyside or Midtown bottlenecks.

    *Justification*: Section 3.2.1 (Bottleneck Analysis) showed average speeds in heavy traffic zones dropping below 0.1 MPH. Staging in slightly less congested "Source" zones nearby allows for more completed trips compared to being stuck in stationary traffic.

*Proposed data-driven adjustments to the pricing strategy to maximize revenue while maintaining competitive rates with other vendors.*

1. *Standardize "Short-Tier" Pricing Across Vendors*:

*Recommendation*: Address the massive price gap in short trips ($0-2$ miles) where VeriFone ($18.35$/mile) is significantly more expensive than Creative Mobile ($11.73$/mile).

*Justification*: Section 3.2.12 shows that while long and medium trips are priced similarly, short trips vary by over $50\%$ between vendors. Standardizing this prevents "vendor-shopping" and ensures a predictable customer experience for the most common city trips.


2. *Tiered Pricing for "High-Occupancy" Vehicles*:

*Recommendation*: Implement a "Group Base Fare" for trips with $5-6$ passengers to offset the massive drop in revenue per person.

*Justification*: Section 3.2.9 shows that revenue per passenger drops from $\$11.28$ (solo) to a meager $\$1.31$ (group of 6). While group travel is efficient for the city, the current flat-fare model drastically undervalued the "wear and tear" of high-occupancy trips. A small per-passenger surcharge for groups over 4 would balance this.

3. *Protect Profitability on "Short-Tier" Routes*:

*Recommendation*: Maintain the high fare-per-mile for short distances but implement a "Congestion Buffer" during peak hours to protect drivers from the bottlenecks found in Section 3.2.1.

*Justification*: Section 3.2.12 confirms that short trips are the highest revenue generators per mile ($\approx \$11-\$18$). However, since these often occur in congested areas, the high rate per mile is easily erased by time lost in traffic. A "Minimum Fare" for trips under 1 mile would protect driver earnings in the Manhattan core.

4. *Incentivize "Long-Tier" Airport Runs*:

*Recommendation*: Offer a "Return Toll Credit" or a "Long-Distance Bonus" for trips over 5 miles, specifically targeting the Source Hubs identified in Section 3.2.6.

*Justification*: Section 3.2.12 shows that "Long-Tier" trips have the lowest fare-per-mile ($\approx \$4.45$). Without incentives, drivers may prefer staying in the high-rate "Short-Tier" circuit, leading to a supply shortage at the airports (JFK/LGA).
