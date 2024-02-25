# Problem Set 1 - Solutions

## Print the Totals of All Variables

    from netCDF4 import Dataset
    import numpy as np
    
    def print_totals(file_path):
        """print emissions totaled by major groups"""
        # open NetCDF file
        root = Dataset(file_path, 'r')
    
        # print individual species totals
        for spec in root.variables:
            if spec == 'TFLAG':
                continue
            try:
                total = np.sum(root.variables[spec][:])
                print(spec + ' = ' + str(total) + ' (' + root.variables[spec].units.strip() + ')')
            except Exception as e:
                print("Error with %s: %s" % (spec, e))
    
        root.close()

## Creating a Simple NetCDF File

    from netCDF4 import Dataset
    
    def create_empty_elevation(file_path):
        '''Creates an empty NetCDF file for elevation data.'''
        # open file
        root = Dataset(file_path, 'w', format="NETCDF4")
        
        # create dimensions
        time = root.createDimension("time", None)
        x = root.createDimension("x", 100)
        y = root.createDimension("y", 100)
        
        # create variable
        elevation = root.createVariable('elevation', 'f4', ('time', 'x', 'y'),
                                        least_significant_digit=2)
        
        # variables should have units
        elevation.units = 'km'
    
        root.close()

## Writing to a NetCDF File

    from netCDF4 import Dataset
    import numpy as np
    
    def fill_valley_elevation(file_path):
        '''example function to write some test data to a test file'''
        # open file
        root = Dataset(file_path, 'r+', format="NETCDF4")
        
        # build the fake elevation data
        steps = np.arange(0.0, 2 * np.pi, np.pi / 50.0)
        yosemite = 1.218 * np.cos(steps) + 1.372
        valley = np.array([1.219 * np.cos(np.arange(0, 2*np.pi, np.pi/50.0)) + 1.372]*100, np.float32).reshape(1,100,100)
        
        # load elevation data
        elevation = root.variables['elevation']
        elevation[0,0:100,0:100] = valley
        
        # add a couple more attributes
        root.FILEDESC = 'elevation of an imaginary valley'
        root.HISTORY = "The elevation doesn't change much over time."
        
        root.close()

## Pulling it All Together

    >>> create_empty_elevation('elevation.ncf')
    >>> fill_valley_elevation('elevation.ncf')
    >>> print_totals('elevation.ncf')
    elevation = 13714.1 (km)

## IOAPI

    def extract_IOAPI_variable(file_path, var):
        '''Extract the values of a variable in an IOAPI NetCDF file.
        This will return a multi-dimensional array of
        the NetCDF file variables.'''
        root = Dataset(file_path, 'r', format='NETCDF3_CLASSIC')
    
        if var not in root.variables.keys():
            raise Exception('The variable ' + str(variable) + ' does not exist.')
    
        return root.variables[var][:]

[Back to Problem Set](problem_set_1_netcdf4_operations.md)
