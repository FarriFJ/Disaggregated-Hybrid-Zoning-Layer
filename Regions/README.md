# Steps to take (TODO-list) to create a zoning system for the Hasselt region

Note: A lot of the manipulations/code that are executed for the Hasselt region will have to be replicated for the other STRAUSS regions. This seems to hint at creating generic scripts that are configured and reused for the different regions. However, initially, it is probably better to start from a ipython workbook for Hasselt that is nicely documented. 

- determine the extent of the study area and the influence region
    - pick a central location in Hasselt
    - create a reasonable buffer (initially not too large to have short experimental runtimes)
- obtain complete Feathers input dataset (incl. population file, land use and impedance materices) for a less detailed zoning system
    - SUBZONES-based zoning system used in the Cegeka project (for now)
    - SUBZONE = deelgemeente = DLG 
- download OSM data and filter the buildings
- cluster buildings accounting for the SUBZONES 
    - note that we start from SUBZONES for the initial experiment, but later on, when we create a dataset based on the statistical sectors, we might revise this and do the clustering based on the statistical sectors (SS).
- convert the clusers of buildings to polygons (zones) that are compatible with the SUBZONE layer boundaries.
    - how do we determine decent/sensible numbers of zones to be obtained?
        - define a maximal surface?
        - look at variability of travel times for points within the cluster and restrict this?
        - ... ?
- disaggregate the SUBZONE layer to the smaller layer (todo: we need a concise name for the new layer)
    - this is `areal interpolation`, which we have implemented ourselves in the code shared with Inez for her thesis (23-24), but this is unelegant. Consider using the [Tobler Python package](https://github.com/pysal/tobler).