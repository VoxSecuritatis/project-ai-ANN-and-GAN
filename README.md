## Neural Networks and Generative Adversarial Networks Portfolio Project
### A porfolio project to demonstrate ability in development, execution, and analysis of deep learning model using a Neural Network and a Generative Adversarial Network (GAN)

### **Project File:** [https://voxsecuritatis.github.io/project-ai-ANN-and-GAN/](https://voxsecuritatis.github.io/project-ai-ANN-and-GAN/)

### Neural Network
This project is a portfolio-ready demonstration of an end-to-end deep learning workflow using the **Modified National Institute of Standards and Technology (MNIST)** handwritten digit dataset (28×28 grayscale images, digits 0–9). The notebook builds, trains, evaluates, and interprets two core image-classification approaches:

- A **Multilayer Perceptron (MLP)** (dense neural network on flattened pixels)
- A **Convolutional Neural Network (CNN)** (spatial feature learning via convolution + pooling)

The work emphasizes not just accuracy, but professional model validation: training/validation behavior, reproducibility cues, confusion-pattern inspection, and practical interpretation of errors.

### Key Quantitative Results (Test Set)
On the MNIST test set, the **Convolutional Neural Network (CNN)** achieved **0.9921 accuracy (99.21%)**, while the **Multilayer Perceptron (MLP)** achieved **0.9781 accuracy (97.81%)** in the side-by-side comparison table.  
That corresponds to error rates of **0.79% (CNN)** vs **2.19% (MLP)**.

In the CNN training interpretation section, the run also documents strong training dynamics with:
- Training accuracy: **99.37%**
- Validation accuracy: **99.15%**
- Generalization gap: **0.22%**

### What the HTML File Is and What It Does
The HTML file is a static, shareable export of the notebook. It is designed for reviewers to open in a web browser and read like a report. It preserves:

- Narrative markdown explanations (project story + reasoning)
- Code cells (how the work was done)
- Outputs (tables, training logs, evaluation summaries, and plots)

Because it is an export, it does not execute code when opened. Reviewers see the captured results and figures exactly as produced when the notebook was last run.

### What This Demonstrates (Portfolio Value)
- Data preparation and sanity checks for an image classification pipeline
- Clear architectural comparison between **Multilayer Perceptron (MLP)** and **Convolutional Neural Network (CNN)** models
- Training diagnostics (loss/accuracy behavior over epochs) to identify underfitting/overfitting
- Evaluation beyond accuracy, including macro and weighted precision, recall, and F1-score comparisons
- Actionable error-pattern inspection (top confusion pairs and misclassification analysis) demonstrating real model understanding

### Why It Matters (Applied Context)
MNIST digit recognition is a simplified proxy for real-world **Optical Character Recognition (OCR)** and image classification tasks (forms processing, handwritten fields, document digitization). This project demonstrates the workflow commonly used in production: preprocessing, selecting an architecture suited to the data, validating generalization, and identifying where errors concentrate—because those errors drive downstream cost (manual review, rework, customer friction) while strong performance creates leverage (speed, automation, scalability).

## MLP, CNN, and GAN Explained

### Multilayer Perceptron (MLP) analogy: "Judging a picture after it’s been shredded"

Imagine you have a 28×28 photo of a handwritten digit. An **Multilayer Perceptron (MLP)** works like this:

* It **shreds the photo into a long list of individual pixels** (784 numbers in a row).
* Then it tries to guess the digit by learning patterns from that list, like:

  * "When these pixel positions are bright at the same time, it’s often a 3.”
* It can still get really good—but it’s missing one big thing:

  * it **doesn’t naturally understand that pixels next to each other form shapes**.

So an MLP is like someone who can recognize a face **only by reading a spreadsheet of pixel brightness values**, not by seeing the image as a picture.

**What you’re looking at in results:**
MLP usually performs well on MNIST, but it tends to make more "shape-based mistakes" because it’s not designed to notice edges and curves as efficiently.

---

### Convolutional Neural Network (CNN) analogy: "A team of inspectors scanning a photo with magnifying glasses"

A **Convolutional Neural Network (CNN)** treats the image like an image.

Picture a team of tiny inspectors sliding magnifying glasses across the photo:

* One inspector specializes in spotting **edges**.
* Another spots **corners**.
* Another spots **curves**.
* Later "teams" combine those into bigger patterns like:

  * loops, hooks, intersections, stroke directions.

Then at the end, the CNN says: "Given all the features I detected, this is most likely a 9.”

This is why CNNs tend to outperform MLPs on image tasks: they’re built to recognize **spatial structure**—the way pixels form shapes.

**What you’re looking at in results:**
CNN typically learns faster, reaches higher accuracy, and makes fewer mistakes because it’s better at understanding the structure of handwritten digits.

---

### One-sentence takeaway (for an uninterested reader)

* **MLP:** "Reads the image like a flat list of numbers and learns associations.”
* **CNN:** "Looks at the image like a picture and learns shapes and patterns—so it’s usually better.”

### Generative Adversarial Network (GAN)
In this project, a **Generative Adversarial Network (GAN)** is like an **Art Forger vs. Art Detective** competition.

#### The two roles

**1) The Art Forger = the Generator**

* The Generator’s job is to **create fake "handwritten digits”** that look like they came from the **Modified National Institute of Standards and Technology (MNIST)** dataset.
* It starts out producing obvious garbage—random noise that doesn’t resemble digits.
* Over time, it learns patterns like **strokes, curves, thickness, spacing**, and digit structure.

**2) The Art Detective = the Discriminator**

* The Discriminator’s job is to **judge** whether an image is:

  * **Real** (from the MNIST training data), or
  * **Fake** (produced by the Generator)
* It gets better at spotting subtle flaws—like weird stroke shapes or unrealistic pixel patterns.

#### How training works (the "game”)

Training alternates between the two:

1. **Train the Detective (Discriminator)**

* Show it a mix of:

  * real MNIST digit images
  * fake digits generated by the Forger
* Teach it to correctly label them **real vs. fake**.

2. **Train the Forger (Generator)**

* Now the Forger tries to produce fakes that **trick the Detective** into saying "real.”
* The Forger is rewarded when the Detective is fooled.

This back-and-forth creates an "arms race”:

* As the Detective improves, the Forger must improve.
* As the Forger improves, the Detective must become sharper.

#### What "success" looks like in your notebook

For your MNIST GAN, success is when:

* The Generator outputs images that look like legitimate handwritten digits (not perfect, but recognizable),
* And the Discriminator can no longer easily tell real from fake.

You’ll typically see:

* Early training: blotchy noise
* Mid training: vague digit-like blobs
* Later training: digits with clearer shapes and strokes

#### How this relates to the rest of your project (MLP vs CNN)

* Your **Multilayer Perceptron (MLP)** and **Convolutional Neural Network (CNN)** sections are about **classification**: "What digit is this?”
* Your GAN section is about **generation**: "Can we create realistic digit images?”

So the GAN is the "creative" capstone:

* not just recognizing digits,
* but learning the digit distribution well enough to **produce new ones**.

