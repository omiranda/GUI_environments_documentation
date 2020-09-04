# Explore BIDS folders, get list of participants and report counts

To feed the GUI_environments you need a list of participants. This list can be generated using the function `scout_bids_for_gui_env`. This function allows you to:

- Get a properly formatted list to feed the GUI_environments.
- Make a report of dtseries, ptseries and dot mat dot mat files.
- Generate a report of folders with missing data.

This is an example of how to run it:

```matlab
[T_count, list,text_counts,text_missing] = scout_bids_for_gui_env(root_path)
```



# Pre-calculate variance file for all the subjects

