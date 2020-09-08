

# List of participants        


In preparation, you need the list of paths to the processed data from the participants on which connectivity matrices will be calculated. This list needs to be saved as a txt file. Keep in mind that the name of this txt file will be used as prefix in folders and files created by this GUI. You might want to use a descriptive name such as “controls_good_QC.txt”, “PD_and_Ct.txt”, …. When this tutorial was prepared, the selected name was `“list_N_14.txt”`. You’ll see the consequences of this decision.
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
# Get list of participants, explore folders and count files

To feed the GUI_environments you need a list of participants. This list can be generated using the function `scout_bids_for_gui_env`. This function will allow you to:

- Get a properly formatted list to feed the GUI_environments.
- Make a report of dtseries, ptseries and dot mat files.
- Generate a report of folders with missing data.

This is an example of how to run it:

```matlab
root_path=[/path_to_the_data_in_my_system/];
[T_count, list,text_counts,text_missing] = scout_bids_for_gui_env(root_path)
```
C:.


```
├───my_subject1
│   └───ses-baselineYear1Arm1
│       ├───anat
│       └───func
├───my_subject2
│   └───ses-baselineYear1Arm1
│       ├───anat
│       └───func
├───sub-NDARINV00HEV6HB
``` 

C:.


├───sub-36112
│   └───ses-4mo
│       ├───anat
│       └───func
├───sub-36119
│   └───ses-4mo
│       ├───anat
│       └───func
├───sub-36147
│   └───ses-4mo
│       ├───anat
│       └───func



| list_func | rest_bold_star_mat | rest_bold_dtseries_nii_ | rest_bold_HCP_ptseries_nii_ | rest_bold_ordon_ptseries_nii_ | 
| --- :| --- :| --- :| --- :| --- :|
| ~\sub-NDARINV00BD7VDC\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV00CY2MDM\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV00HEV6HB\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV00J52GPG\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV00LH735Y\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV00LJVZK2\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV00NPMHND\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV00R4TXET\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV00U4FTRU\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV00UMK5VC\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV00X2TBWJ\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV0A4P0LWM\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV0A4ZDYNL\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 
| ~\sub-NDARINV0A6WVRZY\ses-baselineYear1Arm1\func | 1 | 1 | 1 | 1 | 

**Inputs**
`root_path` is the path to the derivatives folder containing the subjetc ids

**Outputs**

- `T_count`
- `list`
- `text_counts`
- `text_missing`

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