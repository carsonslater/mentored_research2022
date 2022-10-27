# Statistical Analysis Plan

### Introduction
In this project, I am trying to investigate which forecasting methods might be the best fit for different kinds of goods.

### Controls
There will be two kinds of good primarily:
- High Volume (Order Volume > 20) Each Day
- Low Volume (Order Volume < 20) Each Day

I will be selecting a few SKU's as controls for modeling. Of the high and low volume, I want to explore if I can choose multiple that exhibit different trends and seasonal attributes.

I will filter the data with specific median daily volume, daily variance, and range of daily order volumes (See `Data_Transformation_II.Rmd`, Chunk 10). From these observations I will select the SKU's that have been ordered consistently throughout the sample time period (i.e. has been purchased for at least 300 of the days during which the sample data has been collected).

From the SKU's fitting this criteria, I will use them as controls for the data.

A further research question could perhaps be - which models work the best with the *LEAST* amount of information?

### Building Models

The baseline model will be the `Prophet` model that explored in my first iteration of this project.

The additional models will be `Prophet` models using more information from the domain knowledge (such as a logistic growth stipulation in the model fit), `ETS` models, and `auto.arima` models. If I am able to, I will consider the `TBATS` model.

### Evaluating Models

The primary metrics I will be using to evaluate the models will be RMSE, MAPE, and SMAPE. These will be evaluated the final *n* number of weeks (to be determined) of the data versus the forecasted data. Additionally, any actual observations equal to zero will not be used to calculate the error metrics, as they make MAPE equal to infinity.