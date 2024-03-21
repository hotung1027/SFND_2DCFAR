# 1. Implementation steps for the 2D CFAR process.
- 1. define the hyperparameters of training cells, guard cells, and offsets
- 2. apply 2DFFT to convert signals into range-doppler map.
- 3. Convolute the range-doppler map with the kernel of training cells to compute the average signals over the kernel except for guard cells.
- 4. After compute the average of each individual threshold, and multiply them with a scaling factor(offset)
  5. Binary threshold with individual signal surpass the threshold after offset.
  6. Da ta, we have the detetion bin on the range-doppler map

# 2. Selection of Training, Guard cells and offset.
The selection is based on the size of range-doppler map, that say, it should be chosen relative to the range/doppler resolution.
So that it includes mulitple of signals' peak, as we set the resolution of 1m, the selection of 4 to 16 for training cell are sensible, this time I would like to 16 for longer average for the threshold, to reduce outliers,
and guard cells of 3 relative small to training cell.
The scaling factor (offset), I take 1.6 - 1.8 should be fine for signal to surpass the environmental noise.
# 3. Steps taken to suppress the non-thresholded cells at the edges.
- We skip the computation at edges, by checking the edge and set those detection to 0.
