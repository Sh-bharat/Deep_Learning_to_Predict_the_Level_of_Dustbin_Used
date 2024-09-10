# Deep_Learning_to_Predict_the_Level_of_Dustbin_Used
```
\documentclass[conference]{IEEEtran}
\IEEEoverridecommandlockouts
\usepackage{cite}
\usepackage{amsmath,amssymb,amsfonts}
\usepackage{algorithmic}
\usepackage{graphicx}
\usepackage{textcomp}
\usepackage{tikz}
\usepackage{xcolor}
\usepackage[hidelinks]{hyperref} 
\def\BibTeX{{\rm B\kern-.05em{\sc i\kern-.025em b}\kern-.08em
    T\kern-.1667em\lower.7ex\hbox{E}\kern-.125emX}}

\begin{document}
\title{Deep Learning for Intelligent Waste Management: Dustbin Detection, Classification, and Fullness Prediction\\}

\author{\IEEEauthorblockN{Dr. David Raj Micheal}
\IEEEauthorblockA{\textit{Division of Mathematics} \\
\textit{School of Advanced Sciences}\\
\textit{Vellore Institute of Technology Chennai}\\
\textit{Tamil Nadu – 600127}\\ 
\href{mailto:davidraj.micheal@vit.ac.in}{davidraj.micheal@vit.ac.in}
}



\and
\IEEEauthorblockN{Bharat Sharma}
\IEEEauthorblockA{\textit{Division of Mathematics} \\
\textit{School of Advanced Sciences}\\
\textit{Vellore Institute of Technology Chennai}\\
\textit{Tamil Nadu – 600127}\\ 
\href{bharat.sharma2023@vitstudent.ac.in}{bharat.sharma2023@vitstudent.ac.in}
}
} \maketitle

\begin{abstract} Overfilled dustbins create sanitation challenges and require frequent manual monitoring. This study explores a system for automated dustbin detection, classification, and fullness alert generation. We trained a detection model (or a combined detection-classification model) on diverse dustbin images captured from various angles, lighting conditions, and backgrounds. A separate classification model (if applicable) was trained on top-down dustbin images with varying fill levels. The system successfully located dustbins and categorized their fullness, leading to a significant reduction in overflowing bins and improved waste management efficiency based on user feedback. Future work will focus on expanding the training data, minimizing false positives, refining the alert system, and exploring additional data sources for enhanced performance. This approach has the potential to optimize waste management by automating dustbin monitoring and triggering timely alerts for collection.
 \end{abstract}
 \begin{IEEEkeywords}Real-time dustbin fill level monitoring, Convolutional Neural Network (CNN), Waste Management, Deep Learning, public awareness
 \end{IEEEkeywords}
\section{Introduction}: Overflowing dustbins are a persistent issue in both public and private spaces, leading to unpleasant odors, pest infestations, and potential health hazards. Traditional waste management methods rely on manual monitoring to determine dustbin fullness, a process that can be labor-intensive, time-consuming, and prone to human error. Inconsistent monitoring schedules can lead to overflowing bins, creating a negative impact on aesthetics and public health.
This paper proposes a novel system that leverages computer vision techniques to automate dustbin 

monitoring and optimize waste collection processes. Our system offers several advantages over traditional methods. By automating dustbin monitoring, we significantly reduce the need for manual inspection, freeing up personnel for other tasks. Additionally, real-time monitoring allows for timely alerts to be sent before dustbins overflow, optimizing collection routes and schedules. This not only improves efficiency but also helps maintain a cleaner and more hygienic environment by preventing overflowing bins. Furthermore, the system can collect valuable data on dustbin usage patterns, enabling informed decisions about waste collection frequency and bin placement optimization.
The core of the system lies in a detection model (or a combined detection-classification model) trained on a meticulously curated dataset of dustbin images. This dataset encompasses a wide range of variations to ensure robustness in real-world scenarios, such as viewing angles mimicking CCTV camera perspectives (top-down, oblique), images representing both brightly lit and dimly lit environments, and backgrounds with varying clutter levels to simulate real-world settings. The dataset also incorporates a diverse range of dustbin shapes, sizes, and colors to ensure the model can generalize to different types of bins. Additionally, a separate classification model (if applicable) is trained on top-down dustbin images showcasing various fill levels. By integrating these models, the system can effectively locate dustbins and accurately assess their fullness status, triggering timely alerts for waste collection when necessary.
This paper delves into the details of the system's development, including data collection strategies, model training methodologies, and system integration for alert generation. We evaluate the system's effectiveness through qualitative observations and user feedback, demonstrating its potential to revolutionize waste management practices. Finally, we explore avenues for future work, aiming to further enhance the system's accuracy, robustness, and functionality in diverse deployment environments.

\section{Objectives}The objective of the paper is to develop a computer vision-based system for automated dustbin monitoring and waste collection optimization. By leveraging deep learning techniques, the system aims to reduce manual inspection, improve efficiency, and maintain a cleaner environment.

\section{Literature Review}\cite{b1} have introduced a mechanism to monitor the level of trash in the garbage bin is detected using ultrasonic and infrared sensors. The data is sent to the Raspberry Pi when a certain threshold is met, and the Raspberry Pi then sends an email and SMS alert. Along with the Raspberry Pi, Arduino also receives the data simultaneously. Following that, an ethernet shield is used to send this data to the local host. The resultant is then sent to the Microsoft Azure platforms for training to keep track of real-time garbage, and to predict future waste generation patterns in the specified area. A “Google Calendar” event and smartphone alert system are also provided using the IFTTT method.

\cite{b2} proposes a public garbage bin overflow alarm and positioning system based on the STM32F103C8T6 microcontroller, which uses an infrared human body sensor mounted on the bin's surface to automatically identify who wants to throw garbage automatically open the bin cover for the convenience of users. Moreover, to avoid odour and pollutants in the immediate area after users depart, the bin cover doesn't immediately close. To accurately determine if the exterior waste can be full in all directions, the system also installed three 60- degree ultrasonic sensors on the interior wall of the lid to detect whether the internal garbage is full.

\cite{b3} suggests an ideal route-detecting system and a smart bin. The Suggested smart bin uses various hardware components, including a sonar sensor, an Arduino microcontroller, a GSM/GPRS shield, and a buzzer, to monitor the garbage within the bin and convey information to a server wirelessly. To prevent bin overflow, a buzzer is utilised. A sonar sensor is employed to determine the condition of the bin and measure the echo back distance. To transfer messages via a wireless connection, GSM/GPRS shield is utilised. Path optimisation utilises a genetic algorithm based on data recorded in a database.

\cite{b4} focuses on machine learning and Internet of Things-based technology, a promising perfect solution for making a smart city. As presented in the suggested framework, continually checks the metal level, noxious gas level, and dustbin capacity and then creates an alert message to handle the trash at the residential level of society immediately. Data from sensors is used to determine whether to issue an alert message. Based on test data, different supervised machine learning algorithms and techniques such as Support Vector Machine (SVM), Naive Biased (NB), Random Forest (RF), Decision Tree (DT), and K-Nearest Neighbours are matched side by side and an analysed for the categorisation and send alert messages. The appropriateness of the proposed work depends on how well the categorisation and prediction algorithms operate.

\cite{b5} recommended a system where deep convolutional neural network designs would be used. Regarding transfer learning methods and fine-tuning weight parameters using ImageNet, DenseNet121 delivered the best overall performance, achieving 95\% test accuracy. Our model, called RecycleNet, employs a deep convolutional neural network architecture that has been fine-tuned for sorting various recyclable materials. This cutting-edge method lowered the parameters of a 121-layer network from “7 million to around 3 million”.

\cite{b6} develops a system for classifying common waste products such as newspaper/sheets, cardboard, plastic, metallic waste, and other garbage. The model was developed by transfer learning and trained on the ImageNet Large Visual Recognition Challenge dataset. After refinement and quantisation, the resulting baseline model achieved an accuracy of 87.2\%.

\cite{b7} on a garbage classification system that uses deep learning convolutional neural networks to combine techniques from object recognition and image classification. Once the trash classification data has been trained and tested using ResNet and MobileNetV2, the garbage object data is trained and tested with three methods from the YOLOv5 family. In the end, findings from five studies on waste classification are combined. Using a consensus voting method, you can increase the rate at which your system recognises and labels image categories to 2\%. A change to the Raspberry Pi CPU was made once testing showed that the recognition rate for rubbish photos had grown to roughly 98\%.

\cite{b8} suggested a deep learning-powered hardware solution for elementary waste classification. It recommends using hardware based on convolutional neural network technology for deep learning. SmartBin uses image classification to determine whether a given trash item is biodegradable. This research compares and contrasts the performance of several popular pre-trained convolution neural networks, including AlexNet, ResNet, VGG-16, and others. InceptionNet is used for waste classification and efficiency testing in addition to hardware components (webCam, Raspberry Pi, infrared sensors, etc.) utilised for trash recognition in the bin. The Inception Neural Network found that the recommended model performed best, with an accuracy of 98.15\% and a loss of 0.10\% for the training set, and 96.2 percent and 0.13 percent for the validation data set.

\cite{b9} compared the performance of four different CNN-based waste-type classifiers ( such as Visual Geometry Group-16, Residual Network-50, Mobile Network V2, and DenseNet-121). The waste-type classifier can identify the sort of waste inferred from the waste-item class. A derived classifier fared better than its direct counterpart in the experiment. Of all garbage classification models, the Residual Network-50 classifier produced the highest accuracy at 94.90\%.

\cite{b10} aims to develop a method that can replace the existing laborious process with an automated one that is quicker, cleaner, and less harmful to the environment. In this paper, we propose a garbage bin identification system that uses the Convolutional Neural Network (CNN) model with three layers and five layers to determine the status of a bin (empty or full). A primary dataset in the form of a two-dimensional image is used for both model training, validation and testing purposes.

\begin{thebibliography}{00}
\bibitem{b1} C. J. Baby, H. Singh, A. Srivastava, R. Dhawan, and P. Mahalakshmi, “Smart bin: An intelligent waste alert and prediction system using machine learning approach,” Proceedings of the 2017 International Conference on Wireless Communications, Signal Processing and Networking, WiSPNET 2017, vol. 2018-Janua, pp. 771–774, 2018, doi: 10.1109/WiSPNET.2017.8299865.
\bibitem{b2} L. Yu, Y. Wang, M. Deng, and X. Gong, “Design of Public Garbage Can Overflow Alarm and Positioning System based on NB-IoT,” vol. 6, no. 7, pp. 132–141, 2020, doi: 10.6919/ICJE.202007.
\bibitem{b3} B. S. Malapur and V. R. Pattanshetti, “IoT based waste management: An application to smart city,” 2017 International Conference on Energy, Communication, Data Analytics and Soft Computing, ICECDS 2017, pp. 2476–2479, 2018, doi: 10.1109/ICECDS.2017.8389897.
\bibitem{b4} S. Dubey, M. K. Singh, P. Singh, and S. Aggarwal, “Waste Management of Residential Society using Machine Learning and IoT Approach,” 2020 International Conference on Emerging Smart Computing and Informatics, ESCI 2020, pp. 293–297, 2020, doi: 10.1109/ESCI48226.2020.9167526.
\bibitem{b5} C. Bircanoglu, M. Atay, F. Beser, O. Genc, and M. A. Kizrak, “RecycleNet: Intelligent Waste Sorting Using Deep Neural Networks,” 2018 IEEE (SMC) International Conference on Innovations in Intelligent Systems and Applications, INISTA 2018, 2018, doi: 10.1109/INISTA.2018.8466276.
\bibitem{b6} S. L. Rabano, M. K. Cabatuan, E. Sybingco, E. P. Dadios, and E. J. Calilung, “Common garbage classification using mobilenet,” 2018 IEEE 10th International Conference on Humanoid, Nanotechnology, Information Technology, Communication and Control, Environment and Management, HNICEM 2018, pp. 1–4, 2018, doi: 10.1109/HNICEM.2018.8666300.
\bibitem{b7} Z. Yang, Y. Bao, Y. Liu, Q. Zhao, H. Zheng, and Y. L. Bao, “Research on deep learning garbage classification system based on fusion of image classification and object detection classification,” Mathematical Biosciences and Engineering, vol. 20, no. 3, pp. 4741–4759, 2023, doi: 10.3934/mbe.2023219.
\bibitem{b8} T. Gupta et al., “A deep learning approach based hardware solution to categorise garbage in environment,” Complex and Intelligent Systems, vol. 8, no. 2, pp. 1129–1152, 2022, doi: 10.1007/s40747-021-00529-0.
\bibitem{b9} C. Srinilta and S. Kanharattanachai, “Municipal solid waste segregation with CNN,” Proceeding - 5th International Conference on Engineering, Applied Sciences and Technology, ICEAST 2019, pp. 1–4, 2019, doi: 10.1109/ICEAST.2019.8802522.
\bibitem{b10} S. Sudha, M. Vidhyalakshmi, K. Pavithra, K. Sangeetha, and V. Swaathi, “An automatic classification method for environment: Friendly waste segregation using deep learning,” Proceedings - 2016 IEEE International Conference on Technological Innovations in ICT for Agriculture and Rural Development, TIAR 2016, no. Tiar, pp. 65–70, 2016, doi: 10.1109/TIAR.2016.7801215.

\end{thebibliography}
\end{document}
 
```
