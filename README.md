## Conda Environment and download pre-trained model
1. You can import my conda environment by running this
```
conda env create -f environment.yml
```
2. You can also donwload the SAM Model here: https://drive.google.com/file/d/18H6d2ASXbJIL8V2cCiuCLEr8eZTNCYtH/view?usp=sharing


## Fintune Hyper-parameter
### First set is under if __name__ == "__main__":<br>
The input rgb image is in this folder: input_path/flag/single_image_num
```
input_path = "data/"
flag = "lerf_teatime"
single_image_num = 1
```
There are five different clip encoding methods for users to choose. The default one is SAM_SortBboxBackground_Interpolation
```
method = "SAM_SortBboxBackground_Interpolation"
output_path = "output_data/" + flag + "/" + method + "/"
```
This is the query text
```
text = "bear" 
```
This thr value is for outputing the filtered saliency map
```
thr = 0.8
```
### Second set is at the beginning of the generate_clip2d_SAM_SortBboxBackground_Interpolation(flag, image, output_path): <br>
w1 is for interpolating two overlapped masks
```
w1 = 0.99
```
sort is to sort the masks by area
```
sort = True
```
extend is to extend the area of the bbox of the mask. Larger extend value can allow user to include more context information
```
extend = 0
```
blur is to blur the background by gaussian filter
```
blur = (1,1,0)
```
### Third set is in mask_generator = SamAutomaticMaskGenerator(sam) <br>
Here you can follow the instructions in SAM official Github readme file, to fine-tune the parameters for SAM Model.
We are using the default ones.

## Run code
```
conda activate PL3DS_Baseline
python3 implicitObjDetection/segment-anything/main3_mac.py
```


