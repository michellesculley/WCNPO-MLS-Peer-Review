# Welcome to the github for the WCNPO MLS Peer Review!

## Finding Information:
You will find the 2023 Stock Assessment Report and supporting documents on catch, size and CPUE data under the [Assessment Documents](https://github.com/michellesculley/WCNPO-MLS-Peer-Review/tree/main/Assessment_Documents) folder.

Additional supporting information may be found in the [Supporting documents](https://github.com/michellesculley/WCNPO-MLS-Peer-Review/tree/main/Supporting_Documents) folder, these include previous assessment reports and background on the biology of WCNPO MLS.

During the peer review meeting the [Presentations google drive](https://drive.google.com/drive/folders/1aufDKI_ESp2vUjzZzxRuWCW6oIzFF615?usp=sharing) will contain the presentations being given by the BILLWG for you to follow along or references, as needed.

The 2023 WCNPO MLS base-case model can be found in the [Base-Case Model folder](https://github.com/michellesculley/WCNPO-MLS-Peer-Review/tree/main/Base-Case_Model). This model will run in about 20 minutes if you use the ss-basecase.par file for starting values. Please do not make any changes to the files in this folder.

You can also find the [Agenda](https://github.com/michellesculley/WCNPO-MLS-Peer-Review/blob/main/Agenda.docx) and a [draft schedule](https://docs.google.com/document/d/19wTXJ2JxXBolMv82FS5iCsV8jBrGUNtYEF10-A4kENo/edit?usp=drive_link) for the meeting.

## Running alternative models
To run additional model runs, you can use the R code found in the [Model-Runs folder](https://github.com/michellesculley/WCNPO-MLS-Peer-Review/tree/main/Model-Runs). Here is the workflow to use this process:

 + Open the Run_SS_Model.R document, and change the base.dir directory to relfect your local directory.
 + From there you can use the model.info list and the Build_all_ss function to run a model, run diagnostics, and print a report summarizing the model run. 
 + Inputs to the control file are found in two google sheets: CTL_inputs and CTL_parameters. R will ask you to authentic your access to these sheets the first time you run the code, and may ask to reauthorize access occationally if the token expires. There is where you can run alternative parameterizations for the model. And example using the 2019 biological parameters is set up for you.
 + To run the base model from this code:
   + ensure your model.info scenari and out_dir are both called "base" and your MAT_Options, GROWTH_Option, M_Option, LW_Option, and EST_Option are all set to "Base".
   + To run from the par set init_values to 1, then decide if you want to write the files, run the model, run any diagnostics, plot the r4ss plots, write the summary report file, and/or run any of the diagnostics in parallel.

If you would like to run an alternative parameterization, you will need to first edit the two CTL google sheets. For example, to run the model with the 2019 growth parameters: 
1. Add the 5 growth parameter lines to the MLS sheet in the CTL_params file, and input the new parameter intial values
2. Create a new sheet in the CTL_inputs file called "2019_Growth" and copy the MLS column of the base sheet to the new sheet
3. Adjust the appropriate values in this sheet and return to the Run_SS_Model.R file.
4. Under model.info, change the out_dir and scenario to "2019_Growth", and under the Build_all_SS function change the GROWTH_option to "2019_Growth" and make sure your init_param setting is 0 (don't use par file).
5. Run all the code in Run_SS_Model. A new folder under SS3 Runs should appear that contains the new model run and any options you choose to include (diagnostics, report file, plots).

A few usage notes:
It takes approximately one hour to run the WCNPO MLS basecase model without the appropriate par file. We have included the ss-basecase.par file so that you can use it to speed up the model run.

There is a known issue that sometimes when trying to run the R0_Profile in profile, the file copy function from r4ss doesn't copy the files correctly and R will exit the function. If this happens, delete the SR_LN(R0) folder from your SS3 Runs model folder and rerun the profile. The function should work properly on the second try. This appears to only occur if you are running the retrospectives and R0_profile consecutively. Troubleshooting this issue is ongoing.

## Github Disclaimer

This repository is a scientific product and is not official communication of the National Oceanic and Atmospheric Administration, or the United States Department of Commerce. All NOAA GitHub project code is provided on an ‘as is’ basis and the user assumes responsibility for its use. Any claims against the Department of Commerce or Department of Commerce bureaus stemming from the use of this GitHub project will be governed by all applicable Federal law. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by the Department of Commerce. The Department of Commerce seal and logo, or the seal and logo of a DOC bureau, shall not be used in any manner to imply endorsement of any commercial product or activity by DOC or the United States Government.
