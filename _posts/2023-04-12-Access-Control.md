---
layout: post
title: "서버 접근 통제와 3A"
date: 2023-04-12
categories: "notes"
---

서버 접근 통제

- 개념 : 사람 또는 프로세스가 비인가자로부터 객체의 기밀성, 무결성, 가용성을 보장하기 위해 서버 내 파일에 읽기, 쓰기, 실행 등의 접근 여부를 허가 또는 거부하는 기능

- 유형

| 유형 | 설명 |
| :------ | :----- |
| DAC (Discretionary Access Control) | 신원 기반의 접근 통제 기법 (임의적 접근 통제) |
| MAC (Mandatory Access Control) | 권한 기반의 접근 통제 기법 (강제적 접근 통제) |
| RBAC (Role Based Access Control) | 역할 기반의 접근 통제 기법 (역할 기반 접근 통제) |

* 3A (Authentication, Authorization, Accounting)

| 구성 | 설명 |
| :-----: | :----- |
| 인증 (Authentication) | 접근을 시도하는 가입자 또는 단말에 대한 식별 및 신분 검증 |
| 권한 부어 (Authorization) | 검증된 가입자나 단말에게 일정 수준의 권한과 서비스 허용 |
| 계정 관리 (Accounting) | 리소스 사용에 대한 정보를 수집하고 관리하는 서비스 |
