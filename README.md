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
<br>
## When executing the provided SQL queries you can expect the following results:-
<br>
<br>


Shows likelihood of dying if you contract covid in your country
<br>
Select Location, date, total_cases,total_deaths, (total_deaths/total_cases)*100 as DeathPercentage
<br>
From PortfolioProject..CovidDeaths
<br>
Where location like '%states%'
<br>
and continent is not null 
<br>
order by 1,2
<br>
![dying probability](https://github.com/amithar06/Portfolio-Project/assets/132035144/baadbb3f-467a-4524-bd5c-77019dce4bf0)

