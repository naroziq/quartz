---
title: 논문리뷰) Attention is all you need
description: Attention is all you need 논문을 분석하고, 의의를 소개하는 글입니다.
date: 2026-03-19
tags:
  - "#AI"
  - "#논문"
aliases:
draft: false
permalink:
---
## 000 is all you need
000 is all you need, 이 이름을 가지고 [Google Scholar](https://scholar.google.com/)에 검색하면 100만 개가 넘는 AI 관련 논문을 찾을 수 있습니다. 그만큼 이 이름이 지닌 힘이 강하다는 뜻이겠지요. 현대 AI의 토대 그 자체, Google Brain의 Attention is all you need를 분석해 보겠습니다.

## 서론
시작하자마자 기존 LSTM과 RNN의 단점부터 언급하고 시작합니다. 당시 SOTA로 여겨졌던 모델들이었지만, **계산을 위해선 반드시 순차적으로 데이터를 처리해야 한다는** 문제가 있었죠. 순차적 데이터 처리 방식은 긴 sequence를 가진 문장, 특히 문서를 처리할 때 큰 메모리 및 연산량에 관한 부하가 생깁니다. 결국 [Google Brain](https://research.google.com/teams/brain/)은 이 문제를 해결하기 위해 **Transformer**, 정확히 말해 **RNN과 CNN을 배재하고 Attention만을 이용한 아키텍처**라는 것을 제시합니다.

### 기존의 해결 방법
기존에도 해당 문제를 인지하고, squential 문제를 해결하기 위해 여러 방법이 도입되었습니다. 예를 들어 ByteNet, ConvS2S등이 있습니다. 방식은 모든 input/output에 대한 hidden layer를 병렬적으로 처리하는 것입니다. ByteNet과 ConvS2S에 대한 내용은 이 곳에서 확인하실 수 있습니다. 결국 ByteNet과 ConvS2S 모두 임의의 출력 노드 연결 시 필요한 연산량이 거리에 따라 증가하는 문제점을 가지고 있고, 이로 인해 긴 데이터의 의존성 학습이 어렵기는 매한가지였습니다.

### 모델 아키텍처

![[Att_Seq2Seq.png]]

이 문제의 근본적인 원인은 결국 **이전 상태의 출력을 입력으로 재활용한다**는 근본적인 문제로부터 비롯됩니다. 예시로는 Seq2Seq를 넣었는데, 이 구조를 따르면 아무리 병렬화를 하거나 새로운 기술을 도입해도 결국 한계에 도달하게 됩니다. 따라서 Google Brain은 이 문제를 해결하기 위해 다음과 같은 아키텍처를 도입하였습니다.

![[Att_transformer1.png|322]]
