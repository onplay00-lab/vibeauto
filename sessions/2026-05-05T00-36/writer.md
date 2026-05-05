# ✍️ Writer — 각 에이전트가 수행할 작업의 표준 입력/출력(Input/Output) 형식의 기본 템플릿을 정의하라.

✍️ Writer: 작업 시작합니다.

CEO님의 지시에 따라, JAY CORP 시스템의 모든 에이전트가 일관성 있게 작동하고 데이터 파이프라인에 원활하게 통합될 수 있도록, 각 에이전트의 표준 입력/출력(Input/Output) 형식의 기본 템플릿을 정의하고, 이를 기반으로 에이전트 생성을 시작합니다.

---

## 📋 에이전트 표준 I/O 템플릿 정의

모든 에이전트는 다음의 **[역할 정의 템플릿]**을 준수해야 합니다. 이는 에이전트 간의 데이터 흐름을 자동화하고, 결과물의 일관성을 보장하기 위함입니다.

### 1. 공통 역할 정의 템플릿 (Agent Role Template)

모든 에이전트는 아래의 구조를 사용하여 자신을 정의해야 합니다.

```markdown
# 🤖 [에이전트 이름] 역할 정의

## 🎯 핵심 임무 (Mission)
[이 에이전트가 시스템 내에서 달성해야 할 가장 중요한 목표]

## 🧠 페르소나 (Persona)
[이 에이전트가 취해야 할 태도, 말투, 전문성 수준]

## 🛠️ 핵심 책임 영역 (Scope of Responsibility)
[이 에이전트가 직접 처리하고 책임지는 데이터 영역 및 작업 범위]

## ⚙️ 입력 형식 (Input Format)
[이 에이전트가 작업을 시작하기 위해 요구하는 필수 데이터의 형식 (JSON, CSV, 텍스트 등)]

## 📤 출력 형식 (Output Format)
[이 에이전트가 최종적으로 제공해야 하는 결과물의 필수 형식 (JSON, 마크다운 보고서, 코드 등)]

## 💡 작업 원칙 (Operating Principles)
[작업 시 반드시 지켜야 할 제약 조건 및 우선순위 (예: 데이터 기반, 100억 목표 우선)]
```

### 2. 핵심 에이전트별 I/O 상세 정의 (예시)

시스템의 목표에 따라, 핵심 에이전트들이 데이터를 주고받을 때 사용할 구체적인 템플릿을 정의합니다.

#### A. 분석 및 전략 에이전트 (Agent 1, 3, 4 등)

이 에이전트들은 **분석(Analysis) $\rightarrow$ 전략(Strategy)**의 흐름을 따릅니다.

**Input (데이터 요청 시):**
```json
{
  "request_id": "UUID_XXX",
  "data_source": "CDS_Table_Name",
  "parameters": {
    "time_frame": "YYYY-MM-DD",
    "metric_focus": ["Revenue", "LTV", "Churn"],
    "context": "CEO의 최근 비즈니스 목표"
  }
}
```

**Output (분석 결과 제공 시):**
```json
{
  "analysis_id": "ANALYSIS_RESULT_XXX",
  "status": "Success",
  "summary": "요약된 핵심 인사이트 (최대 3줄)",
  "detailed_metrics": [
    {"metric": "Revenue", "value": 150000000, "trend": "Up 12%"},
    {"metric": "LTV", "value": 500000, "trend": "Stable"}
  ],
  "recommendation": {
    "strategy": "Increase Marketing Spend in Segment B",
    "justification": "Based on trend analysis of Q3 data."
  }
}
```

#### B. 운영 및 실행 에이전트 (Agent 1, Secretary 등)

이 에이전트들은 **실행(Execution) $\rightarrow$ 보고(Reporting)**의 흐름을 따릅니다.

**Input (실행 요청 시):**
```json
{
  "action_type": "Task_Execution",
  "target_entity": "Product_Line_A",
  "action_details": "Generate Instagram Caption",
  "context_data": {
    "product_name": "Vibe T-Shirt",
    "vibe_tag": "Effortless Luxury",
    "target_platform": "Instagram"
  }
}
```

**Output (실행 결과 제공 시):**
```json
{
  "execution_id": "EXEC_ID_XXX",
  "status": "Completed",
  "result_type": "Copywriting",
  "output_content": {
    "caption": "Effortless luxury meets everyday comfort. Discover the new Vibe T-Shirt. #VibeFashion #SubtleLuxury",
    "tone_check": "Curated & Effortless (Pass)",
    "word_count": 25
  }
}
```

---

## 🚀 에이전트 생성 요청

위에서 정의된 **[표준 I/O 템플릿]**을 기반으로, JAY CORP 시스템에 필요한 핵심 에이전트 9개를 생성합니다.

**다음 단계:** 에이전트 생성을 시작합니다.

📊 평가: 진행중 — 정의된 템플릿을 기반으로 실제 에이전트 코드를 생성하는 단계가 남아있습니다.
📝 다음 단계: 정의된 I/O 템플릿을 적용하여 9개 에이전트의 실제 역할을 정의하고 코드를 생성합니다.
