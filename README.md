# -Multimodal-Fusion-based-System-for-Filtering-Hate-Speech-from-Memes


# Arabic Hateful Meme Detection (Multimodal: Vision + Text)

This repository contains experiments on detecting hateful Arabic memes by combining **visual** and **textual** features within a multimodal framework.

## Overview
- **Task:** Hateful vs. Non-hateful meme classification  
- **Dataset:** QCRI/Prop2Hate-Meme (Arabic text–image pairs)  
- **Text Models:** AraBERT, mBERT, BERT-base-uncased  
- **Image Models:** InceptionResNetV2, EfficientNetB3, EfficientNetB7  
- **Fusion:** Early fusion of text and image embeddings  
- **Primary Metric:** Macro F1-score  

## Results (Macro F1 on validation/test)
| Model                            | F1  |
|----------------------------------|-----|
| InceptionNet + AraBERT           | 0.59 |
| InceptionNet + BERT-base-uncased | 0.60 |
| EfficientNetB3 + mBERT           | 0.53 |
| EfficientNetB7 + mBERT           | 0.62 |
| **Proposed: InceptionNet + mBERT** | **0.63** |

