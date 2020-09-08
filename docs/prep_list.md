#  Get list of participants, explore folders and count files using `scout_bids_for_gui_env`

To feed the GUI_environments you need a list of participants. This list can be generated using the function `scout_bids_for_gui_env`. This function will allow you to:

- Get a properly formatted list to feed the GUI_environments.
- Make a report of dtseries, ptseries and dot mat files.
- Generate a report of folders with missing data.

This is a basic example of how to run it:

```matlab
root_path='C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human';
[T_count, list,text_counts,text_missing] = scout_bids_for_gui_env(root_path);
```

**Mandatory Input**
`root_path` is the path to the derivatives folder containing the subjetc ids

**Outputs**

- `T_count.` Table reporting the file types per participant in the `root_path`.

| list_func | rest_star_mat | rest_bold_dtseries_nii_ | 
| --- :| --- :| --- :|
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_01\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_02\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_03\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_04\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_05\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_06\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_07\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_08\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_09\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_10\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_11\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_12\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_13\fake_visit_1\func | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_14\fake_visit_1\func | 1 | 1 | 

- `list` A matlab cell with the fullpath of subjects with data. This cell has the same content as the txt file that is created ans saved by this function. 

| list | 
| :--- |
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_01\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_02\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_03\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_04\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_05\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_06\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_07\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_08\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_09\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_10\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_11\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_12\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_13\fake_visit_1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_14\fake_visit_1 | 

- `text_counts`. Cell array showing a summary count of file *per* type/extension.

| text_counts | 
| :---|
| N func = 14 | 
| N *rest*.mat = 14 | 
| N *rest*bold*dtseries.nii* = 14 | 

- `text_missing`. Cell array showing a summary count of missing files *per* type/extension.

| text_missing | 
| :---|
| N folders with missing *rest*.mat data = 0 | 
| N folders with missing *rest*bold*dtseries.nii* data = 0 | 

- txt file. It also save a txt file indicating the number of participants with data to calculate connectivity matrices. The default name has a s preffix `list_N_`, followed by the actual count. In this example the file name is `list_N_14.txt`.




