# object_detection_resnet50
###### (Input images are under ./keras_retinanet/CSV)

cd object_detection_resnet50

pip install numpy --user ## for latest numpy

pip install . --user

python setup.py build_ext --inplace

###### Finish the above and then proceed.

## check inputs
python keras_retinanet/bin/debug.py csv keras_retinanet/CSV/train_annotations.csv keras_retinanet/CSV/classes.csv

## model training
python keras_retinanet/bin/train.py --batch-size 2 --epochs 20 --steps 100 --backbone resnet50 --gpu 2 csv keras_retinanet/CSV/train_annotations.csv keras_retinanet/CSV/classes.csv --val-annotations keras_retinanet/CSV/val_annotations.csv

## convert to inference model
retinanet-convert-model snapshots/resnet50_csv_20.h5 retinanet_inference.h5

## model testing
test.ipynb
