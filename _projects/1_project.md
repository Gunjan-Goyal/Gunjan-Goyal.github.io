---
layout: page
title: Smart Terrain Detection 
description: EfficientNet 
img: assets/img/main1.jpg
importance: 1
category: work
related_publications: false
---

Our project leverages EfficientNet for real-time surface terrain classification to enhance wheelchair navigation. Using a Raspberry Pi Camera, the system captures images of the ground and processes them through a deep learning model trained on the StreetSurfaceVis dataset. The model accurately classifies surfaces such as concrete, asphalt, unpaved paths, and paving stones, achieving 98.95% validation accuracy. This classification enables adaptive motorized assistance, ensuring smoother navigation over challenging terrains while preserving user control.

Model Architecture
The StreetSurfaceVis dataset, with 9,122 annotated street-level images from Germany,
was used to train and evaluate the terrain detection model. We fine-tuned pre-trained architecture- EfficientNet B0 to extract features. It is compiled using TensorFlow’s Keras API, optimizing the categorical cross-entropy loss and an adaptive learning strategy. There are different types of layers used in EfficientNet B0. <br>
{% include figure.liquid path="assets/img/main11.jpg" title="Layers of EfficientNet Model" class="img-fluid rounded z-depth-1" %}

The first 50 layers were frozen and the remaining layers were trainable. A Global Average Pooling (GAP) layer was added to reduce spatial dimensions, followed by a dense layer with 128 ReLU-activated neurons. A dropout layer (50%) was applied before the final softmax classification layer, which included neurons equal to the number of surface classes, that is, 17. The model was optimized using the Adam optimizer with a 0.0001 learning rate and trained using categorical cross-entropy loss over 20 epochs with a batch size of 32. <br>
Early stopping (patience = 3) and model checkpointing based on validation loss were used to prevent overfitting and retain the best model.

{% include figure.liquid path="assets/img/main12.jpg" title="Accuracy and Loss" class="img-fluid rounded z-depth-1" %}
Performance Evaluaiton of the EfficientNet Model. 

Will be presenting the article "Context-Aware Adaptive Wheelchair: AI-Driven Terrain Detection for Mobility Assistance" at ICETESS-2025. The extended version will be published in a Springer, 2025, highlighting our advancements in ML-driven surface classification for wheelchair navigation.
