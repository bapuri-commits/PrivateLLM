# PrivateLLM — 검열 없는 개인용 AI 시스템

> 오픈소스 모델/도구를 조합하여, 텍스트·이미지·영상을 다루는 uncensored AI 환경을 구축하는 프로젝트.

## What is this?

상용 AI 서비스(ChatGPT, Midjourney 등)의 검열 제약 없이, 로컬 GPU에서 자유롭게 사용할 수 있는 개인용 AI 시스템을 구축합니다. 밑바닥부터 만드는 게 아니라, **이미 잘 만들어진 오픈소스 제품을 조합**하고, 필요한 부분만 선택적으로 강화합니다.

| 항목 | 내용 |
|------|------|
| **목표** | Uncensored 텍스트 LLM + 이미지 생성/편집 + 영상 처리 |
| **전략** | 기존 오픈소스 제품 조합 → 사용 → 평가 → 필요한 부분만 강화 |
| **로컬 GPU** | RTX 3080 Ti (12GB) — 8B LLM, SDXL/Flux 이미지 생성 가능 |
| **클라우드** | RunPod — 70B 모델, 대규모 작업 시 사용 |

## Tech Stack

| 분류 | 기술 |
|------|------|
| 텍스트 LLM | Ollama + Dolphin / Abliterated 모델 |
| 이미지 생성 | ComfyUI + SDXL / Flux |
| 이미지 제어 | ControlNet (포즈/깊이), IP-Adapter |
| 영상 처리 | AnimateDiff, Stable Video Diffusion |
| 클라우드 GPU | RunPod (필요 시) |

## Phases

| Phase | 내용 | 인프라 |
|-------|------|--------|
| **1** | 텍스트 LLM 즉시 구동 (Ollama) | 로컬 |
| **2** | 이미지 생성/편집 환경 (ComfyUI) | 로컬 |
| **3** | 영상 처리 (이미지→영상, 보정) | 로컬/RunPod |
| **4** | 평가 및 선택적 강화 | 상황에 따라 |
| **5+** | AI 영상 생성, API 서빙, 파인튜닝 | RunPod |

## Project Structure

```
PrivateLLM/
├── configs/           # 설정 파일
├── scripts/           # 유틸리티 스크립트
├── data/              # 데이터
├── notebooks/         # 실험/분석용
├── docs/              # 설계 문서
│   ├── MASTER_PLAN.md # 마스터 플랜 (기본 설계 문서)
│   └── handoff/       # 세션 핸드오프
└── README.md
```

## Quick Start

```bash
# Phase 1: 텍스트 LLM (Ollama 설치 후)
ollama run dolphin-llama3
```

## 문서 규칙

- **설계/기술 결정의 진실 기준** = 이 레포의 `docs/`
- **학습/성찰 기록** = The Record (`2_Projects/PrivateLLM/_index.md`)
- 세션 핸드오프는 `docs/handoff/YYYY-MM-DD.md`에 기록
