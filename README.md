# Emotion-Recognition Using EEG Signals. 
An official repository for "A Deep Learning Approach for Emotion Recognition using Physiological Signals"

# Table of Contents
- [Instructions To use the code](#Instructions-To-use-the-code)

## Instructions To use the code

1. The .ipynb notebooks are for pedagogical reasons on how each part of the code works.
2. the .py files are for effortlessly reproducing the results.

#### Now let's look at how we can reproduce the results using the Python scripts. 

**Step 1**: Use the `pre-processing .ipynb` to get the numpy files of all the subjects present in the dataset.

**Step 2**: now run the script `data.py` to. 

```
!python data.py --input_directory "/content/drive/MyDrive/project_eeg/data_preprocessed_python" \
                --num_subjects 5\
                --output_directory "./"
```
here the `data.py` file takes 3 arguments. 
1. input directory to the pre-processed files.
2. select the number of subjects that we want (1-30)
3. An output directory that can be mentioned. we can also skip this part and a default folder would be created called 'Data_selected`

**Step 3**: run the script `data-split.py`.

```
!python data-split.py --input_directory "/content/drive/MyDrive/project_eeg/" \
                       --output_directory "/content/drive/MyDrive/project_eeg/output"
```
This step takes the select data and then converts the data into train and test split numpy files. The default output directory is named as TrainTestfiles

**Step 4**: 2 models are being proposed here. To run the model one (CNN) run the script `cTrain.py`. this code performs 5-fold cross-validation  on training data that is 85% and performs a test on 15% of the data. 

```
!python cLTrain.py --data_directory "/content/drive/MyDrive/project_eeg" --emotion 0
```
For training the network we need to provide where the data is present that is data directory and also select the emotion that we want to train our model for. 

- emotion 0 - Arousal
- emotion 1 - Valence
- emotion 2 - Dominance
- emotion 3 - Liking

After training the cnn model the results on cross-validation and the model's weights are saved in a new folder named results. it also contains a confusion matrix on the test data. 

**Step 5**: To run another model (CNNLSTM) run the script `cLtrain.py`. this code performs the same as ctrain.py however, we use a new proposed model here. 

After training the cnnlstm model the results on cross-validation and the model's weights are saved in a new folder named Lresults. it also contains a confusion matrix on the test data. 

**Step 6** If you want to train the proposed models without cross-validation you can just run the train.py file to train on the cnn model. the commands are the same as steps 4 and 5.
