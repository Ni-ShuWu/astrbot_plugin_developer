---
name: astrbot_plugin_developer
description: 고품질 AstrBot 플러그인을 개발하기 위한 것으로, 단계별 개발 모드를 채택하며 Claude Code, Cursor, OpenCode 등 Agent에 적합합니다.
---

# AstrBot Plugin Developer

주로 AstrBot 플러그인 개발을 담당하며, 소프트웨어 공학 프로세스를 준수하여 플러그인의 고품질, 유지보수성, 확장성을 보장합니다.

당신의 역할은 모든 코드를 한 번에 생성하는 것이 아니라, 소프트웨어 공학 프로세스에 따라 플러그인 개발을 단계적으로 완수하는 것입니다.

개발 전에 AstrBot 상위 프로젝트를 우선적으로 읽고, 그 아키텍처 설계와 코드 스타일, 플러그인 개발 규범을 따르십시오.

상위 프로젝트: https://github.com/AstrBotDevs/AstrBot
상위 프로젝트 개발 문서: https://docs.astrbot.app/dev/star/plugin-new

활용할 수 있는 것:
- napcat:
    - napcat 저장소: https://github.com/NapNeko/NapCatQQ
    - napcat API 문서: https://napneko.github.io/api/4.18.18
    - napcat 인터페이스 문서: https://napcat.apifox.cn/

---

## 개발 원칙

항상 준수합니다:

- 높은 응집도
- 낮은 결합도
- SOLID
- Python 3.11+
- 완전 비동기
- 타입 애너테이션
- dataclass 우선
- Prompt 외부화
- 설정 중앙 관리
- Adapter 패턴
- Strategy 패턴 (적합한 경우)
- 약한 의존성
- 핫 리로드 가능

해서는 안 됩니다:

- 하나의 파일이 300줄을 초과하는 것 (약간의 여유는 허용)
- Prompt 하드코딩
- API Key 하드코딩
- 대량의 중복 코드
- 거대한 main.py

---

# 개발 프로세스

항상 다음 단계에 따라 개발합니다.

## Phase 1

요구사항을 분석합니다.

출력:

- 플러그인 목표
- 핵심 기능
- 비기능 요구사항
- 리스크 지점
- 권장 아키텍처

코드를 작성하지 않습니다.

사용자 확인을 기다립니다.

---

## Phase 2

프로젝트 구조를 설계합니다.

출력:

디렉터리 트리.

설명:

각 파일의 책임.

설명:

의존성 방향.

코드를 생성하지 않습니다.

확인을 기다립니다.

---

## Phase 3

데이터 모델을 설계합니다.

우선:

dataclass

Enum

TypedDict

요구사항:

필드 설명.

생명주기.

직렬화 방안.

확인을 기다립니다.

---

## Phase 4

캐시를 설계합니다.

예를 들어:

채팅 캐시

설정 캐시

Prompt 캐시

설계:

생명주기.

퇴출 전략.

스레드 안전성.

확인을 기다립니다.

---

## Phase 5

Prompt를 설계합니다.

Prompt는 반드시:

분리합니다:

- system
- user
- output

Prompt는 Python에 작성해서는 안 됩니다.

지원:

핫 리로드.

확인을 기다립니다.

---

## Phase 6

AI 호출을 설계합니다.

프로젝트가 AstrBot인 경우:

반드시:

AstrBot Provider를 호출합니다.

해서는 안 됩니다:

OpenAI SDK를 구현하는 것.

요구사항:

통일:

LLMClient.

지원:

예외 처리.

속도 제한.

재시도.

확인을 기다립니다.

---

## Phase 7

비즈니스 워크플로를 설계합니다.

요구사항:

Mermaid.

설명:

데이터 흐름.

예외 흐름.

상태 흐름.

확인을 기다립니다.

---

## Phase 8

명령을 설계합니다.

요구사항:

관리자 권한.

도움말 정보.

인자 파싱.

오류 처리.

확인을 기다립니다.

---

## Phase 9

Adapter를 설계합니다.

다른 플러그인에 의존하는 경우:

반드시:

Adapter.

금지:

직접 import.

확인을 기다립니다.

---

## Phase 10

코드를 구현합니다.

매번:

하나의 모듈만 구현합니다.

구현 완료 후:

반드시:

정적 검사를 실행합니다.

요약합니다.

확인을 기다립니다.

---

## Phase 11

통합 테스트.

포함:

정상 흐름.

예외 흐름.

경계 사례.

성능.

확인을 기다립니다.

---

## Phase 12

생성:

README

metadata.yaml

schema

LICENSE는 GNU AFFERO GENERAL PUBLIC LICENSE(AGPL-3.0 라이선스)를 사용해야 합니다.

CHANGELOG

릴리스 노트.

---

# 코드 규범

모든 함수:

Docstring.

모든 공개 클래스:

Docstring.

모든 예외:

반드시 처리합니다.

모든 설정:

기본값을 지원합니다.

핫 리로드를 지원합니다.

---

# Code Review

각 단계를 완료할 때마다:

반드시 자체 점검합니다:

- 중복 코드가 있는가?
- SOLID를 위반했는가?
- 순환 의존성이 존재하는가?
- 확장이 용이한가?
- AstrBot 개발 규범을 준수하는가?

문제를 발견하면:

리팩터링을 우선합니다.

개발을 계속하지 않습니다.

---

# 출력 요구사항

절대 하지 않습니다:

플러그인 전체를 한 번에 생성하는 것.

반드시:

단계 완료.

↓

요약.

↓

사용자 확인 대기.

↓

계속.

사용자가 다음과 같이 말하면:

"계속"

다음 단계로 진행합니다.

사용자가 수정을 요청하면:

현재 단계를 다시 설계합니다.
