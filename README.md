**I. Introduction**
_Overview of the Project_
The Smart Security Camera System proposed in this project uses Python-based computer vision techniques to detect high-speed movements and is intended to track cars, vans, and E-scooters on campus. The goal of this proactive monitoring is to reduce hazards without requiring continual human supervision. The report outlines the features, requirements, and design of the system and shows how it can be used to detect and avoid safety issues. This project aims to create a watchful and safe atmosphere, demonstrating how safety and technology may coexist in the university landscape.
**
II. Research and Literature Review**
_A. Review of Existing Solutions for Pedestrian Safety Enhancement_
Pedestrian safety is a critical concern, and several existing solutions leverage technology to enhance safety on walkways and campuses. In the context of the University of Northampton's need for a smart security camera system to detect speedy movements, we explore current technologies and solutions that contribute to pedestrian safety enhancement.

_Surveillance Camera Systems:_
Traditional surveillance camera systems are widely used for monitoring public spaces. These systems can capture and record video footage, providing a passive means of surveillance. However, their effectiveness in detecting and responding to speedy movements may be limited. The challenge lies in distinguishing between normal walking speeds and potentially hazardous situations.

_Computer Vision and Object Detection:_
Modern computer vision techniques have been applied to enhance pedestrian safety. Object detection algorithms, such as YOLO (You Only Look Once) and Faster R-CNN (Region-based Convolutional Neural Network), can identify and track objects, including pedestrians, in real-time. These systems can be integrated with surveillance cameras to provide more intelligent monitoring.

_Intelligent Traffic Management Systems:_
Some urban areas employ intelligent traffic management systems that use cameras and sensors to monitor and manage vehicular traffic. These systems often include features such as automatic license plate recognition (ALPR) and speed detection. While primarily designed for road traffic, these technologies can be adapted for pedestrian safety by adjusting parameters and integrating with pedestrian walkways.

_Smart Crosswalks and Traffic Lights:_
Innovations in urban planning include smart crosswalks equipped with sensors and cameras. These systems can detect pedestrians approaching crosswalks and adjust traffic light timings accordingly. While more focused on road intersections, similar principles could be applied to pedestrian pathways within the campus to enhance safety.

_Mobile Applications for Pedestrian Safety:_
Some applications leverage the ubiquity of smartphones to enhance pedestrian safety. These apps may provide real-time information on traffic conditions, suggest safer routes, or include features like panic buttons for emergency situations. While not directly related to camera systems, integrating such applications with surveillance technology could offer a holistic approach to safety.

_Crowdsourced Safety Data:_
Crowdsourcing platforms enable users to report safety-related incidents and hazards. Integrating such systems with campus security could provide real-time information on potential safety concerns. While not a direct technological solution, it complements surveillance technology by leveraging the collective awareness of the community.

_B. Relevant Studies and Technologies in Speed Detection Systems_

_Object Detection Algorithms:_

At the heart of computer vision in security camera systems lies the capability for object detection. Advanced algorithms such as YOLO (You Only Look Once) and Faster R-CNN (Region-based Convolutional Neural Network) have revolutionized real-time object detection. These algorithms can be trained to recognize a myriad of objects, including pedestrians, vehicles, and potential safety concerns, providing a robust foundation for surveillance systems.
Object detection involves drawing bounding boxes around objects of interest within an image, a task that presents challenges due to varying spatial locations and aspect ratios of objects. Standard convolutional networks with fully connected layers are not well-suited for this variable output length problem. 

_R-CNN_
R-CNN, proposed by (Girshick, 2014), tackles the challenge by using selective search to extract 2000 region proposals from an image. These proposals are then fed into a convolutional neural network, acting as a feature extractor, to produce a 4096-dimensional feature vector. The features are used to train an SVM to classify the object's presence within the proposal, and offset values refine the bounding box. However, R-CNN has limitations, such as time-consuming training and fixed selective search, prompting the development of Faster R-CNN.

_Fast R-CNN_
Fast R-CNN, introduced by the same author, improves upon R-CNN by generating a convolutional feature map from the entire image, identifying region proposals, and reshaping them with RoI pooling. This eliminates the need to feed 2000 region proposals individually, making Fast R-CNN significantly faster in training and testing sessions. Despite its advancements, the dependence on selective search remains a bottleneck, leading to the evolution of Faster R-CNN. (Girshick, 2015)

