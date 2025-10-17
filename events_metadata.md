# Metadata for events.csv
This dataset contains seismic data with the following features:
* **time**: Timestamp when the event occurred.
* **latitude**: Latitude of the event location in decimal degrees.
* **longitude**: Longitude of the event location in decimal degrees.
* **depth**: Depth of the event in kilometers.
* **mag**: The magnitude of the event.
* **magType**: The method or algorithm used to calculate the preferred magnitude for the event.
* **dmin**: Horizontal distance from the epicenter to the nearest station in degrees. One degree corresponds to approximately 111.2 kilometers.
* **net**: The unique identifier of a data contributor.
* **id**: A unique identifier for the event.
* **type**: The type of seismic event (e.g., earthquake, explosion).
* **horizontalError**: Uncertainty of the reported location of the event. A "shallow" value indicates the error is less than 10km; otherwise, it is considered "deep".
* **depthError**: Uncertainty of the reported depth of the event in kilometers.
* **magError**: The estimated standard error of the reported magnitude of the event.
* **is_country**: A binary variable indicating whether an event occurred at sea (`False`) or on land (`True`).
*You can assume that there are no significant outliers in this dataset.*
