This code needs as input a text file with a **list of participants** with processed data. 

In addition, the code requires *per* participant a **cifti's `dtseries` variance file** to identify and exclude outliers. The code wil look for that file in the `root_path/ID/visit/func/` folder. If that file does not exist, the GUI will calculate the variance and make the corresponding file. If needed, you can precalculate those files and save time using the function `dtvariance_patch`.


# List of participants        

In preparation, you need the list of paths to the processed data from the participants on which connectivity matrices will be calculated. This list needs to be saved as a txt file. Keep in mind that the name of this txt file will be used as prefix in folders and files created by this GUI. You might want to use a descriptive name such as “controls_good_QC.txt”, “PD_and_Ct.txt”, …. When this tutorial was prepared, the selected name was `“list.txt”`. You’ll see the consequences of this decision. This list can be generated using the function [`scout_bids_for_gui_env`](prep_list.md).


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
# Variance files

To identify outliers based on bold data across grayoordinates, the GUI_environments look for a txt file that conteins, for each frame, the variance across grayordinates. The `GUI_environments` look for that file in the BIDS folders or at an alternative path provided by the user. You can pre-calculate that variance file using the function [`dtvariance_patch`](prep_variance.md)

Following block shows the list of variance files  for the example used in this tutorial:

```
+--- fake_ID_01_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_02_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_03_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_04_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_05_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_06_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_07_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_08_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_09_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_10_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_11_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_12_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_13_fake_visit_1_task-rest_bold_timeseries_variance.txt
+--- fake_ID_14_fake_visit_1_task-rest_bold_timeseries_variance.txt

```