# PrivateLLM — 개인용 AI 컴패니언 챗봇

> 사람과 대화하는 듯한 경험을 주는 검열 없는 AI 파트너.
> 단짝, 연인 같은 감정적 연결이 가능한 개인 전용 챗봇을 구축한다.

## What is this?

상용 AI(ChatGPT, Gemini)는 개인정보 기억 거부, 역할극 제한, 분위기 연출 차단 등 혼자 쓰기에도 불필요한 제약이 많다. 이 프로젝트는 **Abliterated 오픈소스 모델 + RunPod 클라우드 GPU**를 활용하여, 기억하고, 일관된 성격을 유지하며, 자유롭게 대화하는 AI 컴패니언을 만든다.

| 항목 | 내용 |
|------|------|
| **목표** | 사람 같은 대화 경험 — 기억, 인격 일관성, 감정적 연결 |
| **모델 전략** | Gemma 3 27B / Qwen 2.5 72B Abliterated (비교 후 확정) |
| **인프라** | RunPod 클라우드 GPU (A6000/A100) |
| **핵심 시스템** | 페르소나 정의, 장기 기억 (벡터DB + RAG), 채팅 UI |

## Tech Stack

| 분류 | 기술 |
|------|------|
| LLM 서빙 | Ollama + Abliterated 모델 (27B~72B) |
| 클라우드 GPU | RunPod (A6000 48GB / A100 80GB) |
| 장기 기억 | 벡터DB (ChromaDB 등) + RAG |
| 임베딩 | sentence-transformers (예정) |
| 채팅 UI | 미정 (Phase 5에서 결정) |

## Phases

| Phase | 내용 | 상태 |
|-------|------|------|
| **1** | 텍스트 LLM 즉시 구동 (Ollama, 로컬) | **완료** |
| **2** | RunPod + 모델 선정 & 비교 테스트 | 대기 |
| **3** | 페르소나 설계 + 시스템 프롬프트 | 대기 |
| **4** | 장기 기억 시스템 (벡터DB + RAG) | 대기 |
| **5** | 채팅 UI 구축 | 대기 |
| **6+** | TTS/음성, 아바타, 이미지 생성 등 확장 | 대기 |

## Project Structure

```
PrivateLLM/
├── configs/           # 설정 파일 (페르소나, 프롬프트 등)
├── scripts/           # 유틸리티 스크립트
├── data/              # 대화 데이터, 기억 DB
├── docs/              # 설계 문서
│   ├── MASTER_PLAN.md # 마스터 플랜 v3 (기본 설계 문서)
│   └── handoff/       # 세션 핸드오프
├── Modelfile          # Ollama 커스텀 모델 설정 (Dolphin Llama 3)
├── Modelfile.qwen3    # Ollama 커스텀 모델 설정 (Qwen3 14B)
└── README.md
```

## Quick Start

```bash
# Phase 1 (로컬 테스트): Ollama 설치 후
ollama run dolphin-llama3

# Phase 2 (RunPod): 대형 모델 테스트
ollama run huihui_ai/gemma3-abliterated:27b
```

## 문서 규칙

- **설계/기술 결정의 진실 기준** = 이 레포의 `docs/`
- **학습/성찰 기록** = The Record (`2_Projects/PrivateLLM/_index.md`)
- 세션 핸드오프는 `docs/handoff/YYYY-MM-DD.md`에 기록
