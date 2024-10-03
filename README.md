# Explainable-Cat-AI 🐱🔍

### Unraveling the Mysteries of AI's Decision-Making for a Confused Cat

This repository explores how to explain the decision-making process of a pre-trained black-box model (**ResNet34**) using **LIME (Local Interpretable Model-agnostic Explanations)**. Specifically, we dive into the case of a **confused cat** image, analyzing why the model predicts that the image contains a cat, and which parts of the image were most critical to that decision.

![Confused Cat Image](path-to-image.png)

---

## Project Overview

### The Story:
In this project, we take an AI model trained on ImageNet, **ResNet34**, and feed it an image of a confused cat. The model predicts that the image contains a "cat" (phew!). However, as curious data scientists, we wanted to know **why** the model made that decision. Enter **LIME**, our trusty sidekick, which helps us break down the prediction and reveal which parts of the cat’s image influenced the model’s decision.

### Key Features:
- **Explaining Black-Box Models**: We use **LIME** to generate local explanations for the model's decision, showing which parts of the image were most influential.
- **Side-by-Side Visualization**: The repository provides a comparison of the **original image** and the **LIME-explained image** where relevant parts are highlighted.
- **Comparison of Techniques**: Discussion on why **LIME** was chosen over other explainability techniques like **SHAP** and **Anchors**.

---

## Why LIME?

### Strengths:
- **Model Agnostic**: LIME works with **any model**, be it a decision tree, deep neural network, or random forest. This flexibility was essential since we were dealing with a **black-box model** like ResNet34.
- **Visual Explanations for Images**: LIME's ability to highlight **specific parts of the image** made it ideal for image data. It broke down the cat's face into **superpixels** and helped us see exactly which regions mattered most to the model.
- **Localized Explanations**: We didn’t need to explain the entire model’s behavior. Instead, we wanted to know **why the model made this specific prediction** for our confused cat. LIME focuses on such **local explanations**, making it a great choice for this task.
- **Faster Computation**: LIME's approximation using **perturbations** is relatively quick compared to other techniques like SHAP, especially when working with image data. It allowed us to get the explanations efficiently.

### Limitations:
- **Instability in Perturbations**: LIME perturbs the image by altering superpixels, and sometimes, this can lead to noise. Slight perturbations can confuse the model, leading to unstable explanations.
- **Local, Not Global**: While LIME explains individual predictions, it doesn't offer **global insights** into how the model works across all data. It's perfect for explaining the cat's prediction but won't tell us about the model's overall behavior.
- **Computationally Expensive for Larger Models**: LIME requires generating many perturbations (we used **5000 samples**), which can be computationally expensive, especially for larger models and datasets.

### Potential Improvements:
- **More Stable Perturbations**: One improvement would be to use more sophisticated perturbation techniques to ensure the highlighted areas remain stable and meaningful.
- **Combining LIME with SHAP**: While LIME is excellent for local explanations, combining it with **SHAP** could provide **global insights** and make the explanation more comprehensive.

---

## LIME vs. SHAP and Anchors

We also considered **SHAP** and **Anchors**, two other powerful explanation techniques, but **LIME** emerged as the best choice for our task. Here's how it stacks up against the competition:

### Comparison Table: LIME vs. SHAP vs. Anchors

| **Technique** | **Strengths** | **Limitations** | **Why We Didn’t Choose It** |
| --- | --- | --- | --- |
| **LIME** | - Model agnostic <br> - Visual explanations for images <br> - Localized explanations | - Perturbations can be noisy <br> - Focused only on local behavior | Chosen for its ability to explain **specific image predictions** with visual clarity. Perfect for understanding the **cat’s image**. |
| **SHAP** | - Based on **Shapley values** (theoretically sound) <br> - Provides both **local** and **global** explanations | - Computationally expensive <br> - Complex to interpret for images | SHAP is **more suited for structured data** like tabular datasets. It provides global insights, but LIME's **visual explanation** is more intuitive for **image data**. |
| **Anchors** | - High-confidence, **rule-based** explanations <br> - Easy to interpret for **text** and **tabular data** | - Doesn’t offer visual explanations for images <br> - Works best with structured data | Anchors generates **rule-based** explanations that are more suited to structured data, not images. It lacks the **visual component** needed for interpreting **image data** like our cat. |

### Why LIME was the Best Choice:
- **Images Need Visual Explanations**: Our task was to explain the prediction of an image model, and **LIME** excels at offering **visual insights**. It shows us which parts of the image (superpixels) mattered most to the model.
- **Localized Focus**: We were interested in why **this specific cat image** was classified as a "cat," and LIME’s ability to zoom in on individual predictions made it perfect for this scenario.
- **Faster Results**: Compared to SHAP, which would have taken longer to compute for an image model like ResNet34, LIME was more efficient while still delivering **interpretable results**.

---

## Why LIME Was Chosen

We selected **LIME** over **SHAP** and **Anchors** due to its unique strengths in handling image data and providing **visual explanations**. Here's a quick comparison:

| **Technique** | **Why LIME is Better** |
| ------------- | ---------------------- |
| **LIME**      | Offers visual explanations for images, making it ideal for tasks like explaining image classification predictions. |
| **SHAP**      | Great for structured/tabular data, but slower and more complex for images. |
| **Anchors**   | Rule-based, useful for text/tabular data but lacks visual explanations for image data. |

**LIME** was the perfect sidekick to help us understand why **ResNet34** predicted that the image showed a cat, particularly for its ability to highlight specific regions like the cat's eyes, whiskers, and face.

---

## Limitations and Improvements

While **LIME** provided the explanation we needed, it has some limitations, including:

- **Instability in Perturbations**: Sometimes, LIME's superpixel perturbations can cause noisy or less meaningful explanations.
- **Local, Not Global**: LIME focuses on local explanations but doesn't offer a global understanding of the model.

### Potential Improvements:
- Combining **LIME** with **SHAP** to gain more **global insights** into model behavior while keeping the **localized visual explanations** that worked so well for image classification.

## Run the Project

To run the project, simply click the button below, and it will open the project in **Google Colab**:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https)

This will allow you to run the notebook directly in your browser with no local setup required!





