This code needs as input a text file with a **list of participants** with processed data. This section explains the content of the file and also describes how to use the support function `scout_bids_for_gui_env` to generate this file.

In addition, the code requires *per* participant a **cifti's `dtseries` variance file** to identify and exclude outliers. The code wil look for that file in the `root_path/ID/visit/func/` folder. If that file does not exist, the GUI will calculate the variance and make the corresponding file. If needed, you can precalculate those files and save time using the function `dtvariance_patch`.



# List of participants        


In preparation, you need the list of paths to the processed data from the participants on which connectivity matrices will be calculated. This list needs to be saved as a txt file. Keep in mind that the name of this txt file will be used as prefix in folders and files created by this GUI. You might want to use a descriptive name such as “controls_good_QC.txt”, “PD_and_Ct.txt”, …. When this tutorial was prepared, the selected name was `“list_N_14.txt”`. You’ll see the consequences of this decision. As shown below, this list can be generated using the function `scout_bids_for_gui_env`.


Following block shows the content of the subject_list's txt file which contains fullpath to the processed data:

```
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_01\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_02\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_03\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_04\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_05\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_06\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_07\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_08\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_09\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_10\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_11\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_12\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_13\fake_visit_1
C:\Users\oscar\OneDrive\matlab_code\GUI_environments\data\anonymized_human\fake_ID_14\fake_visit_1
```

The following block shows the folders with processed data within each path

```
.
+--- fake_ID_01
|   +--- fake_visit_1
|   |   +--- anat
|   |   |   +--- fake_ID_01_fake_visit_1_atlas-MNI_space-fsLR32k_curv.dscalar.nii
|   |   |   +--- fake_ID_01_fake_visit_1_atlas-MNI_space-fsLR32k_desc-smoothed_myelinmap.dscalar.nii
|   |   |   +--- fake_ID_01_fake_visit_1_atlas-MNI_space-fsLR32k_myelinmap.dscalar.nii
|   |   |   +--- fake_ID_01_fake_visit_1_atlas-MNI_space-fsLR32k_sulc.dscalar.nii
|   |   |   +--- fake_ID_01_fake_visit_1_atlas-MNI_space-fsLR32k_thickness.dscalar.nii
|   |   |   +--- fake_ID_01_fake_visit_1_space-ACPC_dseg.nii.gz
|   |   +--- func
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_bold_mask.mat
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_bold_mask.mat_0.2_cifti_censor_FD_vector_10_minutes_of_data_at_0.2_threshold.txt
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_bold_roi-Gordon2014FreeSurferSubcortical_timeseries.ptseries.nii
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_bold_roi-HCP2016FreeSurferSubcortical_timeseries.ptseries.nii
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_bold_timeseries.dtseries.nii
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_run-1_desc-filtered_motion.tsv
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_run-1_motion.tsv
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_run-2_desc-filtered_motion.tsv
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_run-2_motion.tsv
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_run-3_desc-filtered_motion.tsv
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_run-3_motion.tsv
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_run-4_desc-filtered_motion.tsv
|   |   |   +--- fake_ID_01_fake_visit_1_task-rest_run-4_motion.tsv
+--- fake_ID_02
|   +--- fake_visit_1
|   |   +--- anat
|   |   |   +--- fake_ID_02_fake_visit_1_atlas-MNI_space-fsLR32k_curv.dscalar.nii
|   |   |   +--- fake_ID_02_fake_visit_1_atlas-MNI_space-fsLR32k_desc-smoothed_myelinmap.dscalar.nii
|   |   |   +--- fake_ID_02_fake_visit_1_atlas-MNI_space-fsLR32k_myelinmap.dscalar.nii
|   |   |   +--- fake_ID_02_fake_visit_1_atlas-MNI_space-fsLR32k_sulc.dscalar.nii
|   |   |   +--- fake_ID_02_fake_visit_1_atlas-MNI_space-fsLR32k_thickness.dscalar.nii
|   |   |   +--- fake_ID_02_fake_visit_1_space-ACPC_dseg.nii.gz
|   |   +--- func
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_bold_mask.mat
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_bold_mask.mat_0.2_cifti_censor_FD_vector_All_Good_Frames.txt
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_bold_roi-Gordon2014FreeSurferSubcortical_timeseries.ptseries.nii
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_bold_roi-HCP2016FreeSurferSubcortical_timeseries.ptseries.nii
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_bold_timeseries.dtseries.nii
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_run-1_desc-filtered_motion.tsv
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_run-1_motion.tsv
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_run-2_desc-filtered_motion.tsv
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_run-2_motion.tsv
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_run-3_desc-filtered_motion.tsv
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_run-3_motion.tsv
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_run-4_desc-filtered_motion.tsv
|   |   |   +--- fake_ID_02_fake_visit_1_task-rest_run-4_motion.tsv
+-
```
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