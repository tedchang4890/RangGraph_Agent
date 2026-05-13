# 🏋️‍♂️ 맞춤형 운동 추천 멀티 에이전트 시스템 (Multi-Agent Exercise Recommender)

사용자의 현재 신체 상태와 고민(증상)을 분석하여, 이를 해결할 수 있는 **최적의 운동을 추천해 주는 AI 에이전트 파이프라인**입니다. 

LangGraph를 활용하여 여러 에이전트가 각자의 역할을 수행하며(증상 추출 ➡️ 운동 추천 ➡️ 최종 답변 정리), 로컬 LLM인 Ollama를 사용하여 외부 API 비용 없이 안전하고 빠르게 동작합니다.

---

## 🛠 기술 스택 (Tech Stack)

- **Language:** Python 🐍
- **LLM:** Ollama 🦙 (Model: `exaone3.5:2.4b`)
- **Framework:** 
  - LangChain 🦜🔗 (프롬프트 체인 구성 및 LLM 연동)
  - LangGraph 🕸️ (상태 기반 멀티 에이전트 워크플로우 구축)

---

## 🤖 멀티 에이전트 파이프라인 소개

이 시스템은 단일 LLM에 모든 것을 맡기지 않고, 정확도와 논리성을 높이기 위해 3개의 특화된 에이전트로 작업을 분할하여 처리합니다.

1. **Extractor Agent (증상 추출 에이전트)**
   - 사용자의 자연어 질문에서 핵심적인 신체 상태나 증상(예: 체력 저하, 체중 증가 등)만 정확하게 추출합니다.
2. **Matcher Agent (후보 추천 에이전트)**
   - 추출된 증상 데이터를 바탕으로, 해당 문제를 개선하는 데 가장 효과적인 운동 후보 3가지를 논리적으로 추론합니다.
3. **Answer Agent (답변 생성 에이전트)**
   - 앞선 에이전트들의 결과(증상, 운동 후보군)를 종합하여, 사용자가 읽기 쉽도록 개조식(Bullet points)으로 최종 답변을 정리해 줍니다.

---

## 🗺️ 그래프 구조 (LangGraph Architecture)

시스템의 실행 흐름은 아래 그래프와 같습니다. `extractor`에서 시작하여 `matcher`를 거쳐 `answer` 노드에서 종료(`END`)됩니다.

<img width="105" height="430" alt="스크린샷 2026-05-13 15 54 24" src="https://github.com/user-attachments/assets/44dcd2c6-c245-4a34-9d8c-f13215d66638" />

---

## 🚀 실행 결과 (Results)

**💡 사용자 질의 (Query):**  
> *"체력이 안좋고, 살이 계속 찌는데 어떤 운동을 할까?"*

시스템을 거쳐 최종적으로 다듬어진 AI의 맞춤형 운동 추천 결과입니다.

<img width="910" height="162" alt="스크린샷 2026-05-13 15 55 17" src="https://github.com/user-attachments/assets/915a1b04-1e67-4c23-8881-c1005ad96649" />
<img width="910" height="520" alt="스크린샷 2026-05-13 15 55 07" src="https://github.com/user-attachments/assets/ee70a3e3-a678-4b12-963e-f9be2355ea20" />
