%%
ID: 6401297
Updated: 2020-11-24
%%
![](https://images-na.ssl-images-amazon.com/images/I/418lVZnPZXL._SL500_.jpg)

# About
Title: [[Ggplot2]]
Author: [[Hadley Wickham]]
Category: #supplementals
Number of Highlights: ==10==
Last Highlighted: *2020-11-24*
Readwise URL: https://readwise.io/bookreview/6401297

# Highlights 
The names of generated variables must be surrounded with .. when used.  ^113158741

---

With longitudinal data, you often want to display multiple time series on each plot, each series representing one individual. To do this with qplot(), you need to map the group aesthetic to a variable encoding the group membership of each observation. This is explained in more depth in Section 4.5.3.  ^113158742

---

Mapping a categorical variable to an aesthetic will automatically split up the geom by that variable, so these commands instruct qplot() to draw a density plot and histogram for each level of diamond colour.  ^113158743

---

You can also manually set the aesthetics using I (), e.g., colour = I (“red”) or size = I(2). This is not the same as mapping and is explained in more detail in Section 4.5.2.  ^113158744

---

The default faceting method in qplot() creates plots arranged on a grid specified by a faceting formula which looks like row_var ∼ col_var.  ^113158745

---

From top to bottom: faceted histogram, a conditional density plot, and frequency polygons. All show an interesting pattern: as quality increases, the distribution shifts to the left and becomes more symmetric.  ^113158746

---

Position adjustments are normally used with discrete data.  ^113158747

---

Faceting is described in Chapter 7.  ^113158748

---

More details about the algorithm used can be found in ?loess.  ^113158749

---

The data that you want to visualise and a set of aesthetic mappings describing how variables in the data are mapped to aesthetic attributes that you can perceive. • Geometric objects, geoms for short, represent what you actually see on the plot: points, lines, polygons, etc. • Statistical transformations, stats for short, summarise data in many useful ways. For example, binning and counting observations to create a histogram, or summarising a 2d relationship with a linear model. Stats are optional, but very useful. • The scales map values in the data space to values in an aesthetic space, whether it be colour, or size, or shape. Scales draw a legend or axes, which provide an inverse mapping to make it possible to read the original data values from the graph. • A coordinate system, coord for short, describes how data coordinates are mapped to the plane of the graphic. It also provides axes and gridlines to make it possible to read the graph. We normally use a Cartesian coordinate system, but a number of others are available, including polar coordinates and map projections. • A faceting specification describes how to break up the data into subsets and how to display those subsets as small multiples. This is also known as conditioning or latticing/trellising.  ^113158750

