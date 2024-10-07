Project Deocused
Synthetic Defocusing using Monocular Depth Estimation

Graded blurring of an image based on how far a point is from focus using just a single image with no extra data.
To achieve this, we generate a depth map for the image using machine learning.
Create blurred versions of the image in levels based on how far a point is from the depth of focus.
Stitch the different blurred images to create the final image with the selected point fully focused while points further away become more blurred.

How to Run
You'll need to set up TensorFlow v1 and OpenCV for the bare minimum run.

NOTE: Setting up TensorFlow v1 can be tricky, hence it is recommended to use a prebuilt docker image.

bash
Copy code
docker pull tensorflow/tensorflow:1.0.0-py3
GPU-specific images are also available.

Install a trained model for depth estimation:

bash
Copy code
sh ./depth/get_model.sh model_kitti depth/
This will download the model that gives the best results for the sample in the repo.

Call main.py with the model path and image path:

bash
Copy code
python main.py --model_path /path/to/model --image_path /path/to/image
The image will load up. Clicking anywhere sets that as the point of focus, regenerating the image.

I've pushed in the depth data for the sample images, so you can actually run the program without TensorFlow or a trained model for the sample images :)

Depth Estimation
We have used the method based on the paper Unsupervised Monocular Depth Estimation with Left-Right Consistency. They train a machine learning model to generate a depth map using just a single image.

How the Machine Learning Model is Trained (in Simple Terms):
The model is trained on a large set of stereo (left-right) images to generate a right image from a given left image.
By generating the right image, the model learns internally about the depth of various points in the image.

Once the model is trained, we can give it a simple image and it will be able to generate a depth map for that image.

The depth estimation code we have is a minimal stripped-down version just to run the model.

The Team
This was done as a final year project by Bhavesh Kalihari and Sanchit Singh.

Leave a star if you liked the project. :)