# EBD-YOLO
A Real-time Lightweight Crop Pest Detection Algorithm using Edge Devices
# Usage
1. Download this repository
2. Create a virtual environment python >= 3.8
3. Install Pytorch
4. pip install -r requrements.txt
# Code Description
1. dataset configure file: "data/pest-08.yaml"
2. model configure files: "models/yolov5-pest/*.yaml"
3. attention module files: "models/CBAM.py, ECA.py, EMA.py". They are registered in "yolo.py"
4. DCNV3_Yolo, Bottleneck_DCNV3, and C3_DCNV3 are defined in "models/DCNv3.py" and registered in "yolo.py"
# Dataset
The dataset is available at: https://drive.google.com/file/d/1ZnZGZ3hXuHnOeEWCOoqJgnHSwYfOkgag/view?usp=sharing
# Results
1. Performance comparison of integrating different attention modules

Model    | Precision(%)    | Recall(%)  | mAP50(%)  | Parameters
-------- | -----           | -----      | -----     | -----
YOLOv5n  | 87.4    | 89.3	| 91.8        | 1,769,989        
+ECA     | 88.8    | 89.5 | 92.2 (+0.4) | 1,770,001(+12) 			
+CBAM    | 88.7    | 86.9 | 92.4 (+0.6) | 1,781,038(+11,049)
+EMA     | 88.9    | 89.1 | 92.5 (+0.7) | 1,783,653(+13,664)

2. Performance comparison of YOLOv5n+EMA and BiFPN models

Model    | Precision(%)    | Recall(%)  | mAP50(%)  | Parameters
-------- | -----           | -----      | -----     | -----
YOLOv5n+EMA  | 88.9    | 89.1	| 92.5        | 1,783,653        
+BiFPN       | 87.5    | 91.6 (+2.5%)       | 92.8 (+0.3) | 1,800,046(+16,393)

3. Performance comparison of YOLOv5n and EBD-YOLO models

Model    | Precision(%)    | Recall(%)  | mAP50(%)  | Parameters
-------- | -----           | -----      | -----     | -----
YOLOv5n                          | 87.4          | 89.3	      | 91.8        | 1,769,989        
+EMA+BiFPN+DCNv3 (EBD-YOLO)      | 90.1(+2.7)    | 92.1(+2.8) | 93.2(+1.4)  | 1,835,227(65,238)
