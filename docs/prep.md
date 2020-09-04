# Explore BIDS folders, get list of participants and report counts

To feed the GUI_environments you need a list of participants. This list can be generated using the function `scout_bids_for_gui_env`. This function allows you to:

- Get a properly formatted list to feed the GUI_environments.
- Make a report of dtseries, ptseries and dot mat dot mat files.
- Generate a report of folders with missing data.

This is an example of how to run it:

```matlab
[T_count, list,text_counts,text_missing] = scout_bids_for_gui_env(root_path)
```

**Inputs**
`root_path` is the path to the derivatives folder containing the subjetc ids

**Outputs**

- `T_count`
- `list`
- `text_counts`
- `text_missing`

# Pre-calculate variance file for all the subjects

The `GUI_environments` look for outliers based on the variance of the dtseries. If existing, that file is used, if not the file is calculated. You can calculate the variance file by running this patch:

```matlab
dtvariance_patch(path_list_file)
```

**Mandatory Inputs**
- `path_list_file`: Path to the list of participants made by the function `scout_bids_for_gui_env`

**Optional inputs**
- `output_folder`: Path to a output folder. If not provided,  creates a folder named `dtvariace_files` and saves the data there:  `output_folder=[pwd filesep 'dtvariance_files']`;
-`save_in_BIDS_folder`: accepts as input `1` or `0`. If not provided its default value is zero. If provided and set to `1`, saves variance files in the same location where the `*dtseries` cifti files are located.
- `string_to_match`: advanced feature to allow search for dtseries on different nested folders. No need to use it if imaging data is BIDs formatted.