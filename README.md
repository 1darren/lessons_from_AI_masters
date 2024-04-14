# lessons_from_AI_masters
Lessons from my Master's in AI 

- Computer Vision: X-Ray Image Detection Project
- AI Systems Evaluation: TrojanNet *(coming soon)*
- Multi-Agent System: Drone Project *(coming soon)*



## 👁 **Torch X-Ray Vision Project**

[![readme Quotes](https://quotes-github-readme.vercel.app/api?quote=Theory%20can%20only%20take%20you%20so%20far.&author=Oppenheimer&type=horizontal)](https://github.com/piyushsuthar/github-readme-quotes)

Problem:
- Binary classification (healthy/unhealthy) on images of Chest X-ray.
- Training set: ([ChestXray8](https://arxiv.org/abs/1705.02315)).
- [Final assessment](https://www.kaggle.com/competitions/cs604xray/leaderboard? consisted of test images from Xray8 mixed with X-rays from COVID-19 patients.

My approach:
- [TorchXRayVision](https://github.com/mlmed/torchxrayvision) ("XRV") as a pre-trained feature extractor, extracting disease prediction logits.
- [LightGBM](https://lightgbm.readthedocs.io/en/stable/) as classifier, achieving up to 73% accuracy.

- Reasoning: 
  - Everybody would be training models; brute-force training is not the wisest course of action.
  - Making use of a pre-trained model for feature extraction is industry standard and moves faster
  - Instead of dealing with large datasets (60,000 images of 1024x1024), I could convert images into feature tensors (15 disease logits from XRV model) and make predictions from there.


Learnings from Others:
*After the class, I went around and asked people how they achieved better results. From best to worst:*
- [EfficientNet](https://arxiv.org/pdf/1905.11946.pdf) with [focal loss](https://arxiv.org/abs/1708.02002). Focal loss would have trained the model to focus on edge cases and 'difficult' examples, thereby improving prediction performance.
- Pre-trained [TorchXRayVision](https://github.com/mlmed/torchxrayvision) model with binary classifier (frozen weights). I should've experimented with the model directly instead of using LightGBM classifier.
- Ensemble of 5 models from [Stanford Chex](https://stanfordmlgroup.github.io/competitions/chexpert/) competition (weights unfrozen). Someone who did way more literature review than me and spent more time building models (and constructing an ensemble). According to him, breakthrough happened when weights were unfrozen.

My reflections:
- Even with LightGBM, my test accuracy plateaued around 70%. I should have changed track there.
- I could have branched further at the start, trying different models & architectures.
- I did some literature review, but I could've gone further -- learning from CheXpert and Focal Loss. 
