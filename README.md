# Assignment1
### 붉은 달의 성채 게임 저장 서버 구현

게임 진행 상황을 저장하고 불러올 수 있는 Spring Boot 기반 게임 저장 서버입니다.

### API 명세

| Method | URL | 기능 |
|---|---|---|
| POST | `/games` | 새 게임 생성 |
| GET | `/games` | 저장된 게임 목록 조회 |
| GET | `/games/{gameId}` | 게임 상세 조회 |
| PUT | `/games/{gameId}/progress` | 게임 진행 상황 및 덱 저장 |
| PATCH | `/games/{gameId}` | 플레이어 이름 변경 |
| DELETE | `/games/{gameId}` | 게임 삭제 |

### ERD

games  1  ──────  N  run_cards

- `games.id` (PK) ↔ `run_cards.game_id` (FK)
- 하나의 게임은 여러 개의 카드를 가질 수 있습니다.

### games

| Column | 설명 |
|---|---|
| id | 게임 ID (PK) |
| player_name | 플레이어 이름 |
| current_hp | 현재 HP |
| current_floor | 현재 층 |
| phase | 게임 진행 단계 |
| status | 게임 상태 |

### run_cards

| Column | 설명 |
|---|---|
| id | 카드 ID (PK) |
| game_id | 게임 ID (FK) |
| card_type | 카드 타입 |
| acquired_floor | 카드를 획득한 층 |