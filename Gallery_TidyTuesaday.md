TidyTuesday Gallery by Magda Blum-Oeste
=======================================
================
Magdalena Blum-Oeste
7/20/2019

INTRODUCTION
------------

This is a collection of charts prepared using data sets from the \#TidyTuesday initiative by R4DS

<br>

GALLERY
-------

### Tidy Tuesday week 29 - R4DS member activity

The area chart inspired by Harro Cyranka (twitter: @harrocyranka)

#### Graph values and themes

``` r
# Graphic elements
text_color1 <- "#d1d1d1"
text_color2 <- "#d1d1d1"
background1 <- "#22282b"
grid_major <- "#575b5d"
panel_border <- "#929495"

# Colour palette
        #22282b
        #575b5d
        #929495
        #d1d1d1
        #dfa2a6
        #e2707d
        #de2a56

# Theme
theme_mbo1 <- function (base_size = 12, base_family = "Source Sans Pro") {
  theme_bw() +
  theme(text = element_text(family = base_family,face = "plain", colour = "black",
                            size = base_size, hjust = 0.5, vjust = 0.5, angle = 0, lineheight = 0.9),
        axis.text = element_text(size = rel(0.8), colour = "white"),
        axis.text.x = element_text(color = text_color1, hjust = 1),
        axis.text.y = element_text(color = text_color1, hjust = 1),
        axis.ticks = element_line(colour = "grey", size = 0.1),
        axis.title.x = element_text(color = text_color1, face = "bold", size = rel(1.2), hjust = 1),
        axis.title.y = element_text(color = text_color1, angle = 90, face = "bold", size = rel(1.2), hjust = 1),
        axis.ticks.length = unit(0.1, "cm"),
      
        legend.position = "none",
        
        panel.background = element_rect(fill = background1, colour = NA),
        panel.border = element_blank(), 
        panel.grid.major = element_line(colour = grid_major),
        panel.grid.minor = element_blank(), 
        panel.spacing.x = unit(5, "pt"), 
        panel.spacing.y = unit(20, "pt"),
          
        plot.background = element_rect(fill = background1, colour = "black"),
        plot.caption = element_text(color = text_color1, face = "italic", size = rel(0.7)), 
        plot.subtitle = element_text(color = text_color1, size = rel(1)),
        plot.title = element_text(color = text_color1, face = "bold", size = rel(1.2)),
        
        strip.background = element_rect(fill = background1, colour = NA),
        strip.text.x = element_text(color = text_color1, face = "bold",  size = rel(1.2)),
        strip.text.y = element_text(color = text_color1, angle = -90, face = "bold", size = rel(1.2))
        
  )
}
```

<br>

#### Data

