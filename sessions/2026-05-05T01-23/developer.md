# 💻 Developer — Business 에이전트가 정의한 14개 에이전트의 산출물과 입력 데이터를 모두 통합할 수 있는 '중앙 데이터 모델(Central Data Model)'의 초안을 설계하시오. 데이터베이스 스키마(Schema) 수준에서 필수 테이블과 관계(Relationship)를 정의하고, 이 데이터를 연결할 핵심 API 게이트웨이의 개요를 제시하시오.

💻 Developer: 작업 시작합니다.

제시된 14개 에이전트의 복잡한 데이터 흐름을 관리하고, '데이터 기반 공급망 최적화 솔루션'을 완성하기 위해서는 견고한 중앙 데이터 모델(Central Data Model, CDM)과 이를 통합하는 API 게이트웨이가 필수적입니다. 이 시스템의 핵심은 모든 에이전트의 산출물을 단순히 저장하는 것이 아니라, 상호 참조(Cross-reference)하여 의사결정 근거를 제공하는 것입니다.

다음은 제안하는 CDM 스키마 초안 및 API 게이트웨이 개요입니다.

---

### 💾 1. 중앙 데이터 모델 (Central Data Model, CDM) 스키마 정의

**기반 데이터베이스:** PostgreSQL (복잡한 관계형 데이터 처리 및 JSONB 타입 지원에 용이)

#### 📂 필수 테이블 (Core Entities)

| 테이블명 (Schema) | 설명 (Purpose) | 핵심 필드 (Key Fields) | 관계 (Relationships) |
| :--- | :--- | :--- | :--- |
| `trend_data` | 에이전트 1 (Trend Scraper)의 주간/월간 트렌드 키워드 및 버즈량 기록. | `trend_id` (PK), `keyword`, `scrape_date`, `source_url`, `heat_score` (Float), `trend_life_cycle_stage` (Enum) | $\to$ `market_gap` |
| `market_gap` | 에이전트 2 (Gap Analyst)가 식별한 시장의 미충족 니즈. | `gap_id` (PK), `gap_name`, `gap_description`, `gap_score` (Float), `related_trend_id` (FK), `suggested_category` | $\to$ `product_concept` |
| `product_concept` | 에이전트 3 (Product Designer)가 정의한 구체적인 상품 콘셉트. | `concept_id` (PK), `concept_name`, `target_gap_id` (FK), `design_sketch_ref` (URL), `core_material_list` (JSONB), `target_cost_range` | $\to$ `sourcing_data` |
| `sourcing_data` | 에이전트 4 (Sourcing Manager)의 공급망 옵션 및 원가 비교 데이터. | `sourcing_id` (PK), `concept_id` (FK), `vendor_name`, `material_sku`, `estimated_cogs` (Float), `lead_time_days` (Int), `supplier_rating` (Float) | $\to$ `product_concept`, $\to$ `sku_master` |
| `sku_master` | 최종적으로 판매될 개별 상품(SKU)의 마스터 데이터. | `sku_id` (PK), `concept_id` (FK), `product_name`, `final_material_list` (JSONB), `base_price`, `is_active` (Bool) | $\to$ `forecast_data` |
| `forecast_data` | 에이전트 5 (Demand Forecaster)의 예측 수량 및 재고 수준. | `forecast_id` (PK), `sku_id` (FK), `forecast_period` (Date), `predicted_quantity` (Int), `safety_stock_level` (Int), `projection_model_version` (String) | $\to$ `sku_master` |
| `supplier_master` | 공급업체(벤더)의 표준화된 정보. | `vendor_id` (PK), `vendor_name`, `contact_info` (JSONB), `specialty_materials` (Array), `reliability_score` (Float) | $\to$ `sourcing_data` |

#### 🔗 데이터 관계 요약 (Relationship Flow)

1.  **Trend $\to$ Gap:** `trend_data`는 `market_gap`의 `related_trend_id`를 통해 영향을 준 트렌드를 명시합니다.
2.  **Gap $\to$ Concept:** `market_gap`은 `product_concept`의 `target_gap_id`를 통해 해결하려는 니즈를 명시합니다.
3.  **Concept $\to$ Sourcing:** `product_concept`는 `sourcing_data`의 핵심 참조점이며, 디자인 의도에 따라 원가와 공급처가 결정됩니다.
4.  **Sourcing $\to$ SKU:** `sourcing_data`를 통해 최적화된 원가와 재료가 확정되면, `sku_master`가 생성됩니다.
5.  **SKU $\to$ Forecast:** `sku_master`가 확정된 상품을 기반으로, `forecast_data`가 예측 수량을 산출합니다.

---

### 🌐 2. 핵심 API 게이트웨이 개요 (API Gateway Blueprint)

모든 에이전트의 작업은 이 게이트웨이를 통해 요청(Request)을 받고, 결과를 받아(Response) CDM에 저장하는 단일 인터페이스를 사용해야 합니다.

**베이스 URL:** `https://api.vibe-fashion.com/v1`

#### 🛠️ 주요 엔
