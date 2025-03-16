# HandFi
Construct 3D Hand Skeleton with Commercial WiFi.

The code can be found at https://github.com/HandFi/HandFi
I'm sorry I haven't been able to organize things because I was graduating and moving to a new place at that time.

## Inference with the pretrained model weights

download the dataset for inference from the link: https://drive.google.com/drive/folders/1IRPQcTVDaMZmQIO0taGbtNPH90VRGtMa?usp=sharing
put it into `./dataset/`

download the pretrained weights from the link: https://drive.google.com/drive/folders/1loLGPQXrsvjKBKvPww3l-BdmW92DhoZW?usp=sharing 
put it into `./runexp1` or your own run folder


run `csi_test.py` will inference the whole dataset with the pretrained model and calculate the quantitative results. 

Usage: `python csi_test.py --folder <folder store pth file> --bs <inference batch size> --dir <dataset folder> --save <save the inference data to local>`

can quickly run `sh csi_test.sh` for default

Output: mPA, IoU, mpjpe, pck of inference handnet via dataset

Data saving:
With set `--save` to 1, it will generate `gt_joints.pt` `gt_mask.pt` `pred_joints_2d.pt` `pred_joints_3d.pt` `pred_mask.pt`. We can plot to visual the groud truth and prediction with these.

## Visualization

There are a sample folder with each gesture two samples named `infersmall` in this link https://drive.google.com/drive/folders/1yCNydY3YaBTXko7q8v7zrXrIKKxv_xyb?usp=drive_link for quick visualize the experiment result (but you need to change the file name inside the plotjoints.py and plotmask.py to the corresponding)

The following code we still use the inference whole dataset result

### visual joints

run `plotjoints.py` will generate one sample with its ground truth and predicted joints in .png format

Usage: `python ./plotjoints.py --k <batch idx> --j <sample idx> --folder <folder store pt file> --exp <subdirectory to store the output image>`

can quickly run `sh plotjoints.sh` for default (plot first 16 samples in pt file)


### visual mask

run `plotmask.py` will generate one sample with its ground truth and predicted mask in .jpg format

Usage: `python ./plotmask.py --k <batch idx> --j <sample idx> --folder <folder store pt file> --exp <subdirectory to store the output image>`

can quickly run `sh plotmask.sh` for default (plot first 16 samples in pt file)

## Data Processing

### data collection

collect csi data to run `./DATACollection/CollectCSI/testv_1X3.m`

collect ground truth data (joints and mask) to run `./DATACollection/CollectGT/collect_GT.py`

### data cleaning

run matlab code in `./DATACleaning`

