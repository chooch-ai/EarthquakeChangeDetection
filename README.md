# EarthquakeChangeDetection

This repository aims to assess the damage caused by the devastating earthquake that shaked Turkey and Syria in Feb 6, 2023. 
Here, we provide pre & post disaster satellite images acquired from [Planet](https://www.planet.com/), as well as the buildings 
that are detected using Chooch AI Inference Engine. 

### Directory Structure
Pre & post disaster satellite images that are spatiallyt matched are provided under `./data_matched/`  directory. 
The `files_info.csv` contains useful information and paths to image pairs. 

The image pairs are grouped by city and dictrict such that each pair can be accessed as:  
```bash
{city}/{district}_{id}/
-- {...}_pre.jpg
-- {...}_post.jpg
-- {...}_pre.tif
-- {...}_post.tif
-- {...}_result.jpg
-- {...}_result.json
```
`.tif` files contain geospatial information. `.tif` files and `.jpg` files have the same image content.  
For some pairs, our preliminary results that compare pre&post images are provided as `_results.jpg` and `_results.json`. 

### Compared Objects Format

#### Result JSON 

Each json has two components, `raw_results` and `changes`, where 
- `raw_results` contain the original predictions for `'A'` & `'B'` images and 
- `changes` contain the predictions grouped by class name and belonging to `'only_A','only_B','common_A','common_B'`  

where in our case `A` refers to pre-disaster and `B` refers to post-disaster buildings. The objects listed under `'only_A'` are supposed to be the destroyed buildings.

####  Comparison Image
The images are shown side by side (or top/bottom, depending on aspect ratio) and the bounding boxes are drawn in two colors, such that:    
- <span style="color:cyan">blue</span> for common (non-damaged) buildings 
- <span style="color:red">red</span> for objects that are present only in pre disaster image, therefore destroyed buildings.

