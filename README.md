# PrivateLLM — 프라이빗 Uncensored LLM 구축 및 파인튜닝

> RunPod 환경에서 오픈소스 LLM을 기반으로, 검열 없는 독립 추론 시스템을 구축하고 파인튜닝하는 프로젝트.

## What is this?

상용 AI 서비스의 거절(Refusal) 제약을 벗어나, 자체 GPU 인프라에서 완전히 통제 가능한 LLM을 운영하기 위한 기술 프로젝트입니다.

| 항목 | 내용 |
|------|------|
| **목표** | Uncensored LLM 서빙 + 커스텀 파인튜닝 파이프라인 구축 |
| **인프라** | RunPod (RTX 4090 / A6000) |
| **핵심 기술** | QLoRA, EXL2/GGUF 양자화, vLLM, Unsloth |
| **베이스 모델** | Abliterated Llama 3, Dolphin, Midnight-Miqu, Mixtral |

## Tech Stack

| 분류 | 기술 |
|------|------|
| 언어 | Python 3.10+ |
| 파인튜닝 | Unsloth / Axolotl, QLoRA |
| 추론 엔진 | vLLM, Oobabooga Text-Generation-WebUI |
| 양자화 | EXL2, GGUF |
| 인프라 | RunPod, Docker (CUDA 12.1) |
| 데이터셋 | Dolphin, OpenHermes 2.5, PIPPA, LimaRP |

## Project Structure

```
PrivateLLM/
├── configs/           # 학습/추론 설정 YAML
├── scripts/           # RunPod 셋업, 데이터 전처리, 학습 스크립트
├── data/              # 전처리된 데이터셋 (JSONL)
├── notebooks/         # 실험/분석용 Jupyter 노트북
├── docs/              # 설계 문서, 실험 로그
│   └── handoff/       # 세션 핸드오프
└── README.md
```

## Quick Start

```bash
# 1. 환경 설정
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt

# 2. 설정 파일 수정
cp configs/example.yaml configs/train.yaml

# 3. 파인튜닝 실행 (로컬 또는 RunPod)
python scripts/train.py --config configs/train.yaml
```

## 문서 규칙

- **설계/기술 결정의 진실 기준** = 이 레포의 `docs/`
- **학습/성찰 기록** = The Record (`2_Projects/PrivateLLM/_index.md`)
- 세션 핸드오프는 `docs/handoff/YYYY-MM-DD.md`에 기록
