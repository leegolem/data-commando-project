# 관후의 개인 작업공간
H&M 거래 데이터를 기반으로 상위 20% 핵심고객과 하위 20% 고객의 구매 행동을 비교하고, 특히 온라인/오프라인 채널 이용 차이를 함께 분석해 기업이 집중할 채널/고객 전략 우선순위를 도출한다.

# 분석 테이블
1. customer_summary (고객 1명당 1줄)

transactions_clean에서 고객별로 계산:
total_revenue = 총구매액(가격 합)
num_purchases = 구매횟수(거래 건수)
aov = 객단가 = total_revenue / num_purchases
last_purchase_date = 마지막 구매일(최신 날짜)
recency_days = 전체 마지막날 - 마지막 구매일
segment = Top20 / Bottom20 / Others (기준: total_revenue)

2. customer_channel_summary (고객×채널 요약)

transactions_clean에서 고객×채널로 계산:
channel_revenue = 채널별 구매액(온라인/오프라인 각각)
channel_purchases = 채널별 구매횟수
channel_share = 채널 매출 비중 = channel_revenue / total_revenue
(customer_summary의 total_revenue를 customer_id로 붙여서 계산)

# customer_hm
컬럼명	컬럼 상세정보
customer_id	고객 id *****
FN	패션 뉴스 구독여부 ***** / 인사이트 도출용 / 
Active	커뮤니케이션 가능여부 ***** / 인사이트 도출용 /
club_member_status	회원 상태 (신규, 활성, 탈퇴)
fashion_news_frequency	패션 뉴스 알람 주기
age	나이

# transaction_hm
컬럼명	컬럼 상세정보
t_dat	구매일 *****
customer_id	고객 id *****
article_id	article id ***** /articles_hm랑 조인해서 “Top20이 뭘 사는지” 볼 때/
price	가격 *****
sales_channel_id	판매 채널 (1 : 오프라인, 2: 온라인) *****

# articles_hm
컬럼명	컬럼 상세정보 
article_id	article 아이디 *****
product_code	상품 코드
prod_name	상품 명
product_type_no	상품 종류 코드
product_type_name	상품 종류 명
product_group_name	제품군 *****
graphical_appearance_no	그래픽 정보 코드
graphical_appearance_name	그래픽 정보 - (예시) Solid
colour_group_code	상품 색상 코드
colour_group_name	상품 색상 명 - (예시) Light Beige
perceived_colour_value_id	명도 id
perceived_colour_value_name	명도 분류 - (예시) Dusty Light
perceived_colour_master_id	색상군 코드
perceived_colour_master_name	색상군 - (예시) Beige
department_no	소분류 코드
department_name	소분류 명 - (예시) Tights basic
index_code	중분류 코드
index_name	중분류 명 - (예시) Lingeries/Tights
index_group_no	타겟 그룹 코드
index_group_name	타겟 그룹 명 - (예시) Ladieswear
section_no	섹션 코드
section_name	섹션 명 - (예시) Womens Nightwear, Socks & Tigh
garment_group_no	대분류 코드 
garment_group_name	대분류 명 - (예시) Socks and Tights *****
detail_desc	제품 상세 설명