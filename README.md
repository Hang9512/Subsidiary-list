#Subsidiary - list

[Project description and purpose]

There are a total of three documents. 
- Document one pertains to public companies, named “Public Company”
- Document two to private companies, named “Private Company”
- For ease of reference, I have consolidated public and private company information into a single comprehensive document, named “Public and Private Company”


## Table of Contents

- [About](#about)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
- [Checking result](#Checking-result)
  - [Stata code](#Stata-code)

## About

Using `Stata 17.0` to check the possible duplicated observations.

Introduction of the variables:
In the table:
- first column is the `Company Name`, representing the parent companies within the United States 
- second column comprises `Exchange Tickers` 
- third column indicates the `Company Type`, categorized as either a public or private company 
- fourth column displays the `Location of the Parent Company`, specifically within the United States 
- fifth column provides information on the `Location and Names of Direct Subsidiaries operating outside the United States `
- sixth column denotes the `Company Status`


## Getting Started

### Prerequisites

Stata 17.0

## Checking result

### Stata code

```Stata

encode CompanyName, gen(CN)
encode CompanyStatus, gen(CS)
encode CompanyType, gen(CT)
encode CountryRegionofIncorporation, gen(Region)
encode ExchangeTicker, gen(Ticker)
encode GeographicLocationsCurrentDi, gen(SubRegion)
duplicates list Ticker SubRegion Region CT CS CN

```
Result:
Duplicates in terms of Ticker SubRegion Region CT CS CN
(0 observations are duplicates)

This result means all these six observations being uniquely identified.


