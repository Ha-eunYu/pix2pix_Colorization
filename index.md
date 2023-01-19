---
layout: default
title: Home
nav_order: 1
description: " "
permalink: /
---


### MLP, CNN, RNN의 Inductive bias
네트워크가 어떤 것에 특화되어 있는가
- MLP
  - 이미지 전체의 커다란 패턴
  - NLF에서 알파벳 맞추는 네트워크
- CNN
  - Translation invariant
  - 이미지의 기하학적 위상적 패턴
  - 이미지안의 cannel 위치 상관없이 있는지 아닌지 판단
- RNN
  - 데이터의 입출력에 순서가 중요하게 작용
  - 자연어 처리
- GNN
  - 이미지를 그래프로 표현, 각 객체의 관계성을 표현
  - 순서는 상관없으나, 관계가 중요  

### Skip Connection
- 고주파 저주파
  - HF: 쉽게 사라진다
  - LF: 멀리 간다
- 깊은 네트워크
  - HF가 사라짐, 기울기 폭주 or 소실
- Skip Connection 사용이유
  - U-net: 깊은 네트워크에서 쉽게 사라지는 HF를 네트워크 시작에서 끝으로 전달
  - ResNet
    - 네트워크가 언제나 깊으면? 이미지 백장에 네트워크 깊이가 오천만이면? 
    - 정확한 데이터셋 크기와 모델의 비선형성을 계산할 수 없음
    - 데이터에게 두 가지 길을 제시: 모든 레이어를 통과할 것인지 아닌지
    - HF 전달


# pix2pix_colorization_1
[Isola, Phillip, et al., 2017] (https://arxiv.org/pdf/1611.07004.pdf, "참고 논문")

## Intro
pix2pix를 활용하여 흑백 이미지를 컬러 이미지로 변환

### AI Intro.
AI/Machine Learing/Deep Learing
- Artiicial Intelligence
  - Applications
    - Computer Vision
    - Speech Recognition
    - Natural Language
    - Processing etc.
  - Machine Learning
    - 통계를 기반으로 퍼셉트론 하나
    - Linear Regression
    - Probabilistic Graphical Model
    - Deep Learning: 레이어 많음 

- ML로 컴퓨터에 이미지를 이해시키자!!
  -  Computer Vision
  -  Image Processing
  -  Graphics
  -  Computational Phography

- Computer Vision
  - Machine Learing
  - Mathematics Statistics
  - Roboics
  - Computer Graphics
  - Signal Processing

## GAN
있을 법한 이미지 생성

### Overview
Train data ---Real sample---> Discriminator ---Is sample real?---> *p*

Noise ------> Generator --- Fake sample ---> Discriminator ---Is sample real?---> *p*

**Discriminator(D)는 진짜 이미지와 Generator(G)가 만든 가짜 이미지인지 판별**
**D는 더 잘 판별, G는 더 잘 속이도록 학습진행**

### Loss Function
Binary Cross Entropy
D is trained to discriminate sample from data.
Gradients of D guides G(z) to flow to regins more likely to be classified as data.
D(x)=1/2
pg=pdata

### Mode Collapse
D가 어떤 이상한 이미지를 진짜라고 잘못 판별한 경우: G가 주구장창 이상한 이미지를 생성
D가 제대로 판별하지 못하는 어떠한 이미지을 G가 반복적으로 생성

### 모든 이미지들은 어떤 노이즈로 만들어짐
(smiling woman) - (neutral woman) + (netural man) = (smiling man)
(man with glasses) - (man without glasses) + (woman without galsses) = (woman with glasses)
데이터 생성에 있어 많은 가능성이 존재
interpolation 변화: 노이즈를 조금씩 변화시켜 새로운 데이터 생성

## Color Space
### RGB
Red Channel + Green Channel + Bluew Channel

### Lab
Lightness Channel + a Channel + b Channel
- Lightness Channel: 빛의 강도, 흑백 채널
- a Channel: 초록색과 빨강색의 비율
- b Channel: 노란색과 파란색의 비율

### Lab를 사용하여 코딩
RGB를 흑백으로 바꾸고 딥러닝으로 컬러 이미지(RGB)예측: R, G, B채널 예측
Lab에서 L을 딥러닝으로 넣고 컬러 이미지(a,b)예측: a, b 채널 예측




