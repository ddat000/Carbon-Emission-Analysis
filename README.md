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
SELECT *
FROM product_emissions
LIMIT 10;
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
SELECT *
FROM industry_groups
LIMIT 10;
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
SELECT *
FROM companies
LIMIT 10;
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
SELECT *
FROM countries
LIMIT 10;
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
 product_name,
 SUM(carbon_footprint_pcf) AS total_emissions
FROM
 product_emissions 
GROUP BY
 product_name
ORDER BY
 total_emissions DESC
LIMIT 10;
```
| product_name                                                                                                                       | total_emissions | 
| ---------------------------------------------------------------------------------------------------------------------------------: | --------------: | 
| Wind Turbine G128 5 Megawats                                                                                                       | 3718044         | 
| Wind Turbine G132 5 Megawats                                                                                                       | 3276187         | 
| Wind Turbine G114 2 Megawats                                                                                                       | 1532608         | 
| Wind Turbine G90 2 Megawats                                                                                                        | 1251625         | 
| TCDE                                                                                                                               | 198150          | 
| Land Cruiser Prado. FJ Cruiser. Dyna trucks. Toyoace.IMV def unit.                                                                 | 191687          | 
| Retaining wall structure with a main wall (sheet pile): 136 tonnes of steel sheet piles and 4 tonnes of tierods per 100 meter wall | 167000          | 
| Electric Motor                                                                                                                     | 160655          | 
| Audi A6                                                                                                                            | 111282          | 
| Average of all GM vehicles produced and used in the 10 year life-cycle.                                                            | 100621          | 

- What are the industry groups of these products?
```sql
SELECT 
	p_e.product_name,
	SUM(p_e.carbon_footprint_pcf) AS total_emissions,
	i_g.industry_group
FROM
	product_emissions p_e
	LEFT JOIN industry_groups i_g
	ON p_e.industry_group_id = i_g.id
GROUP BY
 p_e.product_name
ORDER BY
 total_emissions DESC
LIMIT 10;
```
| product_name                                                                                                                       | total_emissions | industry_group                     | 
| ---------------------------------------------------------------------------------------------------------------------------------: | --------------: | ---------------------------------: | 
| Wind Turbine G128 5 Megawats                                                                                                       | 3718044         | Electrical Equipment and Machinery | 
| Wind Turbine G132 5 Megawats                                                                                                       | 3276187         | Electrical Equipment and Machinery | 
| Wind Turbine G114 2 Megawats                                                                                                       | 1532608         | Electrical Equipment and Machinery | 
| Wind Turbine G90 2 Megawats                                                                                                        | 1251625         | Electrical Equipment and Machinery | 
| TCDE                                                                                                                               | 198150          | Materials                          | 
| Land Cruiser Prado. FJ Cruiser. Dyna trucks. Toyoace.IMV def unit.                                                                 | 191687          | Automobiles & Components           | 
| Retaining wall structure with a main wall (sheet pile): 136 tonnes of steel sheet piles and 4 tonnes of tierods per 100 meter wall | 167000          | Materials                          | 
| Electric Motor                                                                                                                     | 160655          | Capital Goods                      | 
| Audi A6                                                                                                                            | 111282          | Automobiles & Components           | 
| Average of all GM vehicles produced and used in the 10 year life-cycle.                                                            | 100621          | Automobiles & Components           | 

- What are the industries with the highest contribution to carbon emissions?
```sql
SELECT 
	i_g.industry_group,
	SUM(p_e.carbon_footprint_pcf) AS total_emissions
FROM
	product_emissions p_e
	LEFT JOIN industry_groups i_g
		ON p_e.industry_group_id = i_g.id
GROUP BY 
	i_g.industry_group
ORDER BY 
	total_emissions DESC
