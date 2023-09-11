
<h1 align="center" id="title">Voice Assistant Speaker Verification</h1>
<h3 align="center" id="title"> ECAPA-Based Speaker Verification of Virtual Assistants: A Transfer Learning Approach </h3>

## Abstract
![ss_v4](https://github.com/rishsans/Voice-Assistant-Speaker-Verification/assets/98217912/56d9c202-d9b1-4d65-8521-79187cc5253c)

- Utilizing transfer learning with the ECAPA-TDNN model trained on the VoxCeleb2 dataset.
- Intra-voice assistant comparisons: Achieved accuracies of 83.33% (iOS) and 66.67% (Alexa) for text-independent samples and 50% for text-dependent samples.
- Inter-voice assistant comparisons (Alexa, Siri, Google Assistant, Cortana): 100% accuracy for text-independent, 80% for text-dependent.
- Demonstrates the effectiveness of transfer learning and ECAPA-TDNN model for secure speaker verification across speech assistant versions.
- Valuable insights for enhancing speaker verification in the context of speech assistants.

## Introduction
- Speaker verification utilizes speech characteristics differentiated based on pitch, formants, spectral envelope, MFCCs, and prosody characteristics.
- "Voice prints" represent a speaker's unique vocal qualities.
- Two types of speaker verification methods: text-dependent and text-independent.
- Transfer learning employs pre-trained models to improve performance when labeled data is scarce.
- The ECAPA-TDNN model from the SpeechBrain toolkit is used in this study for transfer learning on virtual assistants.

## Methodology
### Dataset
- A custom audio dataset was created with a subset selected for analysis.
- Organized into:
  - **Intra-pair Comparisons:** 
    - Siri Versions (iOS 9 vs iOS 10 vs iOS 11)
    - Alexa Versions (3rd gen vs 4th gen vs 5th gen)
  - **Inter-pair Comparisons:** 
    - Alexa 
    - Siri
    - Google
    - Cortana

### SpeechBrain
- Features the ECAPA-TDNN model, a state-of-the-art model for speaker recognition that uses TDNN design with MFA mechanism, Squeeze-Excitation (SE), and residual blocks.
- Hyperparameters are detailed in a YAML format.
- Data Loading makes use of a PyTorch dataset interface.
- Batching includes extracting speech features like spectrograms and MFCCs.
- `Brain_class()` simplifies the neural model training process.

### Pre-trained Model: ECAPA-TDNN
- SpeechBrain provides outputs using pre-trained models such as ECAPA-TDNN.
1. Data preprocessing: Extract 80-dimensional filterbank features.
2. Model initialization: 5 TDNN layers, an attention mechanism, and an MLP classifier.
3. Hyperparameter setting: epochs, batch size, learning rate, etc.
4. Training: Trained on the VoxCeleb2 dataset.
5. Validation and Testing: Evaluate on a validation set.

## Implementation
<table>
<tr>
<td>
- Normalize, denoise, and extract features from audio samples.
                   
- Adjust the ECAPA-TDNN model's initial layer for TDSV and TISV.
  
- Use the model to verify speaker identities and obtain similarity scores.
  
- Store scores and predictions in arrays.
- Calculate accuracy, precision, F1 score, and recall for evaluation.
</td>
<td>
<img src="https://github.com/rishsans/Voice-Assistant-Speaker-Verification/assets/98217912/1df88772-1502-40f7-9501-5a3b40faaaf9" alt="ss_v5" width="200"/>
</td>
</tr>
</table>

## Result
<p align="center">
  <img src="https://github.com/rishsans/Voice-Assistant-Speaker-Verification/assets/98217912/8e13cd7d-8e96-4cc4-ad4e-d204e746aea9" alt="ss_v3" width="700"/>
</p>

## Output Snippets

<img src="https://github.com/rishsans/Voice-Assistant-Speaker-Verification/assets/98217912/2874e542-f198-48ec-8da6-4189317d386e" alt="ss_v2" width="900"/>

<img src="https://github.com/rishsans/Voice-Assistant-Speaker-Verification/assets/98217912/e82071d5-91e8-47d2-9d5f-2bd3e8a399f9" alt="s3" width="900"/>

<img src="https://github.com/rishsans/Voice-Assistant-Speaker-Verification/assets/98217912/0e38457a-ebde-4509-b35e-3d76725ad930" alt="ss_v1" width="900"/>

<img src="https://github.com/rishsans/Voice-Assistant-Speaker-Verification/assets/98217912/77f4871e-7b3a-4928-a9a3-f96f25655c5e" alt="s5" width="900"/>

<img src="https://github.com/rishsans/Voice-Assistant-Speaker-Verification/assets/98217912/07a3fbee-59b1-44a4-8c56-6fd27fa6cc49" alt="s6" width="900"/>

<img src="https://github.com/rishsans/Voice-Assistant-Speaker-Verification/assets/98217912/8ddcd976-c3eb-40af-a390-6e80e28fa8db" alt="s7" width="900"/>


## Conclusion
- Intra-pair TDSV analysis shows similarities among all versions, leading to potential security concerns.
- Inter-pair TDSV analysis found matches between Cortana & Google Assistant and Alexa.
- TISV has higher accuracy than TDSV due to the model's capability to differentiate different texts.
- For better performance, additional training on a broader dataset of synthetic voices is recommended.
- The study emphasizes the potential of transfer learning and SpeechBrain for speaker verification, also acknowledging challenges with synthetic voices.















