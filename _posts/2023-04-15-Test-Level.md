---
layout: post
title: "테스트 레벨(Test Level)의 종류"
date: 2023-04-15
categories: "notes"
---

1. 단위 테스트 (Unit Test)

- 구현이 진행되면서 수행하는 테스트이다. 소프트웨어 설계의 최소 단위인 모듈이나 컴포넌트에 초점을 맞춘 테스트이다.
명세 기반 테스트와 구조 기반 테스트로 나뉘지만, 주로 구조 기반 테스트(화이트 박스 테스트) 위주로 수행한다.

2. 통합 테스트 (Integration Test)

- 각 모듈 간 인터페이스 관련 오류/결함을 찾는 체계적이 테스트 기법이다.

3. 시스템 테스트 (System Test)

- 통합된 단위 시스템의 기능이 시스템에서 정상적으로 수행되는지 검증하는 테스트이다.
기능적 요구사항 테스트와 비기능적 요구사항 테스트가 있다.

4. 인수 테스트 (Acceptance Test)

- 최종 사용자와 업무 이해관계자 등이 테스트를 수행함으로써 개발된 제품에 대해 운영 여부를 결정하는 테스트이다.

* 인수 테스트의 종류

| 종류 | 설명 |
| :-- | :-- |
| 사용자 인수 테스트 | 사용자가 시스템 사용의 적절성 여부 등을 확인 |
| 운영상의 인수 테스트 | 관리자가 인수 시 수행하며, 백업/복원, 재해 복구, 사용자 관리, 정기 점검 등을 확인 |
| 계약 인수 테스트 | 계약 상의 인수/검수 조건 등의 충족 여부 등을 확인 |
| 규정 인수 테스트 | 지침/법규/규정 등이 맞게 개발되었는지 확인 |
| 알파 테스트 | 실제 사용자가 개발자 환경에서 통제된 상태로 개발자와 함께 수행 |
| 베타 테스트 | 실제 환경에서 일정 수의 사용자에게 소프트웨어를 사용하게 하고 피드백을 받음 |
