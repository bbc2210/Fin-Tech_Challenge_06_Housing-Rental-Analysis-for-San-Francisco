# Housing-Rental-Analysis-for-San-Francisco

In this challenge, your job is to use your data visualization superpowers, including aggregation, interactive visualizations, and geospatial analysis, to find properties in the San Francisco market that are viable investment opportunities.

Instructions:

Use the `san_francisco_housing.ipynb` notebook to visualize and analyze the real-estate data.

Note that this assignment requires you to create a visualization by using the integration between Plotly and the Mapbox API. Be sure to create your environment file (`.env`) and include your Mapbox API access token. Then import your Mapbox API access token into the `san_francisco_housing.ipynb` notebook, and set it by using the `px.set_mapbox_access_token` function.

Additionally, you need to read the `sfo_neighborhoods_census_data.csv` file from the `Resources` folder into the notebook and create the DataFrame that you’ll use in the analysis.

The main task in this Challenge is to visualize and analyze the real-estate data in your Jupyter notebook. Use the `san_francisco_housing.ipynb` notebook to complete the following tasks:

- Calculate and plot the housing units per year.
- Calculate and plot the average prices per square foot.
- Compare the average prices by neighborhood.
- Build an interactive neighborhood map.
- Compose your data story.

##### Calculate and Plot the Housing Units per Year

For this part of the assignment, use numerical and visual aggregation to calculate the number of housing units per year, and then visualize the results as a bar chart. To do so, complete the following steps:

1. Use the `groupby` function to group the data by year. Aggregate the results by the `mean` of the groups.

2. Use the `hvplot` function to plot the `housing_units_by_year` DataFrame as a bar chart. Make the x-axis represent the `year` and the y-axis represent the `housing_units`.

3. Style and format the line plot to ensure a professionally styled visualization.

4. Note that your resulting plot should appear similar to the following image:

   

![zoomed-housing-units-by-year](Images\zoomed-housing-units-by-year.png)



1. Answer the following question:
   - What’s the overall trend in housing units over the period that you’re analyzing?

##### Calculate and Plot the Average Sale Prices per Square Foot

For this part of the assignment, use numerical and visual aggregation to calculate the average prices per square foot, and then visualize the results as a bar chart. To do so, complete the following steps:

1. Group the data by year, and then average the results. What’s the lowest gross rent that’s reported for the years that the DataFrame includes?

2. Create a new DataFrame named `prices_square_foot_by_year` by filtering out the “housing_units” column. The new DataFrame should include the averages per year for only the sale price per square foot and the gross rent.

3. Use hvPlot to plot the `prices_square_foot_by_year` DataFrame as a line plot.

   > **Hint** This single plot will include lines for both `sale_price_sqr_foot` and `gross_rent`.

4. Style and format the line plot to ensure a professionally styled visualization.

5. Note that your resulting plot should appear similar to the following image:

![A screenshot depicts an example of the resulting plot.](Images\avg-sale-px-sq-foot-gross-rent.png)

1. Use both the `prices_square_foot_by_year` DataFrame and interactive plots to answer the following questions:
   - Did any year experience a drop in the average sale price per square foot compared to the previous year?
   - If so, did the gross rent increase or decrease during that year?

##### Compare the Average Sale Prices by Neighborhood

For this part of the assignment, use interactive visualizations and widgets to explore the average sale price per square foot by neighborhood. To do so, complete the following steps:

1. Create a new DataFrame that groups the original DataFrame by year and neighborhood. Aggregate the results by the `mean` of the groups.
2. Filter out the “housing_units” column to create a DataFrame that includes only the `sale_price_sqr_foot` and `gross_rent` averages per year.
3. Create an interactive line plot with hvPlot that visualizes both `sale_price_sqr_foot` and `gross_rent`. Set the x-axis parameter to the year (`x="year"`). Use the `groupby` parameter to create an interactive widget for `neighborhood`.
4. Style and format the line plot to ensure a professionally styled visualization.
5. Note that your resulting plot should appear similar to the following image:

![A screenshot depicts an example of the resulting plot.](Images\pricing-info-by-neighborhood.png)