LIMIT 10;
```
| industry_group                                   | total_emissions | 
| -----------------------------------------------: | --------------: | 
| Electrical Equipment and Machinery               | 9801558         | 
| Automobiles & Components                         | 2582264         | 
| Materials                                        | 577595          | 
| Technology Hardware & Equipment                  | 363776          | 
| Capital Goods                                    | 258712          | 
| "Food, Beverage & Tobacco"                       | 111131          | 
| "Pharmaceuticals, Biotechnology & Life Sciences" | 72486           | 
| Chemicals                                        | 62369           | 
| Software & Services                              | 46544           | 
| Media                                            | 23017           | 

- What are the companies with the highest contribution to carbon emissions?
```sql
SELECT 
	companies.company_name,
	SUM(p_e.carbon_footprint_pcf) AS total_emissions
FROM
	product_emissions p_e
	LEFT JOIN companies
		ON p_e.company_id = companies.id
GROUP BY 
	companies.company_name
ORDER BY 
	total_emissions DESC
LIMIT 10;
```
| company_name                            | total_emissions | 
| --------------------------------------: | --------------: | 
| "Gamesa Corporación Tecnológica, S.A."  | 9778464         | 
| Daimler AG                              | 1594300         | 
| Volkswagen AG                           | 655960          | 
| "Mitsubishi Gas Chemical Company, Inc." | 212016          | 
| "Hino Motors, Ltd."                     | 191687          | 
| Arcelor Mittal                          | 167007          | 
| Weg S/A                                 | 160655          | 
| General Motors Company                  | 137007          | 
| "Lexmark International, Inc."           | 132012          | 
| "Daikin Industries, Ltd."               | 105600          | 

- What are the countries with the highest contribution to carbon emissions?
```sql
SELECT 
	countries.country_name,
	SUM(p_e.carbon_footprint_pcf) AS total_emissions
FROM
	product_emissions p_e
	LEFT JOIN countries
		ON p_e.country_id = countries.id
GROUP BY 
	countries.country_name
ORDER BY 
	total_emissions DESC
LIMIT 10;
```
| country_name | total_emissions | 
| -----------: | --------------: | 
| Spain        | 9786130         | 
| Germany      | 2251225         | 
| Japan        | 653237          | 
| USA          | 518381          | 
| South Korea  | 186965          | 
| Brazil       | 169337          | 
| Luxembourg   | 167007          | 
| Netherlands  | 70417           | 
| Taiwan       | 62875           | 
| India        | 24574           | 

- What is the trend of carbon footprints (PCFs) over the years?
```sql
SELECT 
	year,
	SUM(carbon_footprint_pcf) AS total_emissions
FROM 
	product_emissions 
GROUP BY 
	year
ORDER BY 
	year ASC;
```
| year | total_emissions | 
| ---: | --------------: | 
| 2013 | 503857          | 
| 2014 | 624226          | 
| 2015 | 10840415        | 
| 2016 | 1640182         | 
| 2017 | 340271          | 

- Which industry groups has demonstrated the most notable decrease in carbon footprints (PCFs) over time?
```sql
WITH yearly_averages AS (
  SELECT 
    ig.industry_group,
    pe.year,
    AVG(pe.carbon_footprint_pcf) as avg_carbon_footprint,
    COUNT(*) as product_count
  FROM product_emissions pe
  JOIN industry_groups ig ON pe.industry_group_id = ig.id
  GROUP BY ig.industry_group, pe.year
),
year_over_year_change AS (
  SELECT 
    industry_group,
    year,
    avg_carbon_footprint,
    product_count,
    LAG(avg_carbon_footprint) OVER (PARTITION BY industry_group ORDER BY year) as prev_year_footprint,
    ((avg_carbon_footprint - LAG(avg_carbon_footprint) OVER (PARTITION BY industry_group ORDER BY year)) / 
     LAG(avg_carbon_footprint) OVER (PARTITION BY industry_group ORDER BY year) * 100) as percentage_change
  FROM yearly_averages
)
SELECT 
  industry_group,
  year,
  ROUND(avg_carbon_footprint, 2) as avg_carbon_footprint,
  product_count,
  ROUND(percentage_change, 2) as year_over_year_change_percent
FROM year_over_year_change
WHERE percentage_change IS NOT NULL
  AND product_count >= 5  -- Filter for industries with significant sample size
ORDER BY percentage_change ASC, year DESC;
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
