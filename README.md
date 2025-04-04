# Momenta - Audio Deepfake Detection Take-Home Assessment

## Submission Information
This is the submission for the Momenta assignment for **Momenta - Audio Deepfake Detection Take-Home Assessment**.

## About the Repository
[Audio Deepfake Detection Repository](https://github.com/media-sec-lab/Audio-Deepfake-Detection)

The repository is a curated collection dedicated to audio deepfake detection. It aggregates a wide range of research papers, datasets, and tools related to detecting synthetic and spoofed audio. The resource is designed to serve both researchers and practitioners by offering theoretical insights and practical resources in one place.

## Audio Large Models and Their Role
The repository provides an overview of various large-scale audio models along with their corresponding research papers. These models, such as **AudioLM, VALL-E, and SpeechGPT**, illustrate how synthetic audio is generated. By analyzing the patterns and differences between real and fake audio produced by these models, researchers can better understand the inherent characteristics of deepfakes and use that knowledge to design more effective detection systems.

## Datasets and Noise Resources
A comprehensive list of popular datasets for audio deepfake detection is included, detailing not only the type of data and the quantity available but also the specific work conducted on each dataset. In addition, the repository offers a collection of noise datasets, which are essential for augmenting training data. By introducing realistic noise conditions into the models, researchers can enhance the robustness and real-world applicability of deepfake detection systems.

## Detection Methodologies
The repository categorizes detection methodologies into several classes based on feature extraction and learning strategies:

- **Handcrafted Feature-based Detection:**
  Uses expert-designed features (e.g., MFCC, LFCC) with classical machine learning approaches.
- **Hybrid Feature-based Detection:**
  Combines handcrafted features with features learned directly from data, leveraging both interpretability and data-driven insights.
- **End-to-end Detection:**
  Bypasses manual feature extraction by processing raw audio directly through deep learning models that learn optimal representations autonomously.
- **Feature Fusion-based Detection:**
  Integrates multiple types of features (such as spectral, temporal, and prosodic) to capture complementary information that improves detection accuracy.

## Evaluation Metrics
The performance of deepfake detection models is primarily evaluated using two metrics:

1. **Equal Error Rate (EER):**
   - Expressed as a percentage, where lower values indicate better performance.
   - It is the point at which the false acceptance rate equals the false rejection rate.
   - Rankings (shown in parentheses, e.g., "(11)" or "(4)") indicate a model's relative performance within its category.

2. **Tandem Detection Cost Function (t-DCF):**
   - A specialized metric for spoofing countermeasures that assesses both detection performance and its impact on the overall verification system.
   - Lower t-DCF values represent superior performance.

## Testing Scenarios
The repository distinguishes between two key testing scenarios in audio deepfake detection:

- **Logical Access (LA):**
  This scenario focuses on synthetic speech attacks that are digitally generated and directly injected into the system. The attacks do not involve any physical transmission; they are purely digital manipulations created through voice synthesis or conversion technologies.

- **Physical Access (PA):**
  In this scenario, the focus is on replay attacks. These occur when an attacker records a genuine user's voice and replays it through a physical medium (such as a speaker) to deceive the system. This setup involves actual acoustic transmission, making the detection process more challenging.

## Identification of Promising Models/Forgery Detection Approaches
### Criteria for Selection:
- **Detecting AI-generated human speech**
- **Potential for real-time or near real-time detection**
- **Analysis of real conversations**

### 1. **AASIST (Audio Anti-Spoofing using Integrated Spectro-Temporal Graph Attention Networks)**

#### Key Innovation:
- AASIST enhances the RawNet2 architecture by integrating a **Multi-head Graph Operation (MGO)** and **Hierarchical Spectro-Temporal Graph Attention Layer (HS-GAL)**.
- The approach processes raw waveform data directly using a **Sinc Filter** front-end and employs **graph attention networks** to capture both spectral and temporal relationships in speech.

#### Performance Metrics (Logical Access - LA Scenario):
- **Equal Error Rate (EER):** 0.83% (Ranked 2nd)
- **Tandem Detection Cost Function (t-DCF):** 0.028 (Ranked 1st)

#### Key Advantages:
- The **end-to-end** architecture eliminates the need for handcrafted feature extraction, improving efficiency.
- The **graph attention mechanism** enhances the detection of subtle inconsistencies in speech patterns.
- Direct processing of raw waveforms helps **identify artifacts introduced by neural vocoders**.
- **High performance** in detecting synthetic speech suggests strong reliability.

#### Potential Limitations:
- The complex architecture may require **significant computational resources**.
- Adaptation may be necessary for **varying audio qualities** in real-world conversations.
- Being an **end-to-end approach**, it may be less interpretable compared to feature-based methods.

---

### 2. **X-Vector-Based Anti-Spoofing ("How to Boost Anti-Spoofing with X-Vectors")**

#### Key Innovation:
- This approach repurposes **x-vectors**, originally developed for speaker verification, to improve deepfake detection.
- It integrates multiple acoustic features, including **Logarithmic Filter Bank Coefficients (LFCC)** and **Mel-Frequency Cepstral Coefficients (MFCC)**, with deep learning models such as **Time Delay Neural Networks (TDNN)** and **SENet34**.
- Detection optimization is achieved through **Large-Margin Cosine Loss (LCML)** for improved feature discrimination.

#### Performance Metrics (Logical Access - LA Scenario):
- **Equal Error Rate (EER):** 0.83% (Ranked 1st)
- **Tandem Detection Cost Function (t-DCF):** 0.024 (Ranked 1st)

#### Key Advantages:
- **Best performance metrics** among hybrid feature-based approaches.
- The use of **multiple feature types** enhances the ability to capture diverse speech artifacts.
- **TDNN-based architecture** is optimized for sequential data processing, enabling near real-time detection.
- The approach leverages **established speaker verification techniques**, making it well-suited for real-world deployment.

#### Potential Limitations:
- The **feature extraction process** may introduce some latency in real-time applications.
- Requires **fine-tuning** to optimize performance for different AI-generated voices.
- **Background noise** in real conversations may affect detection accuracy.

---

### 3. **Self-Distillation for Fake Speech Detection ("Learning from Yourself")**

#### Key Innovation:
- Uses **self-distillation** with **ECANet (Efficient Channel Attention Network)** and **SENet (Squeeze-and-Excitation Network)**.
- Processes both the **Log Power Spectrum (LPS)** and **fundamental frequency (F0)** for improved speech analysis.
- **Angular Softmax (A-Softmax)** optimizes detection through refined feature learning.

#### Performance Metrics:
- **Logical Access (LA) Scenario:**
  - **Equal Error Rate (EER):** 1.00% (Ranked 2nd)
  - **Tandem Detection Cost Function (t-DCF):** 0.031 (Ranked 2nd)
- **Physical Access (PA) Scenario:**
  - **Equal Error Rate (EER):** 0.65% (Ranked 3rd)
  - **Tandem Detection Cost Function (t-DCF):** 0.017 (Ranked 3rd)

#### Potential Limitations:
- **Feature extraction overhead** may impact real-time performance.
- **Adaptation required** for spontaneous speech variations.
- Sensitivity to **emotional expressions** and **speaking conditions**.
