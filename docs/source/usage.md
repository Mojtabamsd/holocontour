### Usage

You can run the segmentation pipeline with:

```python
from holocontour.pipeline.pipeline_runner import pipeline_run
import yaml

with open("path/to/sample_config.yaml") as f:
    config = yaml.safe_load(f)
    

# or define the configuration inline

contour_params = {
    "avg_thresh": 81,
    "max_attempts": 10,
    "increase_avg": 5,
    "seed_thresh": 45,
    "min_contour_area": 30,
    "median": False,
    "hist_match": True,
    "ref_path": 'src\holocontour\data\001-4923.pgm(406,428)-Z43.50.png'
    "sharpening_alpha": 1,
    "median_blur_ksize": 5,
    "erode_ksize": 1
    "convex_hull": True
    "keep_init_mask": False,
    "save_plot": True,
}

metadata = {
    "lat": None,
    "lon": None,
    "date": None,
    "ext": ".png"
}


pipeline_run(
    input_folder="path/to/images",
    output_name="output",
    contour_params=config["contour"],
    lat=config["input_metadata"].get("lat"),
    lon=config["input_metadata"].get("lon"),
    date=config["input_metadata"].get("date"),
    ext=config["input_metadata"].get("ext", ".png")
)