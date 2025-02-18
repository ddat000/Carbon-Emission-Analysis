#Carbon - Emission - Analysis

## Introduction

### What is the project about?
 ![Alt text](https://github.com/ddat000/Carbon-Emission-Analysis/blob/main/cover.jpg)

This report aims to analyze carbon emissions to examine the carbon footprint across various industries. We aim to identify sectors with the highest levels of emissions by analyzing them across countries and years, as well as to uncover trends.

Carbon emissions play a crucial role in the environment, accounting for over 75% of global emissions and posing a significant environmental challenge. These emissions contribute to the accumulation of greenhouse gases in the atmosphere, leading to climate change, planetary warming, and involvement in various environmental disasters.

Through this analysis, we hope to gain an understanding of the environmental impact of different industries and contribute to making informed decisions in sustainable development.
### Data Source: Where Our Data Comes From
- Our dataset is compiled from publicly available data from nature.com and encompasses the product carbon footprints (PCF) for various companies.
- PCFs represent the greenhouse gas emissions associated with specific products, quantified in CO2 (carbon dioxide equivalent).

### Data Structure
- The dataset consists of 4 tables containing information regarding carbon emissions generated during the production of goods.
 ![Alt text](https://github.com/ddat000/Carbon-Emission-Analysis/blob/main/Database%20diagram.png)

### Tables' columns description and Data overview
- Table 'product_emissions'
  - id: Identifier for each product emission record.
  - company_id: Identifier for the company associated with the product.
  - country_id: Identifier for the country where the product is being produced.
  - industry_group_id: Identifier for the industry group to which the product belongs.
  - year: The year in which the emissions data was recorded.
  - product_name: The name of the product associated with the emissions data.
  - weight_kg: The weight of the product in kilograms.
  - carbon_footprint_pcf: The carbon footprint of the product, measured in CO2 equivalent.
  - upstream_percent_total_pcf: The percentage of the total carbon footprint attributed to upstream activities.
  - operations_percent_total_pcf: The percentage of the total carbon footprint attributed to operations.
  - downstream_percent_total_pcf: The percentage of the total carbon footprint attributed to downstream activities.

```sql
SELECT
    *
FROM
    product_emissions
LIMIT
    10;
```
| id            | company_id | country_id | industry_group_id | year | product_name                                                    | weight_kg | carbon_footprint_pcf | upstream_percent_total_pcf                       | operations_percent_total_pcf                     | downstream_percent_total_pcf                     | 
| ------------: | ---------: | ---------: | ----------------: | ---: | --------------------------------------------------------------: | --------: | -------------------: | -----------------------------------------------: | -----------------------------------------------: | -----------------------------------------------: | 
| 10056-1-2014  | 82         | 28         | 2                 | 2014 | Frosted Flakes(R) Cereal                                        | 0.7485    | 2                    | 57.50                                            | 30.00                                            | 12.50                                            | 
| 10056-1-2015  | 82         | 28         | 15                | 2015 | "Frosted Flakes, 23 oz, produced in Lancaster, PA (one carton)" | 0.7485    | 2                    | 57.50                                            | 30.00                                            | 12.50                                            | 
| 10222-1-2013  | 83         | 28         | 8                 | 2013 | Office Chair                                                    | 20.68     | 73                   | 80.63                                            | 17.36                                            | 2.01                                             | 
| 10261-1-2017  | 14         | 16         | 25                | 2017 | Multifunction Printers                                          | 110       | 1488                 | 30.65                                            | 5.51                                             | 63.84                                            | 
| 10261-2-2017  | 14         | 16         | 25                | 2017 | Multifunction Printers                                          | 110       | 1818                 | 25.08                                            | 4.51                                             | 70.41                                            | 
| 10261-3-2017  | 14         | 16         | 25                | 2017 | Multifunction Printers                                          | 110       | 2274                 | 20.05                                            | 3.61                                             | 76.34                                            | 
| 10324-1-2016  | 15         | 16         | 19                | 2016 | KURALON  fiber                                                  | 1500      | 10000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 10418-1-2013  | 84         | 9          | 19                | 2013 | Portland Cement                                                 | 1000      | 1102                 | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 10661-10-2014 | 85         | 28         | 11                | 2014 | Regular Straight 505® Jeans – Steel (Water                      | 0.7665    | 15                   | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 10661-10-2015 | 85         | 28         | 6                 | 2015 | Regular Straight 505® Jeans – Steel (Water                      | 0.7665    | 15                   | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 

- Table 'industry_groups'
  - id: Unique identifier for each industry group.
  - industry_group: The name of the industry group, categorizing businesses within similar sectors based on their products or services offered.

```sql
SELECT
    *
FROM
    industry_groups
LIMIT
    10;
```
| id | industry_group                                                         | 
| -: | ---------------------------------------------------------------------: | 
| 1  | "Consumer Durables, Household and Personal Products"                   | 
| 2  | "Food, Beverage & Tobacco"                                             | 
| 3  | "Forest and Paper Products - Forestry, Timber, Pulp and Paper, Rubber" | 
| 4  | "Mining - Iron, Aluminum, Other Metals"                                | 
| 5  | "Pharmaceuticals, Biotechnology & Life Sciences"                       | 
| 6  | "Textiles, Apparel, Footwear and Luxury Goods"                         | 
| 7  | Automobiles & Components                                               | 
| 8  | Capital Goods                                                          | 
| 9  | Chemicals                                                              | 
| 10 | Commercial & Professional Services                                     | 

- Table 'companies'
  - id: Unique identifier for each company.
  - company_name: The name of the company, identifying the specific organization within the dataset.

```sql
SELECT
    *
FROM
    companies
LIMIT
    10;
```
| id | company_name                                   | 
| -: | ---------------------------------------------: | 
| 1  | "Autodesk, Inc."                               | 
| 2  | "Casio Computer Co., Ltd."                     | 
| 3  | "Cisco Systems, Inc."                          | 
| 4  | "CNX Coal Resources, LP"                       | 
| 5  | "Coca-Cola Enterprises, Inc."                  | 
| 6  | "Compañía Española de Petróleos, S.A.U. CEPSA" | 
| 7  | "Daikin Industries, Ltd."                      | 
| 8  | "Elitegroup computer systems co., Ltd."        | 
| 9  | "Fuji Xerox Co., Ltd."                         | 
| 10 | "Gamesa Corporación Tecnológica, S.A."         | 

- Table 'countries'
  - id: Unique identifier for each country.
  - country_name: The name of the country.
```sql
SELECT
    *
FROM
    countries
LIMIT
    10;
```
| id | country_name | 
| -: | -----------: | 
| 1  | Australia    | 
| 2  | Belgium      | 
| 3  | Brazil       | 
| 4  | Canada       | 
| 5  | Chile        | 
| 6  | China        | 
| 7  | Colombia     | 
| 8  | Finland      | 
| 9  | France       | 
| 10 | Germany      | 

❓ Questions to research

- Which products contribute the most to carbon emissions?
  Top 10 products contribute the most to carbon emissions
```sql
SELECT 
    pe.product_name,
    c.company_name,
    co.country_name,
    ig.industry_group,
    pe.year,
    ROUND(pe.carbon_footprint_pcf, 2) as carbon_footprint_pcf,
    -- Add ranking
    DENSE_RANK() OVER (ORDER BY pe.carbon_footprint_pcf DESC) as emission_rank
FROM product_emissions pe
JOIN companies c ON pe.company_id = c.id
JOIN countries co ON pe.country_id = co.id
JOIN industry_groups ig ON pe.industry_group_id = ig.id
ORDER BY pe.carbon_footprint_pcf DESC
LIMIT 10;
```
| product_name                                                                                                                       | company_name                            | country_name | industry_group                     | year | carbon_footprint_pcf | emission_rank | 
| ---------------------------------------------------------------------------------------------------------------------------------: | --------------------------------------: | -----------: | ---------------------------------: | ---: | -------------------: | ------------: | 
| Wind Turbine G128 5 Megawats                                                                                                       | "Gamesa Corporación Tecnológica, S.A."  | Spain        | Electrical Equipment and Machinery | 2015 | 3718044              | 1             | 
| Wind Turbine G132 5 Megawats                                                                                                       | "Gamesa Corporación Tecnológica, S.A."  | Spain        | Electrical Equipment and Machinery | 2015 | 3276187              | 2             | 
| Wind Turbine G114 2 Megawats                                                                                                       | "Gamesa Corporación Tecnológica, S.A."  | Spain        | Electrical Equipment and Machinery | 2015 | 1532608              | 3             | 
| Wind Turbine G90 2 Megawats                                                                                                        | "Gamesa Corporación Tecnológica, S.A."  | Spain        | Electrical Equipment and Machinery | 2015 | 1251625              | 4             | 
| Land Cruiser Prado. FJ Cruiser. Dyna trucks. Toyoace.IMV def unit.                                                                 | "Hino Motors, Ltd."                     | Japan        | Automobiles & Components           | 2016 | 191687               | 5             | 
| Retaining wall structure with a main wall (sheet pile): 136 tonnes of steel sheet piles and 4 tonnes of tierods per 100 meter wall | Arcelor Mittal                          | Luxembourg   | Materials                          | 2013 | 167000               | 6             | 
| TCDE                                                                                                                               | "Mitsubishi Gas Chemical Company, Inc." | Japan        | Materials                          | 2017 | 99075                | 7             | 
| TCDE                                                                                                                               | "Mitsubishi Gas Chemical Company, Inc." | Japan        | Materials                          | 2017 | 99075                | 7             | 
| Mercedes-Benz GLE (GLE 500 4MATIC)                                                                                                 | Daimler AG                              | Germany      | Automobiles & Components           | 2016 | 91000                | 8             | 
| Electric Motor                                                                                                                     | Weg S/A                                 | Brazil       | Capital Goods                      | 2014 | 87589                | 9             | 
- What are the industry groups of these products?
```sql
WITH
  industry_stats AS (
    SELECT
      ig.industry_group,
      COUNT(*) as product_count,
      ROUND(AVG(pe.carbon_footprint_pcf), 2) as avg_carbon_footprint,
      ROUND(MIN(pe.carbon_footprint_pcf), 2) as min_carbon_footprint,
      ROUND(MAX(pe.carbon_footprint_pcf), 2) as max_carbon_footprint
    FROM
      product_emissions pe
      JOIN industry_groups ig ON pe.industry_group_id = ig.id
    GROUP BY
      ig.industry_group
  )
SELECT
  industry_group,
  product_count,
  avg_carbon_footprint,
  min_carbon_footprint,
  max_carbon_footprint,
  RANK() OVER (
    ORDER BY
      avg_carbon_footprint DESC
  ) as carbon_intensity_rank
FROM
  industry_stats
ORDER BY
  avg_carbon_footprint DESC;
```
| industry_group                                                         | product_count | avg_carbon_footprint | min_carbon_footprint | max_carbon_footprint | carbon_intensity_rank | 
| ---------------------------------------------------------------------: | ------------: | -------------------: | -------------------: | -------------------: | --------------------: | 
| Electrical Equipment and Machinery                                     | 11            | 891050.73            | 0                    | 3718044              | 1                     | 
| Automobiles & Components                                               | 73            | 35373.48             | 106                  | 191687               | 2                     | 
| "Pharmaceuticals, Biotechnology & Life Sciences"                       | 3             | 24162.00             | 15197                | 40215                | 3                     | 
| Capital Goods                                                          | 35            | 7391.77              | 0                    | 87589                | 4                     | 
| Materials                                                              | 180           | 3208.86              | 0                    | 167000               | 5                     | 
| "Mining - Iron, Aluminum, Other Metals"                                | 3             | 2727.00              | 2615                 | 2820                 | 6                     | 
| Energy                                                                 | 5             | 2154.80              | 0                    | 6109                 | 7                     | 
| Chemicals                                                              | 32            | 1949.03              | 0                    | 10245                | 8                     | 
| Media                                                                  | 15            | 1534.47              | 2                    | 9438                 | 9                     | 
| Software & Services                                                    | 34            | 1368.94              | 1                    | 7090                 | 10                    | 
| Technology Hardware & Equipment                                        | 267           | 1362.46              | 0                    | 16100                | 11                    | 
| Tires                                                                  | 2             | 1011.00              | 288                  | 1734                 | 12                    | 
| "Food, Beverage & Tobacco"                                             | 128           | 868.21               | 0                    | 26836                | 13                    | 
| "Forest and Paper Products - Forestry, Timber, Pulp and Paper, Rubber" | 13            | 685.31               | 210                  | 918                  | 14                    | 
| Containers & Packaging                                                 | 8             | 373.50               | 0                    | 964                  | 15                    | 
| Commercial & Professional Services                                     | 44            | 119.66               | 19                   | 380                  | 16                    | 
| "Consumer Durables, Household and Personal Products"                   | 8             | 116.38               | 26                   | 409                  | 17                    | 
| Consumer Durables & Apparel                                            | 68            | 107.49               | 7                    | 2344                 | 18                    | 
| Food & Staples Retailing                                               | 24            | 61.71                | 0                    | 603                  | 19                    | 
| Gas Utilities                                                          | 2             | 61.00                | 61                   | 61                   | 20                    | 
| Utilities                                                              | 4             | 61.00                | 61                   | 61                   | 20                    | 
| Telecommunication Services                                             | 9             | 46.44                | 5                    | 88                   | 22                    | 
| Trading Companies & Distributors and Commercial Services & Supplies    | 6             | 39.83                | 19                   | 90                   | 23                    | 
| "Textiles, Apparel, Footwear and Luxury Goods"                         | 27            | 14.33                | 8                    | 16                   | 24                    | 
| Semiconductors & Semiconductor Equipment                               | 5             | 10.80                | 2                    | 29                   | 25                    | 
| Food & Beverage Processing                                             | 20            | 7.05                 | 0                    | 130                  | 26                    | 
| Retailing                                                              | 5             | 6.00                 | 3                    | 8                    | 27                    | 
| Tobacco                                                                | 1             | 1.00                 | 1                    | 1                    | 28                    | 
| Semiconductors & Semiconductors Equipment                              | 3             | 1.00                 | 1                    | 1                    | 28                    | 
| Household & Personal Products                                          | 2             | 0.00                 | 0                    | 0                    | 30                    | 
- What are the industries with the highest contribution to carbon emissions?
```sql
WITH
  industry_emissions AS (
    SELECT
      ig.industry_group,
      COUNT(DISTINCT pe.id) as total_products,
      -- Carbon footprint metrics
      ROUND(AVG(pe.carbon_footprint_pcf), 2) as avg_carbon_footprint,
      ROUND(SUM(pe.carbon_footprint_pcf), 2) as total_carbon_footprint
    FROM
      product_emissions pe
      JOIN industry_groups ig ON pe.industry_group_id = ig.id
    GROUP BY
      ig.industry_group
  ),
  total_emissions AS (
    SELECT
      SUM(total_carbon_footprint) as overall_total
    FROM
      industry_emissions
  )
SELECT
  ie.industry_group,
  ie.total_products,
  ie.avg_carbon_footprint,
  ie.total_carbon_footprint,
  ROUND(
    (ie.total_carbon_footprint / te.overall_total * 100),
    2
  ) as percentage_of_total_emissions,
  RANK() OVER (
    ORDER BY
      ie.total_carbon_footprint DESC
  ) as emission_rank
FROM
  industry_emissions ie
  CROSS JOIN total_emissions te
ORDER BY
  ie.total_carbon_footprint DESC;
```
| industry_group                                                         | total_products | avg_carbon_footprint | total_carbon_footprint | percentage_of_total_emissions | emission_rank | 
| ---------------------------------------------------------------------: | -------------: | -------------------: | ---------------------: | ----------------------------: | ------------: | 
| Electrical Equipment and Machinery                                     | 11             | 891050.73            | 9801558.00             | 70.27                         | 1             | 
| Automobiles & Components                                               | 73             | 35373.48             | 2582264.00             | 18.51                         | 2             | 
| Materials                                                              | 161            | 3208.86              | 577595.00              | 4.14                          | 3             | 
| Technology Hardware & Equipment                                        | 195            | 1362.46              | 363776.00              | 2.61                          | 4             | 
| Capital Goods                                                          | 33             | 7391.77              | 258712.00              | 1.85                          | 5             | 
| "Food, Beverage & Tobacco"                                             | 101            | 868.21               | 111131.00              | 0.80                          | 6             | 
| "Pharmaceuticals, Biotechnology & Life Sciences"                       | 3              | 24162.00             | 72486.00               | 0.52                          | 7             | 
| Chemicals                                                              | 29             | 1949.03              | 62369.00               | 0.45                          | 8             | 
| Software & Services                                                    | 27             | 1368.94              | 46544.00               | 0.33                          | 9             | 
| Media                                                                  | 15             | 1534.47              | 23017.00               | 0.17                          | 10            | 
| Energy                                                                 | 5              | 2154.80              | 10774.00               | 0.08                          | 11            | 
| "Forest and Paper Products - Forestry, Timber, Pulp and Paper, Rubber" | 13             | 685.31               | 8909.00                | 0.06                          | 12            | 
| "Mining - Iron, Aluminum, Other Metals"                                | 3              | 2727.00              | 8181.00                | 0.06                          | 13            | 
| Consumer Durables & Apparel                                            | 52             | 107.49               | 7309.00                | 0.05                          | 14            | 
| Commercial & Professional Services                                     | 42             | 119.66               | 5265.00                | 0.04                          | 15            | 
| Containers & Packaging                                                 | 8              | 373.50               | 2988.00                | 0.02                          | 16            | 
| Tires                                                                  | 2              | 1011.00              | 2022.00                | 0.01                          | 17            | 
| Food & Staples Retailing                                               | 24             | 61.71                | 1481.00                | 0.01                          | 18            | 
| "Consumer Durables, Household and Personal Products"                   | 8              | 116.38               | 931.00                 | 0.01                          | 19            | 
| Telecommunication Services                                             | 9              | 46.44                | 418.00                 | 0.00                          | 20            | 
| "Textiles, Apparel, Footwear and Luxury Goods"                         | 16             | 14.33                | 387.00                 | 0.00                          | 21            | 
| Utilities                                                              | 2              | 61.00                | 244.00                 | 0.00                          | 22            | 
| Trading Companies & Distributors and Commercial Services & Supplies    | 6              | 39.83                | 239.00                 | 0.00                          | 23            | 
| Food & Beverage Processing                                             | 13             | 7.05                 | 141.00                 | 0.00                          | 24            | 
| Gas Utilities                                                          | 1              | 61.00                | 122.00                 | 0.00                          | 25            | 
| Semiconductors & Semiconductor Equipment                               | 4              | 10.80                | 54.00                  | 0.00                          | 26            | 
| Retailing                                                              | 4              | 6.00                 | 30.00                  | 0.00                          | 27            | 
| Semiconductors & Semiconductors Equipment                              | 3              | 1.00                 | 3.00                   | 0.00                          | 28            | 
| Tobacco                                                                | 1              | 1.00                 | 1.00                   | 0.00                          | 29            | 
| Household & Personal Products                                          | 2              | 0.00                 | 0.00                   | 0.00                          | 30            | 

- What are the companies with the highest contribution to carbon emissions?
```sql
WITH
  company_emissions AS (
    SELECT
      c.company_name,
      ig.industry_group,
      COUNT(DISTINCT pe.id) as total_products,
      -- Carbon footprint metrics
      ROUND(AVG(pe.carbon_footprint_pcf), 2) as avg_carbon_footprint,
      ROUND(SUM(pe.carbon_footprint_pcf), 2) as total_carbon_footprint
    FROM
      product_emissions pe
      JOIN companies c ON pe.company_id = c.id
      JOIN industry_groups ig ON pe.industry_group_id = ig.id
    GROUP BY
      c.company_name,
      ig.industry_group
  ),
  total_emissions AS (
    SELECT
      SUM(total_carbon_footprint) as overall_total
    FROM
      company_emissions
  )
SELECT
  ce.company_name,
  ce.industry_group,
  ce.total_products,
  ce.avg_carbon_footprint,
  ce.total_carbon_footprint,
  ROUND(
    (ce.total_carbon_footprint / te.overall_total * 100),
    2
  ) as percentage_of_total_emissions,
  RANK() OVER (
    ORDER BY
      ce.total_carbon_footprint DESC
  ) as emission_rank
FROM
  company_emissions ce
  CROSS JOIN total_emissions te
ORDER BY
  ce.total_carbon_footprint DESC
LIMIT
  20;
```
| company_name                            | industry_group                                   | total_products | avg_carbon_footprint | total_carbon_footprint | percentage_of_total_emissions | emission_rank | 
| --------------------------------------: | -----------------------------------------------: | -------------: | -------------------: | ---------------------: | ----------------------------: | ------------: | 
| "Gamesa Corporación Tecnológica, S.A."  | Electrical Equipment and Machinery               | 4              | 2444616.00           | 9778464.00             | 70.10                         | 1             | 
| Daimler AG                              | Automobiles & Components                         | 37             | 43089.19             | 1594300.00             | 11.43                         | 2             | 
| Volkswagen AG                           | Automobiles & Components                         | 25             | 26238.40             | 655960.00              | 4.70                          | 3             | 
| "Mitsubishi Gas Chemical Company, Inc." | Materials                                        | 8              | 13251.00             | 212016.00              | 1.52                          | 4             | 
| "Hino Motors, Ltd."                     | Automobiles & Components                         | 1              | 191687.00            | 191687.00              | 1.37                          | 5             | 
| Arcelor Mittal                          | Materials                                        | 2              | 83503.50             | 167007.00              | 1.20                          | 6             | 
| Weg S/A                                 | Capital Goods                                    | 2              | 70323.50             | 140647.00              | 1.01                          | 7             | 
| General Motors Company                  | Automobiles & Components                         | 4              | 34251.75             | 137007.00              | 0.98                          | 8             | 
| "Lexmark International, Inc."           | Technology Hardware & Equipment                  | 29             | 2276.07              | 132012.00              | 0.95                          | 9             | 
| "Daikin Industries, Ltd."               | Capital Goods                                    | 6              | 17600.00             | 105600.00              | 0.76                          | 10            | 
| CJ Cheiljedang                          | "Food, Beverage & Tobacco"                       | 6              | 15802.83             | 94817.00               | 0.68                          | 11            | 
| Waters Corporation                      | "Pharmaceuticals, Biotechnology & Life Sciences" | 3              | 24162.00             | 72486.00               | 0.52                          | 12            | 
| Quanta Computer                         | Technology Hardware & Equipment                  | 21             | 2772.24              | 58217.00               | 0.42                          | 13            | 
| LG Chem Ltd                             | Materials                                        | 7              | 4076.14              | 57066.00               | 0.41                          | 14            | 
| Akzo Nobel                              | Materials                                        | 28             | 1684.54              | 47167.00               | 0.34                          | 15            | 
| Xerox Corporation                       | Software & Services                              | 18             | 2538.44              | 45692.00               | 0.33                          | 16            | 
| "Ricoh Co., Ltd."                       | Technology Hardware & Equipment                  | 10             | 3550.50              | 35505.00               | 0.25                          | 17            | 
| LG Chem Ltd                             | Chemicals                                        | 3              | 5810.00              | 34860.00               | 0.25                          | 18            | 
| Xerox Corporation                       | Technology Hardware & Equipment                  | 9              | 2928.78              | 26359.00               | 0.19                          | 19            | 
| NEC Corporation                         | Technology Hardware & Equipment                  | 3              | 3976.33              | 23858.00               | 0.17                          | 20            | 

- What are the countries with the highest contribution to carbon emissions?
```sql
WITH
  country_emissions AS (
    SELECT
      co.country_name,
      COUNT(DISTINCT pe.id) as total_products,
      COUNT(DISTINCT c.id) as total_companies,
      COUNT(DISTINCT ig.id) as total_industries,
      -- Carbon footprint metrics
      ROUND(AVG(pe.carbon_footprint_pcf), 2) as avg_carbon_footprint,
      ROUND(SUM(pe.carbon_footprint_pcf), 2) as total_carbon_footprint
    FROM
      product_emissions pe
      JOIN countries co ON pe.country_id = co.id
      JOIN companies c ON pe.company_id = c.id
      JOIN industry_groups ig ON pe.industry_group_id = ig.id
    GROUP BY
      co.country_name
  ),
  total_emissions AS (
    SELECT
      SUM(total_carbon_footprint) as overall_total
    FROM
      country_emissions
  )
SELECT
  ce.country_name,
  ce.total_products,
  ce.total_companies,
  ce.total_industries,
  ce.avg_carbon_footprint,
  ce.total_carbon_footprint,
  ROUND(
    (ce.total_carbon_footprint / te.overall_total * 100),
    2
  ) as percentage_of_total_emissions,
  RANK() OVER (
    ORDER BY
      ce.total_carbon_footprint DESC
  ) as emission_rank
FROM
  country_emissions ce
  CROSS JOIN total_emissions te
ORDER BY
  ce.total_carbon_footprint DESC;
```
| country_name   | total_products | total_companies | total_industries | avg_carbon_footprint | total_carbon_footprint | percentage_of_total_emissions | emission_rank | 
| -------------: | -------------: | --------------: | ---------------: | -------------------: | ---------------------: | ----------------------------: | ------------: | 
| Spain          | 13             | 5               | 5                | 699009.29            | 9786130.00             | 70.16                         | 1             | 
| Germany        | 67             | 5               | 2                | 33600.37             | 2251225.00             | 16.14                         | 2             | 
| Japan          | 110            | 21              | 13               | 4600.26              | 653237.00              | 4.68                          | 3             | 
| USA            | 305            | 39              | 19               | 1332.60              | 518381.00              | 3.72                          | 4             | 
| South Korea    | 22             | 6               | 6                | 5665.61              | 186965.00              | 1.34                          | 5             | 
| Brazil         | 17             | 4               | 5                | 9407.61              | 169337.00              | 1.21                          | 6             | 
| Luxembourg     | 2              | 1               | 1                | 83503.50             | 167007.00              | 1.20                          | 7             | 
| Netherlands    | 35             | 1               | 2                | 2011.91              | 70417.00               | 0.50                          | 8             | 
| Taiwan         | 60             | 13              | 3                | 806.09               | 62875.00               | 0.45                          | 9             | 
| India          | 16             | 2               | 3                | 1535.88              | 24574.00               | 0.18                          | 10            | 
| Finland        | 35             | 2               | 3                | 554.59               | 21629.00               | 0.16                          | 11            | 
| South Africa   | 11             | 3               | 3                | 1119.27              | 12312.00               | 0.09                          | 12            | 
| United Kingdom | 32             | 8               | 6                | 243.92               | 9025.00                | 0.06                          | 13            | 
| Ireland        | 6              | 1               | 2                | 855.00               | 5130.00                | 0.04                          | 14            | 
| Sweden         | 26             | 5               | 6                | 174.35               | 4533.00                | 0.03                          | 15            | 
| France         | 20             | 7               | 8                | 129.29               | 2715.00                | 0.02                          | 16            | 
| Chile          | 3              | 1               | 2                | 518.33               | 1555.00                | 0.01                          | 17            | 
| Indonesia      | 1              | 1               | 1                | 721.00               | 721.00                 | 0.01                          | 18            | 
| Canada         | 6              | 1               | 2                | 63.67                | 382.00                 | 0.00                          | 19            | 
| Australia      | 6              | 1               | 1                | 39.83                | 239.00                 | 0.00                          | 20            | 
| Malaysia       | 4              | 1               | 1                | 58.75                | 235.00                 | 0.00                          | 21            | 
| China          | 6              | 4               | 4                | 19.63                | 157.00                 | 0.00                          | 22            | 
| Switzerland    | 28             | 6               | 6                | 3.58                 | 143.00                 | 0.00                          | 23            | 
| Italy          | 23             | 3               | 2                | 0.78                 | 18.00                  | 0.00                          | 24            | 
| Belgium        | 8              | 1               | 2                | 1.00                 | 8.00                   | 0.00                          | 25            | 
| Greece         | 1              | 1               | 1                | 1.00                 | 1.00                   | 0.00                          | 26            | 
| Lithuania      | 1              | 1               | 1                | 0.00                 | 0.00                   | 0.00                          | 27            | 
| Colombia       | 2              | 1               | 1                | 0.00                 | 0.00                   | 0.00                          | 27            | 

- What is the trend of carbon footprints (PCFs) over the years?
```sql
WITH
  yearly_stats AS (
    SELECT
      pe.year,
      -- General statistics
      COUNT(DISTINCT pe.id) as total_products,
      COUNT(DISTINCT pe.company_id) as total_companies,
      COUNT(DISTINCT pe.industry_group_id) as total_industries,
      -- Carbon footprint metrics
      ROUND(AVG(pe.carbon_footprint_pcf), 2) as avg_carbon_footprint,
      ROUND(MIN(pe.carbon_footprint_pcf), 2) as min_carbon_footprint,
      ROUND(MAX(pe.carbon_footprint_pcf), 2) as max_carbon_footprint
    FROM
      product_emissions pe
    GROUP BY
      pe.year
  ),
  year_over_year_change AS (
    SELECT
      year,
      total_products,
      total_companies,
      total_industries,
      avg_carbon_footprint,
      min_carbon_footprint,
      max_carbon_footprint,
      -- Calculate year-over-year changes
      ROUND(
        (
          (
            avg_carbon_footprint - LAG(avg_carbon_footprint) OVER (
              ORDER BY
                year
            )
          ) / LAG(avg_carbon_footprint) OVER (
            ORDER BY
              year
          ) * 100
        ),
        2
      ) as pcf_change_percent
    FROM
      yearly_stats
  )
SELECT
  year,
  total_products,
  total_companies,
  total_industries,
  avg_carbon_footprint,
  min_carbon_footprint,
  max_carbon_footprint,
  pcf_change_percent
FROM
  year_over_year_change
ORDER BY
  year;
```
| year | total_products | total_companies | total_industries | avg_carbon_footprint | min_carbon_footprint | max_carbon_footprint | pcf_change_percent | 
| ---: | -------------: | --------------: | ---------------: | -------------------: | -------------------: | -------------------: | -----------------: | 
| 2013 | 179            | 72              | 14               | 2399.32              | 0                    | 167000               | [NULL]             | 
| 2014 | 190            | 68              | 14               | 2457.58              | 0                    | 87589                | 2.43               | 
| 2015 | 217            | 64              | 22               | 43188.90             | 0                    | 3718044              | 1657.38            | 
| 2016 | 218            | 55              | 13               | 6891.52              | 0                    | 191687               | -84.04             | 
| 2017 | 62             | 12              | 6                | 4050.85              | 0                    | 99075                | -41.22             | 

- Which industry groups has demonstrated the most notable decrease in carbon footprints (PCFs) over time?
```sql
WITH
    yearly_averages AS (
        SELECT
            ig.industry_group,
            pe.year,
            AVG(pe.carbon_footprint_pcf) AS avg_carbon_footprint,
            COUNT(*) AS product_count
        FROM
            product_emissions pe
            JOIN industry_groups ig ON pe.industry_group_id = ig.id
        GROUP BY
            ig.industry_group,
            pe.year
    ),
    year_over_year_change AS (
        SELECT
            industry_group,
            year,
            avg_carbon_footprint,
            product_count,
            LAG(avg_carbon_footprint) OVER (
                PARTITION BY industry_group
                ORDER BY
                    year
            ) AS prev_year_footprint,
            (
                (
                    avg_carbon_footprint - LAG(avg_carbon_footprint) OVER (
                        PARTITION BY industry_group
                        ORDER BY
                            year
                    )
                ) / LAG(avg_carbon_footprint) OVER (
                    PARTITION BY industry_group
                    ORDER BY
                        year
                ) * 100
            ) AS percentage_change
        FROM
            yearly_averages
    )
SELECT
    industry_group,
    year,
    ROUND(avg_carbon_footprint, 2) AS avg_carbon_footprint,
    product_count,
    ROUND(percentage_change, 2) AS year_over_year_change_percent
FROM
    year_over_year_change
WHERE
    percentage_change IS NOT NULL
    AND product_count >= 5 -- Filter for industries with significant sample size
ORDER BY
    percentage_change ASC,
    year DESC;
```
| industry_group                     | year | avg_carbon_footprint | product_count | year_over_year_change_percent | 
| ---------------------------------: | ---: | -------------------: | ------------: | ----------------------------: | 
| Technology Hardware & Equipment    | 2016 | 65.25                | 24            | -96.56                        | 
| "Food, Beverage & Tobacco"         | 2017 | 143.73               | 22            | -96.42                        | 
| Capital Goods                      | 2016 | 796.13               | 8             | -77.29                        | 
| Consumer Durables & Apparel        | 2016 | 40.07                | 29            | -64.57                        | 
| Materials                          | 2014 | 1513.56              | 50            | -63.77                        | 
| Consumer Durables & Apparel        | 2014 | 113.10               | 29            | -60.55                        | 
| Automobiles & Components           | 2014 | 20910.45             | 11            | -19.69                        | 
| Commercial & Professional Services | 2016 | 96.33                | 30            | -19.22                        | 
| Food & Staples Retailing           | 2015 | 70.60                | 10            | -8.67                         | 
| Materials                          | 2016 | 1401.06              | 63            | -7.43                         | 
| "Food, Beverage & Tobacco"         | 2014 | 99.44                | 27            | 5.52                          | 
| Technology Hardware & Equipment    | 2015 | 1895.66              | 56            | 6.47                          | 
| Automobiles & Components           | 2016 | 40138.09             | 35            | 8.05                          | 
| Software & Services                | 2016 | 2538.44              | 9             | 66.59                         | 
| Technology Hardware & Equipment    | 2014 | 1780.44              | 94            | 69.01                         | 
| Automobiles & Components           | 2015 | 37146.68             | 22            | 77.65                         | 
| Capital Goods                      | 2014 | 10411.00             | 9             | 107.56                        | 
| Materials                          | 2017 | 11217.74             | 19            | 700.66                        | 
| Technology Hardware & Equipment    | 2017 | 788.34               | 35            | 1108.19                       | 
| Software & Services                | 2014 | 29.20                | 5             | 1846.67                       | 
| Capital Goods                      | 2017 | 18989.80             | 5             | 2285.28                       | 
| Software & Services                | 2015 | 1523.73              | 15            | 5118.26                       |
