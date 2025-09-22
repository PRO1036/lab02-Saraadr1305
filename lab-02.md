Lab 02 - Plastic waste
================
Sara Adraoui
22/09/25

## Chargement des packages et des données

``` r
library(tidyverse) 
```

``` r
plastic_waste <- read_csv("data/plastic-waste.csv")
```

Commençons par filtrer les données pour retirer le point représenté par
Trinité et Tobago (TTO) qui est un outlier.

``` r
plastic_waste <- plastic_waste %>%
  filter(plastic_waste_per_cap < 3.5)
```

## Exercices

### Exercise 1

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = continent,
                     y = plastic_waste_per_cap)) +
  geom_boxplot(fill = "lightblue") +
  labs(
    title = "Déchets plastiques par habitant",
    subtitle = "Comparaison par continent",
    x = "Continent",
    y = "kg par habitant",
    caption = "Source : Plastic Waste dataset"
  )
```

![](lab-02_files/figure-gfm/plastic-waste-continent-1.png)<!-- -->



    ### Exercise 2

    ``` r
    ggplot(data = plastic_waste,
           mapping = aes(x = plastic_waste_per_cap)) +
      geom_density(fill = "lightblue", alpha = 0.7) +
      labs(
        title = "Distribution des déchets plastiques par habitant",
        subtitle = "Tous les pays (année disponible)",
        x = "Déchets plastiques par habitant (kg)",
        y = "Densité")

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- -->

Réponse à la question…

### Exercise 3

Boxplot:

``` r
# insert code here
```

Violin plot:

``` r
# insert code here
```

Réponse à la question…

### Exercise 4

``` r
# insert code here
```

Réponse à la question…

### Exercise 5

``` r
# insert code here
```

``` r
# insert code here
```

Réponse à la question…

## Conclusion

Recréez la visualisation:

``` r
# insert code here
```
