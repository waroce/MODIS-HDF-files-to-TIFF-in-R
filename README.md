# MODIS-HDF-files-to-TIFF-in-R

library(gdalUtils)

setwd('D:/dados_doc/Rasters/MODIS2015')

files <- dir(pattern = ".hdf")
files

# MOD13Q1.A2015353.h13v10.006.2016007180718

filename <- substr(files,1,41)
filename <- paste0('./output/',filename, ".tif")
filename

# inside <- get_subdatasets(files[1])


for (i in 1:length(filename)){
  # i=1
  sds <- get_subdatasets(files[i])
  gdal_translate(sds[1], dst_dataset = filename[i])
}
