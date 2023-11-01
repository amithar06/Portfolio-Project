# Portfolio-Project
This repository provides comprehensive data and SQL queries for in-depth analysis of every COVID-19-related death during it's peak.
<br>

## Key Questions and Analysis Goals

Here are some of the questions this project aims to analyze COVID-19 data and answer the following key questions:

- What is the likelihood of dying if you contract COVID-19 in a given country? 
- Which countries have the highest COVID-19 infection rates relative to their populations? 
- Which countries have seen the most COVID-19 deaths adjusted for population size? 
- What percentage of the population in each country has received at least one COVID-19 vaccine dose? 
<br>
**When executing the provided SQL queries, you can expect the following results:-**


Shows likelihood of dying if you contract covid in your country

Select Location, date, total_cases,total_deaths, (total_deaths/total_cases)*100 as DeathPercentage
From PortfolioProject..CovidDeaths
Where location like '%states%'
and continent is not null 
order by 1,2
output screenshots/dying probability.png
