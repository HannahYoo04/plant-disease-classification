
# Plant Disease Image Classification
EfficientNet-B0 experiments from a six-person team project for UTS 31256 Image Processing and Pattern Recognition, Spring 2026. The project investigated how well image classifiers recognise healthy and diseased plant leaves under controlled and field imaging conditions.

I trained an EfficientNet-B0 classifier from scratch and evaluated it on a Kaggle test set and an external PlantWild subset. The wider team also explored ResNet, MobileNet, transfer learning, Vision Transformers and feature-based classifiers.
My contribution

- Implemented and trained EfficientNet-B0 for 38 healthy and diseased leaf classes.
- Evaluated predictions with accuracy, macro precision, recall, F1 scores and confusion matrices.
- Mapped PlantWild labels to the training classes and analysed external evaluation results.
- Developed the project's future work proposals, including experiments on background bias and training with more varied images.
Method
- Environment — Google Colab with Python, PyTorch and torchvision.
- Model — EfficientNet-B0 with randomly initialised weights and a 38-class output layer.
- Input — RGB images resized to 224 × 224 and normalised using ImageNet mean and standard deviation.
- Training — 10 epochs, batch size 32, AdamW optimiser, learning rate 0.001 and weight decay 0.0001.
- Checkpoint selection — Highest validation accuracy.
The Kaggle experiment used 70,295 training, 8,786 validation and 8,786 test images. The original training folder was retained, and the original validation folder was split equally into validation and test sets using stratified sampling with seed 42.

For external evaluation, the trained model was applied to PlantWild without further training. After label mapping and filtering, the evaluation contained 1,051 images across 24 classes. Predictions were restricted to these evaluated classes.
Results
All scores below are percentages.
Evaluation dataset	Images	Classes	Accuracy	Macro precision	Macro recall	Macro F1
Kaggle test set	8,786	38	98.83	98.83	98.81	98.81
Filtered PlantWild test subset	1,051	24	11.51	14.47	12.19	8.82


The evaluations use different image distributions and class sets. The Kaggle score measures performance within the training dataset's distribution. The PlantWild result shows limited generalisation to the evaluated field images.

Backgrounds, lighting, viewpoints and class alignment are possible contributors to this difference. Their individual effects remain to be tested. The Kaggle source dataset also includes offline-augmented images, so related images across splits are an additional consideration when interpreting the high test score.
Run in Google Colab
1. Open the EfficientNet notebook in Google Colab and select a GPU runtime.
2. Prepare the Kaggle Plant Diseases Detection dataset and PlantWild dataset.
3. Update the dataset locations and result paths for your environment, including MAIN_ROOT and RESULTS_DIR.
4. Run the data preparation, split generation, training and evaluation cells in order.
5. Review the learning curves, classification reports and confusion matrices.
The original experiment used Google Drive paths. Update those paths to match your own storage.
Future work
- Train on both controlled and field images while reserving the external test set for final evaluation.
- Compare original images, segmented leaves and lesion-focused crops to investigate background reliance.
- Explore combining plant images with disease descriptions.
Acknowledgements

The datasets used were Plant Diseases Detection from Kaggle and PlantWild from Hugging Face.
