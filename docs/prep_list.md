#  Get list of participants, explore folders and count files using  the function `scout_bids_for_gui_env`

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
| N \*rest\*.mat = 14 | 
| N \*rest\*bold\*dtseries.nii* = 14 | 

- `text_missing`. Cell array showing a summary count of missing files *per* type/extension.

| text_missing | 
| :---|
| N folders with missing \*rest\*.mat data = 0 | 
| N folders with missing \*rest\*bold\*dtseries.nii* data = 0 | 

- txt file. It also save a txt file indicating the number of participants with data to calculate connectivity matrices. The default name is `list.txt`.



## Finding subjects with specific parcellations schemas

To look for paths with several parcellation schemas, for example Gordon and HCP, you can use the extra argument *extra_strings_to_match* as follows: 

```matlab
extra_strings_to_match{1}='\*rest\*bold\*ordon*ptseries.nii*';
extra_strings_to_match{2}='\*rest\*bold\*HCP*ptseries.nii*';
[T_count, list,text_counts,text_missing] = scout_bids_for_gui_env(path_BIDS_data,...
    'extra_strings_to_match',extra_strings_to_match)
```

Corresponding outputs are:

- `T_count.` Table reporting the file types per participant in the `root_path`.

| list_func | rest_star_mat | rest_bold_dtseries_nii_ | rest_bold_ordon_ptseries_nii_ | rest_bold_HCP_ptseries_nii_ | 
| --- :| --- :| --- :| --- :| --- :|
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_01\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_02\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_03\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_04\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_05\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_06\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_07\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_08\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_09\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_10\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_11\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_12\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_13\fake_visit_1\func | 1 | 1 | 1 | 1 | 
| C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_14\fake_visit_1\func | 1 | 1 | 1 | 1 | 


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
| --- :|
| N func = 14 | 
| N \*rest\*.mat = 14 | 
| N \*rest\*bold\*dtseries.nii* = 14 | 
| N \*rest\*bold\*ordon\*ptseries.nii* = 14 | 
| N \*rest\*bold\*HCP\*ptseries.nii* = 14 | 

- `text_missing`. Cell array showing a summary count of missing files *per* type/extension.

| text_missing | 
| --- :|
| N folders with missing \*rest\*.mat data = 0 | 
| N folders with missing \*rest\*bold\*dtseries.nii* data = 0 | 
| N folders with missing \*rest\*bold\*ordon\*ptseries.nii* data = 0 | 
| N folders with missing \*rest\*bold\*HCP\*ptseries.nii* data = 0 | 

- txt file. It also save a txt file indicating the number of participants with data to calculate connectivity matrices. 

## Specifying preffix for output txt file

To add a preffix to the txt file made by `scout_bids_for_gui_env`, provide the optional argument *preffix*:

```matlab
preffix='only_Gordon';
[T_count, list,text_counts,text_missing] = scout_bids_for_gui_env(path_BIDS_data,...
    'preffix',preffix)
```

## Avoiding dtseries

If for some reason you only need a list of participants with parcellaterd data (i.e., you do not need/have dtseries), set the additional argument *exclude_dtseries_flag* equal to 1:

```matlab
exclude_dtseries_flag=1;
[T_count, list,text_counts,text_missing] = scout_bids_for_gui_env(path_BIDS_data,...
    'extra_strings_to_match',extra_strings_to_match,...
    'exclude_dtseries_flag',exclude_dtseries_flag,...
```

## Example using several optional arguments

```matlab
preffix='only_HCP_no_dtseries';
exclude_dtseries_flag=1;
extra_strings_to_match='*rest*bold*HCP*ptseries.nii*';

[T_count, list,text_counts,text_missing] = scout_bids_for_gui_env(path_BIDS_data,...
    'extra_strings_to_match',extra_strings_to_match,...
    'exclude_dtseries_flag',exclude_dtseries_flag,...
    'extra_strings_to_match',extra_strings_to_match)
```