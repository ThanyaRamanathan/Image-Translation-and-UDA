# Image Translation and Unsupervised Domain Adaptation (UDA)

This project explores **Image Translation** and **Unsupervised Domain Adaptation (UDA)** to improve deep learning models' adaptability across datasets. It utilizes a **CycleGAN** for domain adaptation between the MNIST and USPS datasets, enabling effective classification without labeled target data.

---

## Key Features

1. **Dataset Preprocessing**:
   - Resize images to 28×28.
   - Convert to greyscale.
   - Normalize pixel values to mean=0.5, std=0.5.

2. **Convolutional Neural Network (CNN)**:
   - Baseline image classification on MNIST.
   - Achieved 68% accuracy on USPS dataset without UDA.

3. **CycleGAN**:
   - Translates images from MNIST (source) to USPS (target) domains.
   - Uses generators, residual blocks, and discriminators for image-to-image translation.
   - Enables training without paired datasets.

4. **UDA Integration**:
   - Applies CycleGAN-generated dataset for target domain training.
   - Improves USPS classification accuracy to 90% without labeled USPS data.

---

## Methodology

### Dataset Preprocessing
- Resize: 28×28 pixels.
- Convert: Greyscale to simplify inputs.
- Normalize: Mean and standard deviation to 0.5 for improved model performance.

### CNN Model
- Two convolutional layers (ReLU activation, max pooling).
- Fully connected layer with ten outputs.
- Trained for 10 epochs on MNIST; tested on USPS.

### CycleGAN
- **Generator**: Translates between domains using convolutions and residual blocks.
- **Discriminator**: Differentiates real vs. translated images using adversarial training.
- **Cycle Consistency**: Ensures original image reconstruction after domain translations.

### UDA Workflow
1. Train CycleGAN with MNIST as source and USPS as target.
2. Generate USPS-like dataset from MNIST.
3. Train CNN on the CycleGAN-translated dataset.
4. Evaluate CNN on USPS dataset.

---

## Implementation Details

### Residual Block
- Addresses vanishing gradient issues.
- Two convolutional layers with ReLU and batch normalization.
- Enables learning from input-output differences.

### Discriminator
- Four-layer CNN with leaky ReLU activation.
- Outputs likelihood of real vs. generated images.

### Generator
- Encodes, processes through residual blocks, and decodes input.
- Uses Tanh activation to normalize pixel values.

### CycleGAN Workflow
1. Forward pass: Translate source to target domain and back.
2. Cycle consistency loss ensures meaningful translations.
3. Adversarial training improves generator realism.

---

## Evaluation and Constraints

### Successes:
- Achieved 90% USPS classification accuracy using UDA.
- Demonstrated effective domain adaptation with CycleGAN.

### Constraints:
1. **Shape Consistency**: Source and target datasets must share similar shapes (e.g., digits in MNIST and USPS).
2. **Dataset Specificity**: Each new dataset requires CycleGAN retraining, limiting scalability.
3. **Potential Translation Errors**: Domain translations may introduce minor inaccuracies.

---

## Future Improvements

1. Automate domain alignment for datasets with greater variability (e.g., rotation, skew).
2. Enhance generalization across multiple datasets simultaneously.
3. Optimize computational efficiency of CycleGAN training.