_Faster R-CNN_
Faster R-CNN, presented by (Ren, 2017), eliminates selective search by using a separate network to predict region proposals. The predicted proposals are then reshaped and used for classification and bounding box prediction. This innovation results in a substantial improvement in test-time speed, making Faster R-CNN suitable for real-time object detection.
While Faster R-CNN offers notable improvements, the paradigm shift arrives with YOLO. YOLO employs a single convolutional network to predict bounding boxes and class probabilities simultaneously, avoiding the need for region proposals. By splitting the image into a grid and predicting multiple bounding boxes within each grid cell, YOLO achieves remarkable speed (45 frames per second as mentioned earlier). However, YOLO struggles with small objects due to spatial constraints.

_YOLO_
The YOLO (You Only Look Once) approach to object detection introduces a novel methodology by framing object detection as a regression problem, predicting spatially separated bounding boxes and associated class probabilities directly from full images. In contrast to prior methods that repurpose classifiers for detection, YOLO employs a unified architecture, treating the entire detection pipeline as a single neural network. This enables end-to-end optimization directly on detection performance, leading to an exceptionally fast and efficient object detection system. (Joseph Redmon, 2016)
The base YOLO model processes images in real-time at an impressive rate of 45 frames per second. Additionally, a smaller version of the network, known as Fast YOLO, achieves an astonishing processing speed of 155 frames per second while still surpassing other real-time detectors in terms of mean average precision (mAP). Despite potentially making more localization errors compared to state-of-the-art systems, YOLO demonstrates a reduced likelihood of predicting false positives on background. Moreover, YOLO exhibits remarkable generalization capabilities, outperforming other detection methods, such as DPM and R-CNN, when transitioning from natural images to diverse domains, including artwork.

Figure 1 - Qualitative Results. YOLO running on sample artwork and natural images from the internet. It is mostly accurate although it does think one person is an airplane.
This innovative and unified approach to object detection not only significantly improves speed but also demonstrates robust performance in various scenarios, showcasing YOLO as a pioneering solution in the field of computer vision.
In conclusion, the evolution of object detection algorithms from R-CNN to Faster R-CNN and, finally, YOLO represents a progression towards more efficient and faster solutions.
 
Figure 2 -  (Joseph Redmon, 2016)

_Facial Recognition:_

Facial recognition technology, another notable application of computer vision, has found its place in security camera systems for identifying and tracking individuals. While promising in enhancing campus security by monitoring entrances and exits, the implementation of facial recognition warrants careful consideration of ethical and privacy implications.

_Automatic License Plate Recognition (ALPR):_

ALPR systems leverage computer vision to interpret license plate information from vehicles. Integrating ALPR with security camera systems enhances the monitoring of vehicular traffic on campus, contributing to both safety and security measures.

_Object Tracking:_

Object tracking algorithms enable continuous monitoring of moving objects within video frames. In the context of security camera systems, object tracking enhances situational awareness by following the trajectory of individuals or vehicles, aiding in the investigation of incidents.

_Intrusion Detection:_

Computer vision techniques can create virtual boundaries or zones within the camera's field of view. Intrusion detection algorithms trigger alerts when an object or person crosses predefined boundaries, providing immediate notifications for potential security breaches.

_Night Vision and Low-Light Enhancements:_

Advanced security camera systems integrate infrared sensors and image processing techniques to enhance night vision and low-light capabilities. This ensures effective surveillance even in challenging lighting conditions.

_Deep Learning for Anomaly Detection:_

Deep learning models, such as autoencoders, contribute to anomaly detection in security camera footage. These models learn normal patterns and behaviours, flagging deviations from the norm as potential anomalies. This approach enhances the system's ability to identify unusual incidents.
**III. Design Specifications**
_A.	User Interface and Functional Description_

The GUI will be simple, with a window of two buttons allowing you to toggle in between the live camera and the speed detection parts of the program.

- Wireframe Design for User Interface
 
Figure 3 - Base GUI (Top), Video Window (Middle), Live Camera Feed(Bottom)

- Functional Architecture Overview (Flowchart, System Components)

 

_B.	Technical Specifications_
- Python-based Implementation Details

1. Speed Detection Function (detect_speed)
Parameters:
vidPath: Path to the video file or camera index.
speed_threshold: Threshold speed for detecting vehicles.
Description:
Initializes a tkinter window for video display (root_video).
Defines the detect_objects function for real-time object detection and speed estimation.
Utilizes the cvlib library for common object detection.
Implements optical flow-based speed calculation between consecutive video frames.
Draws bounding boxes on detected objects and displays the video feed in the tkinter window.
Captures and saves images of detected objects when their speed exceeds the specified threshold.
Handles video stream release and window destruction upon video completion.
Additional Notes:
The calculate_displacement function computes optical flow displacement between frames.
The capture_and_save_image function saves images of detected objects with timestamps.
The tkinter window includes a label (label) to display the video feed.

