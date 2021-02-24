# Dynamic-MKP-Datasets-Generator
A deterministic Dynamic MKP dataset generator command line interface program.

Two static MKP benchmark libraries included as a starting point: OR and GK.


## GenerateDataset command
Generate dataset command will generate an entire dynamic dataset for each static dataset provided in the command arguments. One or more files has to be pointed for dataset creation for example: `DatasetGeneratorCli.exe generatedataset ./datasets/gk/gk01.dat` or `DatasetGeneratorCli.exe generatedataset ./datasets/gk/gk01.dat ./datasets/gk/gk02.dat`

The number of Dynamic dataset states is chosen with option `-s| --states` the default number of states is 100 for example `DatasetGeneratorCli.exe generatedataset ./datasets/gk/gk01.dat -s 53` to generate 53 dynamic dataset states. The number does not include the initial dataset.

The difference from one state to another is controlled using the "State adjustment Magnitude (SAM)" option `-sam| --stateAdjustmentMagnitude`, which is a percentage of the maximum scale applied to each item profit and item weights when generating a new state. SAM value is limited between 0 and 1; the default is 0.05. Generally, SAM should not be more than 0.2 as with higher SAM values, dataset generator creates states that are decreasingly similar one to another. Example: `DatasetGeneratorCli.exe generatedataset ./datasets/gk/gk01.dat -sam 0.1` to generate Dynamic dataset with 0.1 SAM.

Generated datasets will be placed in the folder `./generatedDynamicDatasets/{SAM setting}/{dataset file name}`

## GenerateNextState command
Generate next state command will add an additional state to the existing Dynamic MKP dataset. Example: `GenerateNextState ./generatedDynamicDatasets/SAM-0.05/gk01` this will add one state at the end of the dataset.

Similarily to GenerateDataset command, the SAM can be chosen with the option `-sam| --stateAdjustmentMagnitude`. Default SAM is 0.05

If more than one state needed to add to the dataset the option `-s| --states` can be used. Default number of states is 1.
