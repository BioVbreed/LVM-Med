# Training Faster RCNN model using LVM-Med (R50)

## 1. Activate conda environment
```bash
conda activate vin
```

## 2. Convert dataset to Coco format
```bash
python convert_to_coco.py # Note, please check again if this file is correct. Don't run this file again.
```

## 3. Set train, valid, test folders
Edit [`base_config_track.py`](/Object_Detection/base_config_track.py) at:
+ Lines `11`, `12` for training set
+ Lines `60`, `61` for valid set
+ Lines `65`, `66` for test set
+ Lines `86` for folder store models.

## 4. Train model and test
```bash
bash command.sh
```

## 5. Train from current epochs:
```bash
CUDA_VISIBLE_DEVICES=5 python finetune_object_detect.py --experiment-name 'lvm-med-r50' --weight-path ./checkpoints/converted_vissl_ssl_graph_large.torch --batch-size 16 --optim adam --clip 1 --lr 0.0001 --epochs 40 --labeled-dataset-percent 1.0 --resume
```