2. Optical Flow Calculation (calculate_displacement)
Parameters:
prev: Previous frame.
curr: Current frame.
Description:
Converts frames to grayscale.
Uses Farneback's optical flow method to calculate flow vectors.
Converts Cartesian coordinates to polar coordinates and computes the average magnitude.

3. Image Capture and Save (capture_and_save_image)
Parameters:
frame: Frame containing the detected object.
Description:
Creates an output folder if it doesn't exist.
Generates a timestamp for the image filename.
Saves the captured image in the output folder.

4. Tkinter Window Initialization (root_video)
Description:
Initializes a tkinter window (root_video) for video display.
Creates a label (label) to show the video feed.

5. Camera Toggle (toggle_camera)
Description:
Toggles between using the camera and uploading a video file.
If using the camera, disables the upload button and starts speed detection with a default camera index.
If using a video file, enables the upload button to select a video file.

6. Main tkinter Window (root)
Buttons:
upload_button: Opens a file dialog to upload a video file for speed detection.
camera_button: Toggles between using the camera and uploading a video file.
Execution:
Initializes the main tkinter window (root) and runs the tkinter main loop.

7. File Dialog for Video Upload (open_and_detect_speed)
Description:
Opens a file dialog to select a video file for speed detection.
Calls the detect_speed function with the selected video file and a specified speed threshold.

8. Window Closure Handling (close_window)
Description:
Releases camera resources when the tkinter window is closed.

- System Requirements and Dependencies
1. Python Version:
The code is implemented in Python. Ensure that a compatible version of Python is installed (e.g., Python 3.x).
2. Libraries and Dependencies:
The following Python libraries are required and can be installed using the appropriate package manager (e.g., pip):
cv2 (OpenCV): For computer vision and image processing.
tkinter: For the GUI
PIL (Pillow): For image-related operations.
cvlib: A library for common computer vision tasks, including object detection.
Install dependencies using:
pip install opencv-python tkinter Pillow cvlib
3. Additional Notes:
Ensure that the computer vision library (cv2) is properly configured with the required dependencies, such as NumPy and others.
Verify that the system has access to a webcam or camera if using the camera for real-time speed detection, as well as other requirements such as a strong gpu.
**IV. Base Specification**

_Importing Video Content_
1. Video Stream Initialization:
The code leverages the OpenCV library to initialize the video stream. Whether accessing a pre-recorded video file or capturing real-time footage from a camera, the system adapts dynamically based on the user's choice. OpenCV ensures compatibility with a wide range of video formats, making the system versatile and easily deployable.
 
2. Real-time Camera Feed:
To accommodate scenarios where the system needs to operate in real-time, the code facilitates the utilization of the system's built-in camera. The toggle functionality between using a camera and uploading a video file enhances user flexibility and caters to varied operational requirements.
 
3. Video File Selection:
To upload video content needs to be analysed, the code includes a file dialog that allows users to select a video file. This enhances the system's applicability in diverse environments, such as analysing footage from security cameras or other surveillance sources.
 
4. GUI:
The implementation considers user interaction through the graphical user interface. The buttons for uploading a video file and toggling between camera and video modes provide a user-friendly experience. The GUI serves as a menu control centre, enhancing the accessibility and usability of the system.
 

_Object Detection for Speed Exceedance_
1. Object Detection Algorithm:
The code employs the cvlib library, specifically the detect_common_objects function, to perform object detection on each frame of the video stream. This function utilizes a pre-trained neural network to identify common objects present in the frame. The returned bounding boxes, labels, and confidence scores provide crucial information about the detected entities.
 
2. Speed Estimation:
Object speed is estimated by calculating the displacement of objects between consecutive frames. The displacement is determined through an optical flow calculation, utilizing the Farneback method provided by OpenCV (Farneback, 2003). The average magnitude of optical flow vectors is then used to quantify the movement and calculate the speed in pixels per second.
 
3. Visualization and User Feedback:
The code ensures a visually informative experience by drawing bounding boxes(bbox), around detected objects directly on the video frames. These bounding boxes, along with associated labels and confidence scores, are displayed in real-time on the graphical user interface (GUI). This not only aids in system verification but also provides immediate feedback to users about the identified objects and their spatial distribution.
 