``` r
# Get the data!
r4ds_members <- readr::read_csv("https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2019/2019-07-16/r4ds_members.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   .default = col_double(),
    ##   date = col_date(format = "")
    ## )

    ## See spec(...) for full column specifications.

``` r
knitr::kable(head(r4ds_members, 12), caption = "Original data frame")
```

| date       |  total\_membership|  full\_members|  guests|  daily\_active\_members|  daily\_members\_posting\_messages|  weekly\_active\_members|  weekly\_members\_posting\_messages|  messages\_in\_public\_channels|  messages\_in\_private\_channels|  messages\_in\_shared\_channels|  messages\_in\_d\_ms|  percent\_of\_messages\_public\_channels|  percent\_of\_messages\_private\_channels|  percent\_of\_messages\_d\_ms|  percent\_of\_views\_public\_channels|  percent\_of\_views\_private\_channels|  percent\_of\_views\_d\_ms|  name|  public\_channels\_single\_workspace|  messages\_posted|
|:-----------|------------------:|--------------:|-------:|-----------------------:|----------------------------------:|------------------------:|-----------------------------------:|-------------------------------:|--------------------------------:|-------------------------------:|--------------------:|----------------------------------------:|-----------------------------------------:|-----------------------------:|-------------------------------------:|--------------------------------------:|--------------------------:|-----:|------------------------------------:|-----------------:|
| 2017-08-27 |                  1|              1|       0|                       1|                                  1|                        1|                                   1|                               4|                                0|                               0|                    1|                                   0.8000|                                         0|                        0.2000|                                0.2857|                                      0|                     0.7143|     0|                                   10|                35|
| 2017-08-28 |                  1|              1|       0|                       1|                                  0|                        1|                                   1|                               0|                                0|                               0|                    0|                                   0.0000|                                         0|                        0.0000|                                1.0000|                                      0|                     0.0000|     0|                                   10|                35|
| 2017-08-29 |                  1|              1|       0|                       1|                                  1|                        1|                                   1|                               0|                                0|                               0|                    0|                                   0.0000|                                         0|                        0.0000|                                1.0000|                                      0|                     0.0000|     0|                                   11|                37|
| 2017-08-30 |                  1|              1|       0|                       1|                                  0|                        1|                                   1|                               0|                                0|                               0|                    0|                                   0.0000|                                         0|                        0.0000|                                1.0000|                                      0|                     0.0000|     0|                                   11|                38|
| 2017-08-31 |                  1|              1|       0|                       1|                                  1|                        1|                                   1|                               1|                                0|                               0|                    0|                                   1.0000|                                         0|                        0.0000|                                1.0000|                                      0|                     0.0000|     0|                                   12|                66|
| 2017-09-01 |                188|            188|       0|                     169|                                111|                      169|                                 111|                             252|                                0|                               0|                  119|                                   0.6792|                                         0|                        0.3208|                                0.8809|                                      0|                     0.1191|     0|                                   12|              1101|
| 2017-09-02 |                284|            284|       0|                     225|                                110|                      270|                                 183|                             326|                                0|                               0|                   46|                                   0.8763|                                         0|                        0.1237|                                0.9607|                                      0|                     0.0393|     0|                                   12|              1797|
| 2017-09-03 |                324|            324|       0|                     214|                                 96|                      309|                                 218|                             204|                                0|                               0|                   71|                                   0.7418|                                         0|                        0.2582|                                0.9450|                                      0|                     0.0550|     0|                                   13|              2265|
| 2017-09-04 |                354|            354|       0|                     203|                                 67|                      337|                                 234|                             155|                                0|                               0|                   70|                                   0.6889|                                         0|                        0.3111|                                0.9431|                                      0|                     0.0569|     0|                                   13|              2631|
| 2017-09-05 |                390|            390|       0|                     254|                                 70|                      378|                                 255|                             135|                                0|                               0|                  122|                                   0.5253|                                         0|                        0.4747|                                0.9211|                                      0|                     0.0789|     0|                                   13|              3055|
| 2017-09-06 |                410|            410|       0|                     223|                                 65|                      397|                                 268|                             130|                                0|                               0|                   52|                                   0.7143|                                         0|                        0.2857|                                0.9549|                                      0|                     0.0451|     0|                                   14|              3337|
| 2017-09-07 |                419|            419|       0|                     240|                                 95|                      409|                                 278|                             254|                                0|                               0|                  122|                                   0.6755|                                         0|                        0.3245|                                0.9481|                                      0|                     0.0519|     0|                                   15|              3864|

#### Area chart

``` r
# Tidy the data for area chart
  TiTu29 <- r4ds_members %>% 
    filter(date >= as.Date("2017-09-01")) %>% 
    mutate(day = lubridate::day(date),
           month = lubridate::month(date, label = TRUE),
           year = lubridate::year(date),
           month = factor(month),
           year = factor(year)) %>% 
   select(date, day, month, year, everything())

#Chart
area_chart <- ggplot(TiTu29, aes(x = day, y = daily_active_members, fill = year)) +
        geom_area(color = "#c6c6c6") +
        facet_grid(year ~ month, scales = "free_x") +
        scale_x_continuous(breaks = c(1, 10, 20, 30), expand = c(0, 0)) +
        scale_y_continuous(breaks = seq(0, 250, 50), expand = c(0, 0)) +
        scale_fill_manual(values = c("#78bc3f", "#404293", "#bc3f65")) +
        labs(title = "Daily active members of the R4DS online learning community",
             subtitle = "The community has started on 1st of September 2017",
             x = "Day",
             y = "Daily Active Members") +
      theme_mbo1()

