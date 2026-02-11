# SliceVQA

This repository hosts a set of questions designed to compare performances of medical VQA models.

The benchmark is inspired by radiologists' workflow who inspect 3D CT-scans by sliding through their axial slices. We built a set of questions each bound to a specific slice within a given CT-scan. We have also built multi-scan questions that require to compare a pair of slices from two different volumes. The questions in this dataset focus on tasks requiring fine-grained spatial analysis of the images (e.g. measurements). Commonly, radiologists perform CT-scan readings by sliding through the axial slices. Therefore, they may have a question relative to a specific slice while analyzing the entire volume. SliceVQA addresses this setting as it contains questions localized to given slices while enabling the access to the complete CT-scan for additional context. 

These questions are built upon two publicly available datasets of CT-Scans paired with segmentation masks to be used as images:
* *AMOS*, a multi-organ segmentation dataset.
* The `liver` task of the *Medical Segmentation Decathlon (MSD)* dataset including CT-scans and associated segmentation masks of the liver and hepatic lesions.

The questions were generated using templates automatically filled by leveraging the ground-truth segmentation masks.

 The questions are stored in 4 CSV files:
 - `questions/slicevqa_amos_single.csv`: the single image questions built upon *AMOS*.
 - `questions/slicevqa_liver_single.csv`: the single image questions built upon *MSD*.
 - `questions/slicevqa_amos_multi.csv`: the image pair questions built upon *AMOS*.
 - `questions/slicevqa_liver_multi.csv`: the image pair questions built upon *MSD*.

Each of these files contains 300 questions, there is a total of **1200 questions**.

## Single Image Questions

The CSV files of single image questions present the following columns:
* `scan_idx`: the index of the volume in the source dataset (AMOS or MSD).
* `label`: the segmentation label that has been used to infer the result of the question.
* `slice_index`: the index of sthe lice of which the question is about.
* `question_type`: the category of the question.
* `question`: the text of the question.
* `spacing_info` the spacing in millimeters of the 2D axial slice. 

The questions types are the following:
* `average_intensity` e.g., "What is the average intensity of aorta in this image?"
* `diameter` e.g., "What is the aorta's diameter in millimeters as shown in this image?"
* `extreme_position` (only for AMOS) e.g., "Which organ is left most in this image?"
* `is_brighter` e.g., "Does the right kidney appear brighter compared to the left kidney?"
* `ìs_function_present` e.g., "Does the image show an organ involved in regulating stress hormones?"
* `is_healthy` (only for MSD liver) e.g., "Is the liver healthy in this image?"
* `is_larger` e.g., "Is gallbladder larger than postcava?"
* `relative_position` e.g. "What organ is located on the left side of the aorta in this image?"
* `surface_area` e.g., "What is the aorta's surface area in square millimeters as shown in this image?"
* `target_count` e.g. "How many liver tumors are there in this image?"


## Image Pair Questions

The CSV files of image pair questions present the following columns:
* `scan_idx_1`: the index of the first volume in the source dataset (AMOS or MSD).
* `scan_idx_2`: the index of the second volume in the source dataset (AMOS or MSD).
* `slice_index_1`: the index of the slice of the first volume which the question is about.
* `slice_index_2`: the index of the slice of the second volume which the question is about.
* `label`: segmentation label that has been used to infer the result of the question.
* `question_type`: the category of the question.
* `question`: the text of the question.
* `spacing_info_1` the spacing in millimeters of the 2D axial slice of the first volume.
* `spacing_info_2` the spacing in millimeters of the 2D axial slice of the second volume. 

The questions types are the following:
* `common_organs`, (only for AMOS) e.g., "Is there at least 2 common organs displayed in both images?"
* `diameter_evolution`, e.g., "What is the difference in diameter (in mm) between the largest liver tumor in the first image and the largest one in the second image?"
* `is_bright_compare`, e.g., "Is liver brighter in the first image than the second image?"
* `is_larger_comparison`, e.g., "Is aorta bigger in the first image than the second image?"
* `is_present_target_both`, e.g., "Is there liver in both images?"
* `surface_evolution`, e.g., "What is the difference in total surface area in mm2 of liver tumor between the first and second image?"

## License

The content of this repository is shared under the **Creative Commons Attribution ShareAlike 4.0 License**.

## Citations

*AMOS*:
> Ji, Y., et al, "AMOS: A Large-Scale Abdominal Multi-Organ Benchmark for Versatile Medical Image Segmentation," in Advances in Neural Information Processing Systems, 2022, pp. 36722–36732.

*Medical Segmentation Decathlon*:
> Antonelli, M., Reinke, A., Bakas, S. et al. The Medical Segmentation Decathlon. Nat Commun 13, 4128 (2022). https://doi.org/10.1038/s41467-022-30695-9

