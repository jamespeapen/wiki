# Plotting

## Axis labels

### Change axis label elements from dataset

To change discrete axis labels in a ggplot, get the labels from the dataset or
make a custom list.

```r
# pull label vector from dataframe
custom_labels <- df$label_col %>% 
                unique() %>% # into other functions
                
df %>%
    ggplot(aes(...)) + ...
    scale_x_discrete(labels = custom_labels)

# or for simple regex

df %>%
    ggplot(aes(...)) + ...
    scale_x_discrete(labels = function(x) {
                         sub("pattern", "replacement", x)
           })
```

### Add new lines to long axis labels

```r
ggplot(df, aes(...) +...
    scale_x_discrete(labels = function(x) {
                         sub("\\s", "\n", x)
           })
```

## Patchwork

The `patchwork` library can make panels with plots. The tag from the plot is
used as the figure label in the panel. Layouts can be controlled with `+` for
horizontal arrangement and `/` for vertical arrangement. These operators can be
used with parentheses to control precedence.

```r
library(patchwork)
plot1 <- ggplot(...) + geom_...() + labs(tag = "A")
plot2 <- ggplot(...) + geom_...() + labs(tag = "B")
plot3 <- ggplot(...) + geom_...() + labs(tag = "C")

# A     B     C

plot1 + plot2 + plot3

# A     B
#       C

plot1 + (plot2 / plot3)
```