area_chart
```

<img src="Gallery_TidyTuesaday_files/figure-markdown_github/fig1-1.png" style="display: block; margin: auto;" />

#### Calendar chart - in progress!!!!!

Calender design inspired by <https://www.r-bloggers.com/making-calendar-with-ggplot-moon-phase-calendar-for-fun/>

``` r
# Tidy the data for calendar
TiTu29_cal <- TiTu29

  ## Create Month Week
  TiTu29_cal$yearmonth <- as.yearmon(TiTu29_cal$date) # as.yearmon() from zoo package
  TiTu29_cal$yearmonthf <- factor(TiTu29_cal$yearmonth)
  
  ## Names of week days in base R (whole words)
  TiTu29_cal$weekday <- weekdays(as.Date(TiTu29_cal$date))
  
  ## Names of week days in lubridate (the letters)
  TiTu29_cal$wday <- wday(TiTu29_cal$date, label = TRUE,
                           abbr = TRUE,
                           week_start = getOption("lubridate.week.start", 1))
  
  TiTu29_cal$weekNr <- week(TiTu29_cal$date)
  
  TiTu29_cal <- TiTu29_cal %>% group_by(month) %>% 
    mutate(weekNr_month = dense_rank(weekNr), # dense_rank() from dplyr
           month_full = lubridate::month(date, label = TRUE, abbr = FALSE)) %>%    
    ungroup() %>% 
    select(weekNr, weekNr_month, date, weekday, wday, day, month, year, everything())

# Chart
calendar_chart <- ggplot(TiTu29_cal, aes(x = wday, y = weekNr)) + 
  geom_point(alpha = 1, aes(color = daily_active_members), size = 4) + 
  #geom_text(aes(label = paste0(day, "\n", daily_active_members)), family = "Source Sans Pro", size = rel(1.5)) +
  geom_text(aes(label = day), family = "Source Sans Pro", size = rel(1.8)) +
  facet_grid(month_full ~ year, scales = "free") +  ## So that Each Line is a year!
  scale_x_discrete() +
  scale_y_reverse(expand = c(0, 0.5, 0, 0.5)) +
  scale_colour_gradient2(low = "#bc3f65", high = "#78bc3f",
                         mid = "skyblue", midpoint = 100) +
  labs(title = "Daily active members of the R4DS online learning community", 
       x = "", y = "#Week", color = "Number of daily active members:",
       caption = "(c)Dr.M.Blum-Oeste") +
      theme_mbo1() +
  theme(axis.text.x = element_text(color = text_color1, size = rel(0.8), hjust = 0.5),
        axis.text.y = element_text(color = text_color1, size = rel(1), hjust = 1),
        axis.title.y = element_text(color = text_color1, angle = 90, face = "bold", 
                                    size = rel(1), hjust = 1),
        legend.position = c(0.725, -0.032), #"right", 
        legend.direction = "horizontal",
        legend.justification = 1,
        legend.background = element_rect(fill = background1),
        legend.key.width = unit(10, "mm"),
        legend.key.height = unit(2.5, "mm"),
        legend.title = element_text(family = "Source Sans Pro", size = rel(0.6), color = text_color1, vjust = 0.3),
        legend.text = element_text(family = "Source Sans Pro", size = rel(0.6), color = text_color1,
                                   margin = margin(1, 0, 0, 0, unit = "pt")),
        plot.title = element_text(color = text_color1, face = "bold", size = rel(1), hjust = 0.5),
        panel.grid.major.x = element_line(colour = grid_major),
        panel.grid.major.y = element_line(colour = grid_major), 
        strip.text.x = element_text(color = text_color1, face = "bold",  size = rel(1.2)),
        strip.text.y = element_text(color = text_color1, angle = -90, face = "bold", size = rel(1.2)))
      

calendar_chart
```

<img src="Gallery_TidyTuesaday_files/figure-markdown_github/fig2-1.png" style="display: block; margin: auto;" />
