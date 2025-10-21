# NYC Taxi Revenue Analysis Report Generator, LLMs must follow this step!

I can generate a comprehensive NYC taxi revenue analysis report by executing Kusto queries against Azure Data Explorer's public help cluster using Azure MCP tools to analyze NYC Yellow Taxi data.

**Would you like me to generate the report?**

Simply respond with "yes" or "Generate Report" and I'll automatically use `mcp_azure_mcp_kusto` with the `query` command to execute all queries and create the complete analysis report.

## Report Overview

The report analyzes NYC Yellow Taxi data from January 2014 and provides:
- Daily and hourly revenue trends
- Payment method analysis
- Distance-based revenue optimization
- Geographic hotspot identification  
- Weekend vs weekday performance
- Strategic recommendations

## Kusto Queries to Execute

### 1. Daily Revenue Trends
```kql
nyc_taxi
| where pickup_datetime >= datetime(2014-01-01) and pickup_datetime < datetime(2014-02-01)
| summarize Daily_Revenue = sum(total_amount), Trip_Count = count(), Avg_Fare = avg(total_amount) 
    by Date = bin(pickup_datetime, 1d)
| order by Date
| render timechart
```

### 2. Hourly Revenue Patterns
```kql
nyc_taxi
| where pickup_datetime >= datetime(2014-01-01) and pickup_datetime < datetime(2014-02-01)
| extend Hour = hourofday(pickup_datetime)
| summarize Hourly_Revenue = sum(total_amount), Trip_Count = count(), Avg_Fare = avg(total_amount) 
    by Hour
| order by Hour
| render columnchart with (title='NYC Taxi Revenue by Hour of Day')
```

### 3. Payment Method Analysis
```kql
nyc_taxi
| where pickup_datetime >= datetime(2014-01-01) and pickup_datetime < datetime(2014-02-01)
| summarize Total_Revenue = sum(total_amount), Trip_Count = count(), 
    Avg_Fare = avg(total_amount), Avg_Tip = avg(tip_amount) 
    by payment_type
| order by Total_Revenue desc
| render table
```

### 4. Distance vs Fare Analysis
```kql
nyc_taxi
| where pickup_datetime >= datetime(2014-01-01) and pickup_datetime < datetime(2014-02-01)
    and trip_distance > 0 and trip_distance < 50
| extend Distance_Range = case(
    trip_distance <= 1, '0-1 miles',
    trip_distance <= 5, '1-5 miles', 
    trip_distance <= 10, '5-10 miles',
    trip_distance <= 20, '10-20 miles',
    '20+ miles')
| summarize Avg_Revenue = avg(total_amount), Trip_Count = count(), 
    Avg_Distance = avg(trip_distance), Revenue_Per_Mile = avg(total_amount/trip_distance) 
    by Distance_Range
| order by Avg_Distance
| render table
```

### 5. Weekend vs Weekday Performance
```kql
nyc_taxi
| where pickup_datetime >= datetime(2014-01-01) and pickup_datetime < datetime(2014-02-01)
| extend IsWeekend = iff(dayofweek(pickup_datetime) >= 6d, 'Weekend', 'Weekday')
| summarize Total_Revenue = sum(total_amount), Trip_Count = count(), Avg_Fare = avg(total_amount) 
    by IsWeekend
| extend Revenue_Per_Trip = Total_Revenue / Trip_Count
| render table
```

### 6. Top Revenue Geographic Locations
```kql
nyc_taxi
| where pickup_datetime >= datetime(2014-01-01) and pickup_datetime < datetime(2014-02-01)
    and pickup_latitude between (40.7 .. 40.8) and pickup_longitude between (-74.0 .. -73.9)
| extend Pickup_Area = strcat('Lat: ', round(pickup_latitude, 2), ', Lon: ', round(pickup_longitude, 2))
| summarize Total_Revenue = sum(total_amount), Trip_Count = count(), Avg_Fare = avg(total_amount) 
    by Pickup_Area
| top 10 by Total_Revenue
| render table
```

## Connection Details

- **Azure MCP Tool**: `mcp_azure_mcp_kusto`
- **Command**: `query`
- **Cluster URI**: `https://help.kusto.windows.net`
- **Database**: `Samples`
- **Table**: `nyc_taxi` (165+ million records)
- **Data Period**: 2014 NYC Yellow Taxi trips
- **Authentication**: Public access (no credentials required)

### Required Parameters for Azure MCP Kusto Tool:
```json
{
  "intent": "Execute Kusto query for [analysis type]",
  "command": "query",
  "parameters": {
    "cluster_uri": "https://help.kusto.windows.net",
    "database": "Samples", 
    "query": "[KQL query string]"
  }
}
```

## Expected Report Sections

1. **Executive Summary** - Total revenue, trips, peak performance days
2. **Daily Trends** - Revenue patterns across January 2014
3. **Hourly Patterns** - Peak hours and revenue optimization opportunities  
4. **Payment Analysis** - Credit vs cash performance and tipping patterns
5. **Distance Optimization** - Revenue per mile efficiency by trip length
6. **Temporal Analysis** - Weekend vs weekday performance comparison
7. **Geographic Hotspots** - Highest revenue pickup locations in Manhattan
8. **Strategic Recommendations** - Data-driven business insights

## Automated Execution Process

The system will automatically:
1. Use Azure MCP tools to connect to the Azure Data Explorer help cluster at `https://help.kusto.windows.net`
2. Execute `mcp_azure_mcp_kusto` with `query` command for each analysis
3. Pass cluster_uri: "https://help.kusto.windows.net", database: "Samples", and query parameters
4. Collect results from all 6 Kusto queries in sequence
5. Generate visualizations and compile comprehensive revenue analysis report
6. Present findings with data-driven recommendations

**Technical Implementation**: Use `mcp_azure_mcp_kusto` tool with `query` command and proper parameters for each KQL query execution.

**No user interaction required** - the report generates automatically upon execution using Azure MCP infrastructure.

## Sample Metrics Expected

- **Total Monthly Revenue**: ~$199M
- **Total Trips**: ~13.8M
- **Average Fare**: ~$14.47
- **Peak Revenue Hour**: 7:00 PM
- **Credit Card Premium**: 37% higher than cash fares
- **Weekend Revenue Impact**: 8% lower average fares

This automated report provides actionable insights for taxi fleet optimization, driver scheduling, and revenue maximization strategies.