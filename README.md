# multimodal BEV thesis project


The experiments are conduct on Alvis platform.

The checkpoint files are not included in github due to the limitation of storage space.


### 1. Data Files
#### 1.1. 5% of nuScenes dataset 
Data path:  
/mimer/NOBACKUP/groups/multimodal/v1.0-mini-5p/  

Details of sences:  
train: /mimer/NOBACKUP/groups/multimodal/data_split/train_5p.csv  
valid: /mimer/NOBACKUP/groups/multimodal/data_split/val_5p.csv  

#### 1.2. Full validation of nuScenes dataset 
Data path:  
/mimer/NOBACKUP/groups/multimodal/v1.0-mini-100v/  

Details of sences:  
/mimer/NOBACKUP/groups/multimodal/data_split/val_100v.csv

#### 1.3. 5% geo dataset, 40 scenes for train and 210 scenes for validation
Data path:   
/mimer/NOBACKUP/groups/multimodal/v1.0-mini-geo5p/  

Details of sences:    
train: /mimer/NOBACKUP/groups/multimodal/data_split/geo_train_5p.csv  
valid: /mimer/NOBACKUP/groups/multimodal/data_split/geo_val.csv  

### 2. Models

The checkpoint files are storaged in path ./work_dirs/Fusion_0075_refactor/ for each model folder.   
Eeach model has 6 checkpoint files (since we have 6 epochs in training stage).

#### 2.1. BS1
Model path:  
/mimer/NOBACKUP/groups/multimodal/trained_model/bs1_select  
Checkpoint file:  
https://pan.baidu.com/s/11eXhMg8zpIGA2W20M1IFfw?pwd=1111 


#### 2.2. BS2
Model path:  
/mimer/NOBACKUP/groups/multimodal/trained_model/bs2_select  
Checkpoint file:  
https://pan.baidu.com/s/1NSZSYQZOwzcIeiUoOXZgVg?pwd=1111 


#### 2.3. BS1+PE
Model path:  
/mimer/NOBACKUP/groups/multimodal/trained_model/bs1_pe_select  
Checkpoint file:  
https://pan.baidu.com/s/1HT99uLJHL6Gcop2HBaL6FA?pwd=1111 


#### 2.4. BS2+PE
Model path:  
/mimer/NOBACKUP/groups/multimodal/trained_model/bs2_pe_select  
Checkpoint file:  
https://pan.baidu.com/s/1sYPoWudQ3RD9SH2iuiY0PQ?pwd=1111 


#### 2.5. BS1+IED
Model path:  
/mimer/NOBACKUP/groups/multimodal/trained_model/bs1_ied_select  
Checkpoint file:  
https://pan.baidu.com/s/1VJ1G4s9E9uy2Jir0-qmPRg?pwd=1111 


#### 2.6. BS2+IED
Model path:  
/mimer/NOBACKUP/groups/multimodal/trained_model/bs2_ied_select  
Checkpoint file:  
https://pan.baidu.com/s/10nMIwo6Bmuqm3ZbxwXBz-Q?pwd=1111 


#### 2.7. BS1+PE+IED
Model path:  
/mimer/NOBACKUP/groups/multimodal/trained_model/bs1_pe_ied_select  
Checkpoint file:  
https://pan.baidu.com/s/1p2IzEz3AmMDelZPtHtXwEw?pwd=1111 

#### 2.8. BS2+PE+IED
Model path:  
/mimer/NOBACKUP/groups/multimodal/trained_model/bs2_pe_ied_select  
Checkpoint file:  
https://pan.baidu.com/s/1TzvFatSS34KvWekfCYTDLQ?pwd=1111 


### 3. Offical experimental setting of DeepInteraction 
https://github.com/fudan-zvg/DeepInteraction

### 4.Docker settings on Alvis
The docker environment is generated according to the setting of DeepInteraction on its github page.  
The docker file on Alvis:  
/mimer/NOBACKUP/groups/multimodal/bev_image_dev/  

For example, if one want to activate the docker and use  5% nuScenes dataset:  
#### Step1. Activate docker
apptainer shell --nv --fakeroot -B  /mimer/NOBACKUP/groups/multimodal/v1.0-mini-5p:/root/v1.0-mini-5p /mimer/NOBACKUP/groups/multimodal/bev_image_dev/

#### Step2.Activate conda env
source activate  
conda activate bev  

Then we can train or valid the model according to command provided on github page of DeepInteraction.  

### 5. How to switch various data splittings
#### 5.1. Modify splits.py of nuscene  package
##### Step1. Activate docker with "--writable" 
apptainer shell --nv --fakeroot --writable /mimer/NOBACKUP/groups/multimodal/bev_image_dev/  

##### Step2.Activate conda env
source activate  
conda activate bev  

##### Step3. Modify splits.py
Change to nuscenes directory.  
cd /opt/conda/envs/bev/lib/python3.7/site-packages/nuscenes/utils/  

We have several different backup files of splits.py:  
splits.py_5p_backup : 5% of nuScenes dataset   
splits.py_100v_backup : Full validation of nuScenes dataset   
splits.py_geo_backup : 5% geo dataset  

The backup files are stored in path:  
data_splitting_splits_file  

Simply overwrite the splits.py as requried.  

#### 5.2. Modify model config
Edit the file:  projects/configs/nuscenes/Fusion_0075_refactor.py  
If use 5% of nuScenes dataset, the modify the "data_root" line as  : data_root = '/root/v1.0-mini-5p/'  





