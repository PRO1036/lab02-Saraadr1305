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



    ### Exercise 2

    ``` r
    ggplot(data = plastic_waste,
           mapping = aes(x = plastic_waste_per_cap)) +
      geom_density(fill = "lightblue", alpha = 0.7) +
      labs(
        title = "Distribution des déchets plastiques par habitant",
        x = "Déchets plastiques par habitant (kg)",
        y = "Densité")

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- -->

Réponse à la question…

### Exercise 3

Boxplot:

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
  )
```

![](lab-02_files/figure-gfm/plastic-waste-boxplot-1.png)<!-- -->


    Violin plot:


    ``` r
    ggplot(data = plastic_waste,
           mapping = aes(x = continent,
                         y = plastic_waste_per_cap)) +
      geom_violin(fill = "lightgreen", alpha = 0.7) +
      labs(
        title = "Déchets plastiques par habitant",
        subtitle = "Distribution par continent",
        x = "Continent",
        y = "kg par habitant"
      )

![](lab-02_files/figure-gfm/plastic-waste-violin-1.png)<!-- -->

Réponse à la question…

### Exercise 4

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = plastic_waste_per_cap,
                     y = mismanaged_plastic_waste_per_cap,
                     colour = continent)) +
  geom_point(alpha = 0.7, size = 2) +
  labs(
    title = "Déchets plastiques générés vs mal gérés",
    subtitle = "Par pays",
    x = "Déchets plastiques par habitant (kg)",
    y = "Déchets plastiques mal gérés par habitant (kg)",
    colour = "Continent"
  )
```

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-1.png)<!-- -->

Réponse à la question…

### Exercise 5

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = total_pop,
                     y = plastic_waste_per_cap,
                     colour = continent)) +
  geom_point(alpha = 0.7, size = 2) +
  labs(
    title = "Population totale et déchets plastiques par habitant",
    x = "Population totale",
    y = "Déchets plastiques par habitant (kg)",
    colour = "Continent"
  )
```

    ## Warning: Removed 10 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-population-total-1.png)<!-- -->

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = coastal_pop,
                     y = plastic_waste_per_cap,
                     colour = continent)) +
  geom_point(alpha = 0.7, size = 2) +
  labs(
    title = "Population côtière et déchets plastiques par habitant",
    x = "Population côtière",
    y = "Déchets plastiques par habitant (kg)",
    colour = "Continent"
  )
```

![](lab-02_files/figure-gfm/plastic-waste-population-coastal-1.png)<!-- -->

Réponse à la question…

## Conclusion

Recréez la visualisation:

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = coastal_pop,
                     y = plastic_waste_per_cap,
                     colour = continent,
                     size = total_pop)) +
  geom_point(alpha = 0.7) +
  labs(
    title = "Population côtière et déchets plastiques par habitant",
    subtitle = "Chaque point représente un pays",
    x = "Population côtière",
    y = "Déchets plastiques par habitant (kg)",
    colour = "Continent",
    size = "Population totale"
  )
```

    ## Warning: Removed 10 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](lab-02_files/figure-gfm/recreate-viz-1.png)<!-- -->
