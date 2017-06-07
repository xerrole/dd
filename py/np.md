<!-- doc for numpy -->

# Count pixels occurance in image through numpy, and remove noise background colors.

    # area larger than 1 percent of the whole image is judged as noise background
    NOISE_EDGE_RATE = 0.1
    
    def remove_bg(img, rate=NOISE_EDGE_RATE):
        if isinstance(img, ndarray):
            ima = img
            convert_to_img = False
        else:
            ima = array(img)
            convert_to_img = True

        former_shape = ima.shape
        ima.shape = -1, 3

        imv = ascontiguousarray(ima).view(dtype(void, ima.dtype.itemsize * 3))
        _, positions, counts = unique(imv, return_index=True, return_counts=True)
        bg_pixels = ima[positions[np.where(counts > np.sum(counts) * rate)]]
        for pixel in bg_pixels:
            ima[np.where(ima == pixel)] = 255

        ima.shape = former_shape

        return Image.fromarray(ima) if convert_to_img else ima