1. Use the interactive visualization to answer the following question:
   - For the Anza Vista neighborhood, is the average sale price per square foot for 2016 more or less than the price that’s listed for 2012?

##### Build an Interactive Neighborhood Map

For this part of the assignment, explore the geospatial relationships in the data by using interactive visualizations with Plotly and the Mapbox API. To build your map, use the `sfo_data_df` DataFrame (created during the initial import), which includes the neighborhood location data with the average prices. To do all this, complete the following steps:

1. Read the `neighborhood_coordinates.csv` file from the `Resources` folder into the notebook, and create a DataFrame named `neighborhood_locations_df`. Be sure to set the `index_col` of the DataFrame as “Neighborhood”.
2. Using the original `sfo_data_df` Dataframe, create a DataFrame named `all_neighborhood_info_df` that groups the data by neighborhood. Aggregate the results by the `mean` of the group.
3. Review the two code cells that concatenate the `neighborhood_locations_df` DataFrame with the `all_neighborhood_info_df` DataFrame. Note that the first cell uses the [Pandas concat function](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.concat.html) to create a DataFrame named `all_neighborhoods_df`. The second cell cleans the data and sets the “Neighborhood” column. Be sure to run these cells to create the `all_neighborhoods_df` DataFrame, which you’ll need to create the geospatial visualization.
4. Using Plotly Express, create a `scatter_mapbox` for the `all_neighborhoods_df` DataFrame. Remember that you need your MapBox API key. Be sure to do the following:
   - Set the `size` parameter to “sale_price_sqr_foot”.
   - Set the `color` parameter to “gross_rent”.
   - Set the `size_max` parameter to “25”.
   - Set the `zoom` parameter to “11”.
5. Style and format the line plot to ensure a professionally styled visualization.
6. Note that your resulting plot should appear similar to the following image:

![A screenshot depicts an example of a scatter plot created with the Mapbox API.](Images\mapbox-plot.png)

1. Use the interactive map to answer the following question:
   - Which neighborhood has the highest gross rent, and which has the highest sale price per square foot?

##### Compose Your Data Story

Based on the visualizations that you created, answer the following questions:

- How does the trend in rental income growth compare to the trend in sales prices? Does this same trend hold true for all the neighborhoods across San Francisco?
- What insights can you share with your company about the potential one-click, buy-and-rent strategy that they're pursuing? Do neighborhoods exist that you would suggest for investment, and why?



---

## Technologies

This project leverages python 3.7 with the following packages:

* [Pandas](https://pandas.pydata.org/) - Pandas is a Python library that’s designed speci cally for data analysis. It offers a streamlined way of reviewing datasets and includes
  various functions that simplify importing, updating, and analyzing data.
* [JupyterLab](https://jupyter.org/) - JupyterLab is a web-based user interface that you use to run and review Python-based programs. It easily integrates with the Anaconda
  software package and your Conda development environment.
* [PyViz](https://pypi.org/project/pyviz/) - PyViz is a Python visualization package that provides a single platform for accessing multiple visualization libraries. Two of these libraries are Plotly Express and hvPlot, which you’ll use during this module.
* [The Mapbox API](https://docs.mapbox.com/api/overview/) - The Mapbox web services APIs allow you to programmatically access Mapbox tools and services.

## Installation Guide

Before running the application first install the following dependencies

```python
#Install the PyViz Ecosystem
##From your terminal, log in to your Conda dev environment.
##Install the PyViz packages by using the conda install command as follows:
conda install -c plotly plotly=4.13.
conda install -c pyviz hvplot

##Confirm the installation of all the PyViz packages by running the following commands:
conda list plotly
conda list hvplot

##Install the JupyterLab Extensions
jupyter labextension install jupyterlab-plotly@4.13.0
jupyter labextension install @jupyter-widgets/jupyterlab-manager plotlywidget@4.13.0
jupyter labextension install @pyviz/jupyterlab_pyviz

jupyter lab build
```

---

## Usage

To use the Crypto Arbitrage application simply clone the repository, download whale_navs.csv,   and run the **san_francisco_housing.ipynb** with:

```python
jupyter lab
```

---

## Contributors


---

## License