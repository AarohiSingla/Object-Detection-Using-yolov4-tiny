# Object-Detection-Using-yolov4-tiny


# Open convert_darknet_to_tensorflow_model. And do the below mentioned changes

1- Copy and paste your customdetector.weights file into the 'data' folder

2- Copy and paste your customdetector.names into the 'data/classes/' folder.

3- The only change within the code you need to make in order for your custom model to work is on line 14 of 'core/config.py' file. 
Update the code to point at your customdetector.names file

Open save_model.py file and replace the weights with your custom weight file

## Commands to run

# yolov4-tiny  (converting darknet model into TensorFlow model)
python save_model.py --output ./checkpoints/yolov4-tiny-416 --input_size 416 --model yolov4 --framework tflite  --tiny

#  convert yolov4-tiny  tensorflow model into tflite
python convert_tflite.py --weights ./checkpoints/yolov4-tiny-416 --output ./checkpoints/yolov4-tiny-416.tflite

# yolov4 quantize float16
python convert_tflite.py --weights ./checkpoints/ yolov4-tiny-416 --output ./checkpoints/yolov4-416-fp16.tflite --quantize_mode float16


# Perform Detections
python detect.py --weights ./checkpoints/yolov4-tiny-416.tflite --size 416 --model yolov4 –images testimg.jfif  --output ./output/outputtflite.jpg --framework tflite


# Android App for Object Detection
### Download that code from this link:  https://github.com/tensorflow/examples/tree/master/lite/examples/object_detection/android