4. Dynamic Speed Threshold:
The speed threshold parameter allows for dynamic configuration, enabling users to set a criterion for what is considered a speed exceedance. This adaptability enhances the system's versatility, making it applicable in diverse scenarios where different speed thresholds may be relevant. (Note, the speed can be relative to any video uploaded, so it is measure in pixels per second, which you can adjust in the code).
 

_Saving Video Segments_
1. Image Capture and Timestamping:
Upon the detection of an object with a speed exceeding the specified threshold, the system captures a snapshot of the frame containing the detected object. This image is saved with a timestamp, enhancing the accountability and chronological organization of captured segments. The timestamp, derived from the system's local date and time, is incorporated into the filename for clear identification.
 
2. Output Folder Creation:
Before saving any images, the system checks for the existence of an output folder. If the folder is not present, it is created to store the captured images. This ensures an organized structure for the saved segments and simplifies subsequent retrieval and analysis.
 
3. User Notification:
The system provides real-time feedback to users by printing a message in the console each time an image is saved. This notification not only confirms the successful capture of a segment but also aids in monitoring and assessing the system's performance during runtime.
 
4. Integration with Object Detection:
The image capture and saving mechanism is seamlessly integrated into the object detection pipeline. Whenever an object with a speed exceeding the threshold is identified, the system triggers the capture and storage process. This integration ensures that relevant segments are captured in response to specific events, aligning with the system's purpose of monitoring speeding vehicles.
 
5. Timestamped File Naming Convention:
Adopting a systematic file naming convention enhances the traceability and interpretability of the saved images. The filename incorporates the term "detected_object" along with the timestamp, creating a clear association between the saved segment and the specific instance of speeding detection.
 
**V. Additional Feature Development**
_A. Live Video Feed Integration_
The integration of live video feeds represents a pivotal enhancement to the system's capabilities. By enabling real-time video streaming from cameras, the system extends its reach beyond pre-recorded video files. The live feed integration allows for continuous monitoring and immediate responsiveness to dynamic scenarios. This feature is particularly valuable in scenarios where real-time surveillance and instant speed detection are essential, providing a holistic approach to pedestrian safety.
_B. Categorization of Movements (e.g., Human, Bike, Vehicle)_
The categorization of detected movements introduces a layer of intelligence to the system's object detection capabilities. By extending beyond the identification of common objects, the system classifies detected entities into specific categories such as humans, bikes, or vehicles. This categorization enhances the system's contextual awareness, allowing for more nuanced analysis and decision-making. It lays the foundation for more sophisticated applications, including targeted monitoring based on the type of detected movement.
 
Figure 4 - Here I have tested the live camera, and it categorises pretty accurately the different objects in my room.
_C. Object Detection and Tracking_
The integration of object detection and tracking elevates the system's capacity to monitor and follow moving entities persistently. Unlike traditional object detection, which operates on individual frames, object tracking maintains continuity across frames. This ensures that once an object is detected, the system can track its trajectory over time. Object tracking is especially beneficial in scenarios where continuous monitoring of a specific object, such as a speeding vehicle, is essential for comprehensive security and safety measures.
_D. Development of an Interactive User Interface_
The introduction of an interactive user interface (UI) marks a significant stride towards user accessibility and system manageability.

**VI. Key Feature Implementation and Discussion**
_Selection of Key Features_
The selection of these key features is driven by a strategic approach to enhancing the system's versatility, adaptability, and user-friendliness. Live video feed integration ensures that the system remains relevant in scenarios demanding real-time responsiveness. Categorization of movements adds a layer of intelligence, allowing the system to differentiate between various entities, contributing to more nuanced decision-making. Object detection and tracking extend the system's capabilities beyond mere identification, enabling continuous monitoring and analysis of object trajectories. The development of an interactive user interface prioritizes accessibility, making the system inclusive and user-friendly.

The synergistic integration of these key features transforms the vehicle speed detection system into a comprehensive solution. It aligns with the overarching objective of enhancing pedestrian safety on campus by providing a holistic approach to monitoring and responding to speeding events. As the system evolves, these key features lay the foundation for further customization, adaptation, and the incorporation of additional functionalities to address diverse use cases and scenarios.

