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
# When executing the provided SQL queries you can expect the following results
<br>
<br>

![dying probability](https://github.com/amithar06/Portfolio-Project/assets/132035144/baadbb3f-467a-4524-bd5c-77019dce4bf0)

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


<br>
<br>
<br>

![highest infection rate](https://github.com/amithar06/Portfolio-Project/assets/132035144/50f2abe3-bcc6-452d-bb6c-7d709fb34716)
<br>

Countries with Highest Infection Rate compared to Population
<br>
Select Location, Population, MAX(total_cases) as HighestInfectionCount,  Max((total_cases/population))*100 as PercentPopulationInfected <br>
From PortfolioProject..CovidDeaths <br>
--Where location like '%states%' <br>
Group by Location, Population <br>
order by PercentPopulationInfected desc

<br> <br> <br> <br> 
![most deaths by population](https://github.com/amithar06/Portfolio-Project/assets/132035144/6408de6d-7b2c-490e-a837-11f63620c61e)
<br>
Countries with Highest Death Count per Population <br>

Select Location, MAX(cast(Total_deaths as int)) as TotalDeathCount <br>
From PortfolioProject..CovidDeaths <br>
--Where location like '%states%' <br>
Where continent is not null  <br>
Group by Location <br>
order by TotalDeathCount desc 
<br> <br> <br> <br> 
![recieved at least one Covid Vaccine](https://github.com/amithar06/Portfolio-Project/assets/132035144/bdb26cc0-2fd6-48fe-8ae0-50471fef6e7f)
<br> 
Shows Percentage of Population that has recieved at least one Covid Vaccine

Select dea.continent, dea.location, dea.date, dea.population, vac.new_vaccinations
, SUM(CONVERT(int,vac.new_vaccinations)) OVER (Partition by dea.Location Order by dea.location, dea.Date) as RollingPeopleVaccinated
--, (RollingPeopleVaccinated/population)*100 <br> 
From PortfolioProject..CovidDeaths dea <br> 
Join PortfolioProject..CovidVaccinations vac <br> 
	On dea.location = vac.location <br> 
	and dea.date = vac.date <br> 
where dea.continent is not null <br>  
order by 2,3 

