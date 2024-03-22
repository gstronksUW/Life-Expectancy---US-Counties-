With X as (
select "County" , "Life Expectancy", avg("Life Expectancy") AS Average from public.us_life_expectancy 
  group by "County", "Life Expectancy"
  LIMIT 100)


Select "County", "Life Expectancy", (Select avg("Life Expectancy") from us_life_expectancy)  from X
group by "County" , Average, "Life Expectancy"
  Having Average < (Select avg("Life Expectancy") from us_life_expectancy) 
  order by "Life Expectancy" asc
;
