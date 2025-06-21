# 오스트리아 호텔 데이터 세트

## 정보
이 데이터 세트에는 오스트리아 전역의 호텔에 대한 현실적인 데이터가 포함되어 있습니다.

* 이 데이터 세트는 개인 정보 보호를 유지하면서 변수 간의 현실적인 관계를 보장하기 위해 `generate_austrian_hotels_data.R` 스크립트를 사용하여 프로그래밍 방식으로 생성되었습니다.
  * 이 스크립트는 Claude AI, Sonnet 3.7, 2025-03-15에 의해 작성되었으며 Gabor가 2025-03-17에 검토하고 승인했습니다.
* 이 데이터 세트는 결합할 수 있는 여러 관련 테이블로 구성됩니다.
* 데이터 패턴은 일반적인 호텔 산업 지표를 기반으로 하지만 실제 호텔을 나타내지는 않습니다.

## 데이터 세트 개요

이 데이터 세트에는 점유율, 가격, 관광 통계 및 경제 지표에 대한 데이터가 있는 오스트리아 도시 전역의 호텔이 포함됩니다.

### 파일

모든 파일은 `data/raw/` 디렉터리에 있습니다.

  | 파일 | 설명 | 행 | 주요 열 |
  |------|-------------|------|------------|
  | `hotels.csv` | 기본 호텔 정보 | 200 | `hotel_id` (PK) |
  | `cities.csv` | 도시 정보 | 10 | `city` (PK) |
  | `monthly_occupancy.csv` | 월간 호텔 성과 지표 | ~3,800 | `hotel_id`, `month`, `year` |
  | `city_tourism.csv` | 도시별 월간 관광 통계 | 240 | `city`, `month`, `year` |
  | `economic_indicators.csv` | 월간 경제 지표 | 24 | `month`, `year` |
  | `reviews.csv` | 호텔 투숙객 리뷰 | ~1,700 | `review_id` (PK), `hotel_id` (FK) |
  | `amenities.csv` | 가능한 호텔 편의 시설 목록 | 10 | `amenity_id` (PK) |
  | `hotel_amenities.csv` | 호텔-편의 시설 관계 | ~1,000 | `hotel_id`, `amenity_id` |

  ## 스키마 세부 정보

  ### hotels.csv
  개별 호텔에 대한 정보입니다.

| 열 | 유형 | 설명 |
  |--------|------|-------------|
  | `hotel_id` | 정수 | 기본 키 |
  | `hotel_name` | 문자 | 호텔 이름 |
  | `city` | 문자 | 호텔이 위치한 도시 |
  | `star_rating` | 정수 | 호텔 품질 등급 (3-5성급) |
  | `rooms` | 정수 | 호텔 객실 수 |
  | `year_built` | 정수 | 호텔 건축 연도 |

  ### cities.csv
  오스트리아 도시에 대한 정보입니다.

| 열 | 유형 | 설명 |
  |--------|------|-------------|
  | `city` | 문자 | 도시 이름 (기본 키) |
  | `province` | 문자 | 오스트리아 주 |
  | `population` | 정수 | 도시 인구 |
  | `tourism_rank` | 정수 | 관광 인기 순위 (1 = 가장 높음) |

  ### monthly_occupancy.csv
  월간 호텔 성과 지표입니다.

| 열 | 유형 | 설명 |
  |--------|------|-------------|
  | `hotel_id` | 정수 | hotels.csv에 대한 외래 키 |
  | `month` | 정수 | 월 (1-12) |
  | `year` | 정수 | 연도 (2023-2024) |
  | `occupancy_rate` | 숫자 | 객실 점유율 (0.0-1.0) |
  | `avg_daily_rate` | 숫자 | 1박당 평균 가격 (EUR) |
  | `revenue_per_room` | 숫자 | 사용 가능한 객실당 수익 (RevPAR) |

  ### city_tourism.csv
  각 도시의 월간 관광 통계입니다.

| 열 | 유형 | 설명 |
  |--------|------|-------------|
  | `city` | 문자 | 도시 이름 |
  | `month` | 정수 | 월 (1-12) |
  | `year` | 정수 | 연도 (2023-2024) |
  | `tourist_arrivals` | 정수 | 관광객 도착 수 |
  | `event_days` | 정수 | 해당 월의 행사 일수 |
  | `avg_stay_length` | 숫자 | 평균 체류 기간 (일) |

  ### economic_indicators.csv
  오스트리아의 월간 경제 지표입니다.

| 열 | 유형 | 설명 |
  |--------|------|-------------|
  | `month` | 정수 | 월 (1-12) |
  | `year` | 정수 | 연도 (2023-2024) |
  | `inflation_rate` | 숫자 | 월간 인플레이션율 (십진수) |
  | `unemployment` | 숫자 | 실업률 (십진수) |
  | `consumer_confidence` | 숫자 | 소비자 신뢰 지수 |

  ### reviews.csv
  호텔 투숙객 리뷰입니다.

| 열 | 유형 | 설명 |
  |--------|------|-------------|
  | `review_id` | 정수 | 기본 키 |
  | `hotel_id` | 정수 | hotels.csv에 대한 외래 키 |
  | `rating` | 숫자 | 평점 (1.0-5.0) |
  | `review_date` | 날짜 | 리뷰 날짜 |

  ### amenities.csv
  가능한 호텔 편의 시설 목록입니다.

| 열 | 유형 | 설명 |
  |--------|------|-------------|
  | `amenity_id` | 정수 | 기본 키 |
  | `amenity_name` | 문자 | 편의 시설 이름 |

  ### hotel_amenities.csv
  호텔과 편의 시설 간의 다대다 관계입니다.

| 열 | 유형 | 설명 |
  |--------|------|-------------|
  | `hotel_id` | 정수 | hotels.csv에 대한 외래 키 |
  | `amenity_id` | 정수 | amenities.csv에 대한 외래 키 |