**VII. Testing and Evaluation**
_Black Box Testing for Vehicle Speed Detection System_
Test Scenario	Objective	Test Steps	Expected Outcome	Tested Outcome
File Upload Testing	Verify the system's ability to handle different video file formats and sizes.	1. Upload videos in various formats (e.g., .mp4, .avi, .mkv)
2. Test with videos of different resolutions and file sizes
3. Verify that the system accurately processes and analyses each uploaded video.	Successful upload and accurate processing for various formats and sizes.	Successful upload and accurate processing for various formats and sizes, however the larger and longer videos has dropped frame rate considerably, a strong GPU is recommended.
Camera Mode Testing	Ensure the system functions correctly when using a live camera feed.	1. Toggle between camera and video modes multiple times
2. Verify that the system initializes the camera feed without errors
3. Check if real-time object detection works as expected.	Seamless transition between camera and video modes with successful object detection in real-time.	Seamless transition between camera and video modes with successful object detection in real-time. It does have noticeable performance drops due to potential poor optimisation of code.
Speed Exceedance Detection Testing	Assess the system's ability to detect speeding objects.	1. Create scenarios with objects moving at different speeds
2. Validate that the system triggers speed exceedance alerts for fast-moving objects
3. Ensure accurate reporting of speed in the console.	Timely detection and reporting of objects exceeding the speed threshold.	Timely detection and reporting of objects exceeding the speed threshold.
User Interface Interaction Testing	Validate the responsiveness and usability of the user interface.	1. Test the "Upload Video" button to ensure it opens the file dialog
2. Toggle between "Use Camera" and "Use Video" modes
3. Interact with the user interface elements while object detection is in progress.	Responsive UI elements with smooth transitions between modes and intuitive user interactions.	Responsive UI elements with smooth transitions between modes and intuitive user interactions.
Error Handling Testing	Verify the system's response to unexpected scenarios.	1. Intentionally upload a file with an unsupported format
2. Disconnect the camera while in use
3. Simulate low-light conditions to test the system's robustness.	Graceful handling of errors with meaningful error messages and system stability.	Doesn’t even allow other files to be selected.
Disconnecting the webcam does cause the application to crash.
Accuracy is reduced in low light videos and camera, however it is still fairly accurate.
Performance Testing	Assess the system's performance under different loads.	1. Upload multiple videos simultaneously to evaluate concurrent processing
2. Test the system's real-time processing capability by introducing rapid changes in the camera feed
3. Measure and compare the frame rate and system responsiveness.	Consistent and efficient performance with acceptable frame rates under varying loads.	Framerate drops linear to the amount of GPU and CPU usage is required

**VIII. Conclusion**
_Summary of Achievements_
The system's proficiency in object detection and categorization is a notable accomplishment, providing a foundation for efficient speed detection. Real-time processing capabilities, while facing some performance drops, contribute to the timely identification of speeding instances. The user interface's responsiveness and error handling mechanisms further enhance the system's usability and stability. The system's adaptability to various video formats underscores its versatility in real-world scenarios.
_Future Recommendations and Enhancements_
To propel the system to its full potential, optimization for handling larger videos is imperative. Exploring advanced GPU capabilities and scrutinizing the codebase, particularly in camera mode, can mitigate performance drops and bolster real-time processing efficiency. Addressing potential application crashes during unexpected events, refining the user interface for improved interaction, and integrating advanced AI models for object detection are key steps towards system refinement. Investigating sophisticated speed detection algorithms and conducting thorough compatibility testing will fortify the system's accuracy and ensure its seamless operation across diverse hardware configurations. Establishing a continuous testing and monitoring framework will further enable the system to evolve and adapt to emerging challenges, ensuring sustained effectiveness in pedestrian safety enhancement. The vehicle speed detection system stands as a promising foundation, ready to evolve and meet the dynamic demands of computer vision and security systems.

**IX. References**
Farneback, G., 2003. OpenCV.org. [Online] 
Available at: https://docs.opencv.org/4.x/d4/dee/tutorial_optical_flow.html
Girshick, R., 2015. Fast R-CNN. Microsoft Research.
Girshick, R. e. a., 2014. Rich feature hierarchies for accurate object detection and semantic segmentation. IEEE Conference on Computer Vision and Pattern Recognition, Issue doi:10.1109/cvpr.2014.81..
Joseph Redmon, S. D. R. G. A. F., 2016. You Only Look Once: Unified, Real-Time Object Detection. IEEE Conference on Computer Vision and Pattern Recognition (CVPR), Issue doi:10.1109/cvpr.2016.91.
Ren, S. e. a., 2017. Faster R-CNN: Towards real-time object detection with region proposal networks. IEEE Transactions on Pattern Analysis and Machine Intelligence, Issue doi:10.1109/tpami.2016.2577031.
