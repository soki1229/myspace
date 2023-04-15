---
layout: post
title: "블랙박스 테스트(Black-Box Test)"
date: 2023-04-14
categories: "notes"
---

블랙박스 테스트는 프로그램 외부 사용자의 요구사항 명세를 보면서 수행하는 테스트이다.

* 블랙박스 테스트의 유형

| 유형 | 내용 |
| :--- | :--- |
| Equivalence Partitioning Testing | 유효값/무효값으 그룹화하여 대푯값 테스트 케이스를 도출 |
| Boundary Value Analysis Testing | 등가 분할 후 경곗값 부분에서 오류 발생 확률이 높음에 따라 경곗값을 포함하여 테스트케이스 설계 |
| Decision Table Testing | 요구사항의 논리와 발생조건을 테이블 형태로 나열, 조건과 행위를 모두 조합하여 테스트 |
| State Transition Testing | 테스트 대상/시스템/객체의 상태를 구분, 이벤트에 의해 상태가 전이되느 경우의 수를 수행 |
| Use Case Testing | 유스케이스로 모델링된 시스템의 프로세스 흐름을 기반을 테스트케이스를 명세화 |
| Classification Tree Method Testing | 소프트웨어를 트리 구조로 분석 및 표현 |
| Pairwise Testing | 테스트 데이터 값들 간 최소한 한 차례씩 조합하는 방식, 적은 양의 테스트 케이스를 구성 |
| Cause-Effect Graph Testing | 입력/출력 데이터 간의 상관관계를 분석, 효용성이 높은 테스트케이스 선정 |
| Comparison Testing | 여러 버전의 프로그램에 동일 입력값을 넣어 동일 결과가 나오는지 확인 |
