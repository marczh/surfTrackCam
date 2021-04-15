# Zeno's simple stupid photo trap

## Basic arrangement

<img width="800" alt="image" src="https://user-images.githubusercontent.com/16016898/112650938-31da9780-8e4c-11eb-8eb8-910dc97fa0b2.png">


## required components

* Camera Body: Canon EOS M6 II
* Zoom Lens: at least 200mm
* Raspberry Pi 4 8GB
* [Adafruit Video Grabber](https://www.adafruit.com/product/4669)
* Solid State Relais: [Broadcom ASSR-1228-002E](https://ch.rs-online.com/web/p/halbleiterrelais/1894778/)

## Installation of Dev Board 4 GB
* Follow https://g.co/coral/setup 
* If you get a white screen while connecting the [serial port](https://coral.ai/docs/dev-board/serial-console), connect the power as well after connecting the serial port
* Make sure you have the  `cp210x` Kernel module loaded or compiled in
* Issue with version of [tflite_runtime](https://github.com/google-coral/tflite/issues/45)
* connecting a [USB camera](https://coral.ai/docs/dev-board/camera/#connect-a-usb-camera)
* [Example object tracker](https://github.com/google-coral/example-object-tracker)
* [Add an external SD card](https://github.com/f0cal/google-coral/issues/61) so you have more then 8 GB of space
* Vision Matrix support request for [OV5645](https://servicedesk.matrix-vision.com/servicedesk/customer/portal/1/MVSD-1274)
* Restart the Weston: `sudo systemctl restart weston`
* [Coral Camera](https://coral.ai/products/camera/)

## needed software
* sudo apt-get install python3-edgetpuvision
### run Frequently
* sudo apt-get update
* sudo apt-get dist-upgrade

## Useful commands
* `edgetpu_detect_server --model ${DEMO_FILES}/ssd_mobilenet_v2_face_quant_postprocess_edgetpu.tflite`
* `edgetpu_detect_server --model mobilenet_ssd_v2_coco_quant_postprocess_edgetpu.tflite --labels coco_labels.txt` for Object Tracking using [Example Object Tracker](https://github.com/google-coral/example-object-tracker)
* `edgetpu_detect_server --model mobilenet_ssd_v2_coco_quant_postprocess_edgetpu.tflite --labels coco_labels.txt --filter car,person,bicycle,bus,motorcycle`
* `edgetpu_detect_server --model mobilenet_ssd_v2_coco_quant_postprocess_edgetpu.tflite --labels coco_labels.txt --filter person --threshold 0.15 --print`
### create your own tflite file
* [Examples](https://coral.ai/examples/#code-examples/)
* [Retrain a classification model for Edge TPU using post-training quantization (with TF2)](https://colab.research.google.com/github/google-coral/tutorials/blob/master/retrain_classification_ptq_tf2.ipynb#scrollTo=RwywT4ZpQjLf)

## Research
* [https://github.com/AdaptiveCity/deepdish](Video object recognition, tracking and counting)
* [https://github.com/AdaptiveCity/deepdish/issues/1](Issues with Deepish)
