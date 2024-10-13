# MRNet

Dataset from Clinical Hospital Centre Rijeka, Croatia, originally appears in:

I. Štajduhar, M. Mamula, D. Miletić, G. Unal, Semi-automated detection of anterior cruciate ligament injury from MRI, Computer Methods and Programs in Biomedicine, Volume 140, 2017, Pages 151–164. (http://www.riteh.uniri.hr/~istajduh/projects/kneeMRI/data/Stajduhar2017.pdf)

## Setup

`bash download.sh` (caution: downloads ~6.68 GB of data)

`conda env create -f environment.yml`

`source activate mrnet`

## Train

`python train.py --rundir [experiment name] --diagnosis 0 --gpu`

- diagnosis is highest diagnosis allowed for negative label (0 = injury task, 1 = tear task)
- arguments saved at `[experiment-name]/args.json`
- prints training & validation metrics (loss & AUC) after each epoch
- models saved at `[experiment-name]/[val_loss]_[train_loss]_epoch[epoch_num]`

## Evaluate

`python evaluate.py --split [train/valid/test] --diagnosis 0 --model_path [experiment-name]/[val_loss]_[train_loss]_epoch[epoch_num] --gpu`

- prints loss & AUC

## README-2 (Implementation Hints)

list of installed packages in mr_env are,

```
conda list
# packages in environment at /home/C00579118/miniconda3/envs/mrnet_env:
#
# Name                    Version                   Build  Channel
_libgcc_mutex             0.1                 conda_forge    conda-forge
_openmp_mutex             4.5                       2_gnu    conda-forge
blas                      1.0                         mkl  
bzip2                     1.0.8                h5eee18b_6  
ca-certificates           2024.8.30            hbcca054_0    conda-forge
certifi                   2021.5.30        py36h06a4308_0  
colorama                  0.4.4              pyhd3eb1b0_0  
cudatoolkit               11.3.1               h2bc3f7f_2  
cycler                    0.11.0             pyhd3eb1b0_0  
dataclasses               0.8                pyh4f3eec9_6  
dbus                      1.13.18              hb2f20db_0  
expat                     2.4.4                h295c915_0  
ffmpeg                    4.3                  hf484d3e_0    pytorch
fontconfig                2.14.1               hef1e5e3_0  
freetype                  2.12.1               h4a9f257_0  
giflib                    5.2.1                h5eee18b_3  
glib                      2.63.1               h5a9c865_0  
gmp                       6.2.1                h295c915_3  
gnutls                    3.6.15               he1e5248_0  
gst-plugins-base          1.14.0               hbbd80ab_1  
gstreamer                 1.14.0               hb453b48_1  
icu                       58.2                 he6710b0_3  
intel-openmp              2022.0.1          h06a4308_3633  
joblib                    1.0.1              pyhd3eb1b0_0  
jpeg                      9e                   h5eee18b_3  
kiwisolver                1.3.1            py36h2531618_0  
lame                      3.100                h7b6447c_0  
lcms2                     2.12                 h3be6417_0  
ld_impl_linux-64          2.43                 h712a8e2_1    conda-forge
libblas                   3.9.0            14_linux64_mkl    conda-forge
libcblas                  3.9.0            14_linux64_mkl    conda-forge
libedit                   3.1.20230828         h5eee18b_0  
libffi                    3.2.1             hf484d3e_1007  
libgcc                    14.1.0               h77fa898_1    conda-forge
libgcc-ng                 14.1.0               h69a702a_1    conda-forge
libgfortran-ng            7.5.0               ha8ba4b0_17  
libgfortran4              7.5.0               ha8ba4b0_17  
libgfortran5              14.1.0               hc5f4f2c_1    conda-forge
libgomp                   14.1.0               h77fa898_1    conda-forge
libiconv                  1.16                 h5eee18b_3  
libidn2                   2.3.4                h5eee18b_0  
liblapack                 3.9.0            14_linux64_mkl    conda-forge
libpng                    1.6.39               h5eee18b_0  
libstdcxx-ng              9.3.0               h6de172a_19    conda-forge
libtasn1                  4.19.0               h5eee18b_0  
libtiff                   4.2.0                h2818925_1  
libunistring              0.9.10               h27cfd23_0  
libuv                     1.48.0               h5eee18b_0  
libwebp                   1.2.4                h11a3e52_1  
libwebp-base              1.2.4                h5eee18b_1  
libxcb                    1.15                 h7f8727e_0  
libxml2                   2.9.14               h74e7548_0  
lz4-c                     1.9.3                h295c915_1  
matplotlib                3.3.4            py36h06a4308_0  
matplotlib-base           3.3.4            py36h62a2d02_0  
mkl                       2022.0.1           h06a4308_117  
ncurses                   6.4                  h6a678d5_0  
nettle                    3.7.3                hbbd107a_1  
numpy                     1.19.5           py36hfc0c790_2    conda-forge
olefile                   0.46               pyhd3eb1b0_0  
openh264                  2.1.1                h4ff587b_0  
openssl                   1.1.1w               h7f8727e_0  
pcre                      8.45                 h295c915_0  
pillow                    8.3.1            py36h5aabda8_0  
pip                       10.0.1                   pypi_0    pypi
pyparsing                 3.0.4              pyhd3eb1b0_0  
pyqt                      5.9.2            py36h05f1152_2  
python                    3.6.11          h4d41432_2_cpython    conda-forge
python-dateutil           2.8.2              pyhd3eb1b0_0  
python_abi                3.6                     2_cp36m    conda-forge
pytorch                   1.10.2          py3.6_cuda11.3_cudnn8.2.0_0    pytorch
pytorch-mutex             1.0                        cuda    pytorch
qt                        5.9.7                h5867ecd_1  
readline                  8.2                  h8228510_1    conda-forge
scikit-learn              0.24.2           py36ha9443f7_0  
scipy                     1.5.3            py36h9e8f40b_0    conda-forge
setuptools                40.2.0                   pypi_0    pypi
sip                       4.19.8           py36hf484d3e_0  
six                       1.16.0             pyhd3eb1b0_1  
sqlite                    3.33.0               h62c20be_0  
threadpoolctl             2.2.0              pyh0d69192_0  
tk                        8.6.14               h39e8969_0  
torchaudio                0.10.2               py36_cu113    pytorch
torchvision               0.11.3               py36_cu113    pytorch
tornado                   6.1              py36h27cfd23_0  
tqdm                      4.63.0             pyhd3eb1b0_0  
typing_extensions         4.1.1              pyh06a4308_0  
wheel                     0.31.1                   pypi_0    pypi
xz                        5.4.6                h5eee18b_1  
zlib                      1.2.13               h5eee18b_1  
zstd                      1.5.2                ha4553b6_0
```

## Model Implementation hints,

To train the model for abnormality detection, ACL tear detection, and meniscus tear detection in sequence, you can follow a structured approach. The idea is to train the model on one task at a time (starting with abnormality detection), save the model weights, and then use those weights to fine-tune for ACL and meniscus detection.

## General Workflow

1. Train on Abnormality Detection:
    * Run the first command to train the model on abnormality detection and save the model weights (e.g., abnormal_model.pth).
2. Fine-tune on ACL Tear Detection:
    * Once the abnormal model is trained, use it as the base to fine-tune for ACL detection. Save the fine-tuned ACL model weights (e.g., acl_model.pth).
3. Fine-tune on Meniscus Tear Detection:
    * Similarly, use the abnormal model as the base and fine-tune it for meniscus detection.

## Train model,

1. ``python train.py --rundir`` **<path_to_save_abnormal_model>** ``--task abnormal --backbone alexnet --epochs 50 --learning_rate 1e-5 --gpu``

Ex: Saved in:MRNet-Baseline/abnormal,  ``python train.py --rundir /home/C00579118/MRNet-Baseline/abnormal --task abnormal --epochs 50 --gpu --learning_rate 1e-4``


4. ``python train.py --rundir`` **<path_to_save_acl_model>** ``--task acl --backbone alexnet --epochs 50 --learning_rate 1e-5 --gpu --abnormal_model`` **<path_to_abnormal_model_weights.pth>**

Ex: Saved in:MRNet-Baseline/acl, ``python train.py --rundir /home/C00579118/MRNet-Baseline/acl --task acl --backbone alexnet --epochs 50 --learning_rate 1e-5 --gpu --abnormal_model /home/C00579118/MRNet-Baseline/abnormal/val0.1975_train0.1731_epoch21.pth``


7. ``python train.py --rundir`` **<path_to_save_meniscus_model>** ``--task meniscus --backbone alexnet --epochs 50 --learning_rate 1e-5 --gpu --abnormal_model`` **<path_to_abnormal_model_weights.pth>**

Ex: Saved in:MRNet-Baseline/meniscus, ``python train.py --rundir /home/C00579118/MRNet-Baseline/meniscus --task meniscus --backbone alexnet --epochs 50 --learning_rate 1e-5 --gpu --abnormal_model /home/C00579118/MRNet-Baseline/acl/val0.1295_train0.0716_epoch26.pth``

## Evaluate model

``python evaluate.py --model_path`` **<model_path>** ``--split <split_type> --diagnosis <diagnosis_type> --gpu``

These finds **Valid loss and Valid AUC**

``python evaluate.py --model_path /home/C00579118/MRNet-Baseline/meniscus/val0.2594_train0.1442_epoch17.pth --split valid --diagnosis 0 --gpu``

``python evaluate.py --model_path /home/C00579118/MRNet-Baseline/meniscus/val0.2594_train0.1442_epoch17.pth --split valid --diagnosis 1 --gpu``

``python evaluate.py --model_path /home/C00579118/MRNet-Baseline/meniscus/val0.2594_train0.1442_epoch17.pth --split valid --diagnosis 2 --gpu``

## N. B.
To print the **Accuracy** use ``evaluate2.py``

