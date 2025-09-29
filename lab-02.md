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
ggplot(plastic_waste, aes(x = plastic_waste_per_cap)) +
  geom_histogram() +
  facet_wrap(~ continent)
```

    ## `stat_bin()` using `bins = 30`. Pick better value `binwidth`.

![](lab-02_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

### Exercise 2

``` r
ggplot(plastic_waste, aes(x = plastic_waste_per_cap)) +
  geom_density()
```

![](lab-02_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

``` r
ggplot(plastic_waste, aes(x = plastic_waste_per_cap, colour = continent)) +
  geom_density() +
  labs(
    title = "Courbes de densité des déchets plastiques par habitant",
    x = "Déchets plastiques par habitant (kg/hab/an)",
    y = "Densité",
    colour = "Continent"
  ) 
```

![](lab-02_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
ggplot(plastic_waste, aes(x = plastic_waste_per_cap, fill = continent)) +
  geom_density(colour = NA) +
  labs(
    x = "plastic_waste_per_cap",
    y = "density",
    fill = "continent",
    title = NULL
  ) 
```

![](lab-02_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
ggplot(plastic_waste, aes(x = plastic_waste_per_cap, fill = continent, colour = continent)) +
  geom_density(alpha = 0.4) +
  labs(
    x = "plastic_waste_per_cap",
    y = "density",
    fill = "continent",
    colour = "continent"
  )
```

![](lab-02_files/figure-gfm/unnamed-chunk-5-1.png)<!-- --> Décrivez
pourquoi le reglage de la couleur (color et fill) et le réglage de la
transparence (alpha) ne se trouvent pas au même endroit ? L’un étant
réglé dans aes et l’autre dans geom_density():

Car dans aes(), on met ce qui dépend des données comme par exemple la
couleur qui change selon le continent. Toutefois, alpha est pareil pour
tout le graphe donc on doit le mettre dans geom_density().

### Exercise 3

Boxplot:

``` r
ggplot(plastic_waste, aes(x = continent, y = plastic_waste_per_cap)) +
  geom_boxplot(size = 0.5, outlier.size = 1) +
  labs(
    x = "continent",
    y = "plastic_waste_per_cap")
```

![](lab-02_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

Violinplot:

``` r
ggplot(plastic_waste, aes(x = continent, y = plastic_waste_per_cap)) +
  geom_violin() +
  labs(
    x = "continent",
    y = "plastic_waste_per_cap")
```

![](lab-02_files/figure-gfm/unnamed-chunk-7-1.png)<!-- --> Qu’est ce que
les violin plots permettent de voir sur les données que les boxplot ne
permettent pas ?

Le boxplot fournit une représentation qui indique la médiane, la
dispersion via les quartiles, ainsi que les valeurs atypiques.Le violin
plot, lui, illustre la distribution des données grâce à une estimation
de densité. Il rend visible la structure de la répartition, ce que le
boxplot ne montre pas.

### Exercise 4

Réponse à la question…

### Exercise 5

Réponse à la question…

## Conclusion

Recréez la visualisation:
