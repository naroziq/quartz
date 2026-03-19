---
title: 논문리뷰) Attention is all you need
description: Attention is all you need 논문을 분석하고, 의의를 소개하는 블로그입니다.
date: 2026-03-19
tags:
  - "#AI"
  - "#논문리뷰"
aliases:
draft: false
permalink:
---
## 000 is all you need
000 is all you need, 이 이름을 가지고 [Google Scholar](https://scholar.google.com/)에 검색하면 100만 개가 넘는 AI 관련 논문을 찾을 수 있습니다. 그만큼 이 이름이 지닌 힘이 강하다는 뜻이겠지요. 현대 AI의 토대 그 자체, Google Brain의 Attention is all you need를 분석해 보겠습니다.

## 배경
시작하자마자 기존 LSTM과 RNN의 단점부터 언급하고 시작합니다. 당시 SOTA로 여겨졌던 모델들이었지만, **계산을 위해선 반드시 순차적으로 데이터를 처리해야 한다는** 문제가 있었죠. 순차적 데이터 처리 방식은 긴 sequence를 가진 문장, 특히 문서를 처리할 때 큰 메모리 및 연산량에 관한 부하가 생깁니다. 물론 일부 해결책이 있었지만, 모두 근본적인 해결책은 되지 못했습니다. 결국 [Google Brain](https://research.google.com/teams/brain/)은 이 문제를 해결하기 위해 **Attention**, 정확히 말해 **Attention을 이용한 Transformer**라는 것을 제시합니다.

##