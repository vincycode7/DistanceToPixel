import numpy as np

#code to normalize distance of a sensor to an object
class Normalize_Meter_Distance(object):
    """
        class to covent distance to pixels.
    """
    meter_to_pixel = 3779.5280 #1 meter is equal to 3779.5280

    @classmethod
    def normalize(cls,array=None):
        """
            method to normalize the distance

            Example:
            =======
            Normalize_Meter_Distance.normalize(arr)

            Returns
            =======
            np.ndarray
        """
        
        #convert from meter to pixels
        assert isinstance(array, np.ndarray), "array should be a numpy array"
        array = array * cls.meter_to_pixel

        #nomalize pixels
        min_ = array.min()
        max_ = array.max()

        array = (array - min_)/(max_ - min_)
        return array

    @classmethod
    def test(cls):
        """
            method to test the code
        """
        arr = np.array([[0.7, 0.2, 0.54],
                        [0.1, 0.87, 0.95],
                        [1.1, 0.9, 0.54]], dtype=np.float64)

        result = np.array([[0.6, 0.1, 0.44],
                            [0, 0.77, 0.85],
                            [1, 0.8, 0.44]], dtype=np.float64)

        assert (cls.normalize(array=arr) == result).any(), "Test Failed"
        print("Test Passed")

arr = np.array([[0.7, 0.2, 0.54],
                [0.1, 0.87, 0.95],
                [1.1, 0.9, 0.54]])

if __name__ == "__main__":
    #test method
    Normalize_Meter_Distance.test()