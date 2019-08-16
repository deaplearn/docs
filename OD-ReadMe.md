# About Object Detector 

> 	We use darknet to train custom tiny v3 model

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
		$ cd demo_train && ./trainModel-tiny.sh	

	
	> 	If we download images from other site, use tool labelImg to label the images.
	
	
3. Train with v3-tiny config file and pre-trained model

	> 	check script trainModel-tiny.sh on OIDv4_ToolKit/demo_train
	


4. Test the model. check https://github.com/deaplearn/yolo_opencv.git
	
	>	$ ./detect.sh [*.jpg | *.mp4]	[full | tiny | custom]

		Run ./detect.sh to test image/video 


5. Synthesize tarin images by python-opencv
	
	> 	check simple_synthesize.py in https://github.com/deaplearn/image_sample.git

		*  Download negative/background images from http://image-net.org.
			
			$python3 download_imgs.py

		*  Download and label object images with labelImg, save to './Lables/'. crop the target object.
			
			$python3 cutapple.py

		*  Generate sample images.
			
			$python3 simple_synthesize.py -bg ./neg/scale_100/ -t ./objects/scale/






