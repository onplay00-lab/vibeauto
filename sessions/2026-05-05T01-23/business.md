# 💰 Business — 14개 에이전트의 목록(에이전트 이름)을 최종 확정하고, 각 에이전트별로 '필요한 입력 데이터(Input Data)', '산출물(Output Deliverable)', 그리고 '기대되는 KPI'를 표 형태로 상세히 정의하시오. 이 단계는 단순한 목록 나열이 아닌, 실제로 회사 시스템에 녹아들 수 있는 '기능 정의서'여야 합니다.

💰 Business: 작업 시작합니다.

## 📄 VibeFashion 시스템 에이전트 기능 정의서 (14 Agent Functional Definition)

**목표:** 패션 비즈니스 전반의 가치 사슬(Value Chain)을 자동화하고, 모든 데이터 흐름을 KPI 대시보드(Dashboard)로 통합하여 '데이터 기반 공급망 최적화 솔루션'의 기반을 마련한다.

| 에이전트 이름 | 주요 역할 및 기능 | 필요한 입력 데이터 (Input Data) | 산출물 (Output Deliverable) | 기대되는 KPI (Key Performance Indicator) |
| :--- | :--- | :--- | :--- | :--- |
| **1. 트렌드 수집기 (Trend Scraper)** | 글로벌/로컬 트렌드, 키워드, 소셜 버즈량 크롤링 및 분류. | 크롤링 대상 URL 목록 (인스타그램, 핀터레스트, 트렌드 리포트), 시간대/지역 설정. | 주간/월간 트렌드 키워드 리포트 (Heatmap 포함), 예상 트렌드 수명 주기 예측. | 트렌드 수집 빈도 (Daily/Weekly), 트렌드 적시성 (Lead Time) |
| **2. 시장 갭 분석가 (Gap Analyst)** | 트렌드와 현재 시장 상품군을 비교하여 미충족 니즈(Unmet Needs) 식별. | 트렌드 수집기 산출물, 경쟁사 상품 목록 (스크래핑 데이터), 자사 SKU 데이터. | 시장 갭(Gap) 보고서 (Top 3 기회 영역), 잠재적 카테고리 추천 및 근거. | 기회 발굴 건수 (Number of Gaps Identified), 시장 포화도 지수 (Saturation Index) |
| **3. 상품 기획가 (Product Designer)** | 갭 분석 결과를 바탕으로 구체적인 상품 콘셉트, 디자인 스케치, 소재 조합 정의. | 시장 갭 보고서, 트렌드 키워드, 목표 원가(Cost Target). | 상품 콘셉트 시트 (Concept Sheet), 디자인 스케치 (AI/Manual), 핵심 소재 리스트. | 디자인 완료율 (Completion Rate), 기획-출시 주기 단축률 (Cycle Time Reduction) |
| **4. 원가/소싱 관리자 (Sourcing Manager)** | 기획된 상품에 필요한 원자재 및 부자재의 글로벌 공급처 검색, 견적 비교, 리드타임 분석. | 상품 콘셉트 시트, 목표 원가, 필수 소재 리스트. | 공급망 옵션 비교표 (벤더 A/B/C), 최적 소싱 경로 및 예상 원가(COGS) 보고서. | 평균 원가 절감률 (Cost Reduction %), 소싱 리드타임 (Lead Time) |
| **5. 수요 예측/재고 최적화 (Demand Forecaster)** | 과거 판매 데이터, 계절성, 트렌드 수명 등을 고려하여 정확한 판매 수량 예측. | 과거 판매 이력 데이터 (POS/ERP), 트렌드 수집기 산출물, 프로모션 계획. | SKU별 판매 예측 수량 (Quantity), 안전 재고 수준 (Safety Stock Level), 발주 시점 권고. | 예측 정확도 (MAPE/WAPE), 재고 회전율 (Inventory Turnover Rate) |
| **6. 생산 및 SCM 오케스트레이터 (SCM Orchestrator)** | 확정된 발주량과 소싱 일정을 통합하여 생산 계획을 수립하고 병목 현상 최소화. | 수요 예측 보고서, 원가/소싱 보고서, 생산 설비 용량 정보. | 주간/월간 생산 로드맵 (Gantt Chart), 위험 경고 보고서 (Bottleneck Alert), 최적 발주 스케줄. | 재고 부족으로 인한 판매 손실액 (Lost Sales Value), 납기 준수율 (On-Time Delivery Rate) |
| **7. 가격 및 번들링 전략가 (Pricing Strategist)** | 원가, 경쟁사 가격, 수요 탄력성을 분석하여 최적의 판매 가격 및 번들 옵션 제시. | 원가/소싱 보고서, 경쟁사 ROI 분석, 수요 예측 보고서, 마케팅 목표 마진율. | 가격 정책 옵션 비교표 (A/B/C), 최적 번들링 조합 및 예상 수익(Margin) 시뮬레이션. | 평균 마진율 (Average Margin), 가격 민감도 지수 (Price Elasticity) |
| **8. 마케팅 콘텐츠 생성기 (Content Generator)** | 상품 콘셉트와 타깃 청중에 맞는 스토리텔링, 이미지, 카피라이팅 자동 생성. | 상품 콘셉트 시트, 타깃 페르소나, 최신 트렌드 키워드. | 제품별 마케팅 콘텐츠 패키지 (이미지 셋, SEO 최적화 카피, 숏폼 스크립트). | 콘텐츠 제작 속도 (Time to Content), 전환율 기여도 (Conversion Uplift) |
| **9. 이커머스 최적화 에이전트 (E-commerce Optimizer)** | 생성된 콘텐츠를 기반으로 상품 페이지 UX/UI 개선점 및 SEO 최적화 실행. | 마케팅 콘텐츠 패키지, 경쟁사 웹사이트 분석, 검색 엔진 최신 가이드라인. | 상품 상세 페이지 최적화 리포트 (A/B 테스트용), SEO 메타 태그 세트, UX/UI 개선 제안서. |
