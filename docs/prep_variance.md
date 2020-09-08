# Pre-calculate variance file for all the subjects

The `GUI_environments` look for outliers based on the variance of the dtseries. If existing, that file is used, if not the file is calculated by the `GUI_environments`. If variance files do not exist, you can save time by pre-calculating them by running this patch:

```matlab
dtvariance_patch(path_list_file)
```

**Mandatory Inputs**

- `path_list_file`: Path to the list of participants made by the function `scout_bids_for_gui_env`

**Optional inputs**

- `output_folder`: Path to a output folder. If not provided,  creates a folder named `dtvariace_files` and saves the data there:  `output_folder=[pwd filesep 'dtvariance_files']`;
- `save_in_BIDS_folder`: accepts as input `1` or `0`. If not provided its default value is zero. If provided and set to `1`, saves variance files in the same location where the `*dtseries` cifti files are located.
- `string_to_match`: advanced feature to allow search for dtseries on different nested folders. No need to use it if imaging data is saved using BIDS standads.