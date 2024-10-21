# WildFire Computer Vision Recognition Research

## Introduction
With increasing global temperatures and arid climates, many regions are becoming more vulnerable to uncontrolled fires. A single spark can ignite massive fires in forests, plains, and settlements. Timely detection is crucial, as the minutes it takes for human observers to notice a fire can significantly impact the ability of nearby communities to evacuate. This model aims to assist remote areas, national parks, and sparsely populated regions by utilizing image software to detect fires and alert authorities without requiring human intervention.

## Datasets and Experimental Settings
Initially, we utilized a dataset of 999 images, consisting of 755 fire images and 244 non-fire images. The fire images were primarily forestsfires, varying in size, smoke levels, and distance, while non-fire images included diverse nature scenes. Noting the limited data and the high bias torwards forest fires, we introduced a second dataset of 651 images, comprising 110 urban and non-forest natural fire images and 541 varied non-fire images. This combination aimed to minimize bias and improve model accuracy across diverse fire scenarios and allow for a larger data set.

## Preprocessing and Creation Of Self Made Multi Layer Model
Our initial model was a simple four-layer CNN. Due to varying image sizes, we rescaled all images to the same size and normalized the pixel values between 0 and 1.  The model included three ReLU layers with increasing sizes, followed by MaxPooling, and used a sigmoid function for binary classification (fire vs. non-fire). While the model achieved a validation accuracy of around 95%, it showed significant overfitting when tested on non-forest fire images.

## Testing Various Architectures (1st Experimental Setting)
To address overfitting and bias, we explored pre-trained architectures with transfer learning, adjusting hyperparameters such as epochs, frozen layers, activation functions, nodes, and batch size.

- **VGG-16:** The model performed poorly, showing a high bias towards the initial dataset and could not recognize massive fires not in dense forests.
- **ResNet50:** Although it offered some improvement over VGG-16, it still exhibited significant test loss and lower accuracy when not in natural settings.
- **Xception:** Best Performance out of transfer learning models, with relatively lower bias torwards training data, but still relativelly low test accuracy and okay recall .
- **Self-Made Model:** Slightly better than Xception with testing accuracy, but the training accuracy was some what lower

## Utilizing the Combined Dataset (2nd Experimental Setting)
With a larger and more varied data set with the two best

- **Xception Model:** Test accuracy increased from 20-30% to roughly 80% for most xception models regardless of hyper paramaters , with reduced overfitting. 
- **Self-Made Model:** Test accuracies for models with different hyper paramaters generally improved at levels similar to Xception, but our model with the best hyper paramaters greatly outpaced Xception

Both models demonstrated the importance of dataset quality, as the simpler self-made model provided slightly more stable performance. 
As for which model was better, we believe that with a dataset that is relatively small

## Key Achievements
- Developed multiple Computer Vision models tailored for wild fire detection.
- Fine-tuned foundational models to improve performance metrics.
- Conducted extensive experiments to optimize model parameters, resulting in significant recall improvements:
  - From **75%** to **95%** for the best-performing foundational model from paramater tuning alone.

## K-Fold Cross Validation
To confirm the accuracy improvements, we employed k-fold cross-validation (K=5), validating the effectiveness of our models.

## Tools and Libraries
- **Programming Language:** Python
- **Deep Learning Framework:** TensorFlow (including Keras)
- **Data Manipulation:** Pandas, NumPy
- **Data Visualization:** Matplotlib, Seaborn
- **Image Processing:** PIL (Python Imaging Library)
- **Machine Learning:** Scikit-learn

## Conclusion and Further Research Directions
This project highlighted that while pre-trained models can enhance accuracy, simpler architectures may perform equally well or better for specific tasks, such as binary classification of fire detection. Bias in datasets can severely impact model usability, underscoring the need for diverse training data. Future directions include developing object detection models to identify specific fire locations and integrating video analysis for real-time detection in urban settings.
