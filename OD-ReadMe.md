# About Object Detector 

> 	We use yolo-v3 to train custom tiny v3 model

> 	reference
	https://github.com/deaplearn/darknet.git


1. Prepare Custom Images, you can download from https://storage.googleapis.com/openimages/web/download.html

	> 	Use tools like https://github.com/deaplearn/OIDv4_ToolKit, generate lable info.

	> 	Or Label images yourself https://github.com/tzutalin/labelImg, then convert them to yolo format https://github.com/my-nlp/convert2Yolo.git

2. Fetch train and validation datas.
	
	> 	If we use OIDv4_ToolKit, download train and validation classes images. 

		Take class 'Apple' for example, follow this steps to train your own object model
		$ echo Apple > classes.txt
		$ python3 main.py downloader -y --classes classes.txt --image_IsGroupOf 0 --limit 10 --type_csv train
		$ python3 main.py downloader -y --classes classes.txt --image_IsGroupOf 0 --limit 10 --type_csv validation
		$ ./generateManifest.sh
		$ cd demo_train && ./trainModel.sh	

	
	> 	If we download images from other site, use tool labelImg to label the images.
	
	
3. Train with v3-tiny config file and pre-trained model

	> 	check script trainModel.sh on OIDv4_ToolKit/demo_train
	

4. Use opencv load trained model and it's config info to detect object.
	
	>	check https://github.com/deaplearn/yolo_opencv.git

		$ ./detect.sh [*.jpg] [*.mp4] [live]


5. Use opencv_createsamples to generate train images. Do as follow steps

	(also check https://github.com/deaplearn/image_sample.git)

		*  Prepare compile environment
			
				```
					sudo su
					apt-get update
					apt-get upgrade
					apt-get install git
					Compiler: 
						apt-get install build-essential
					Libraries: 
						apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
					Python bindings and such:
						apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libdc1394-22-dev
					OpenCV development library:
						apt-get install libopencv-dev
				```

		*  Download and compile the opencv. 
			https://github.com/deaplearn/opencv.git

		*  Download negative/background images from http://image-net.org.

		*  Download and label object images. crop the target object.

		*  Generate sample images.

		*  Convert label info to yolo format.






