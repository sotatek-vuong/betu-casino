# betu-casino

## Configuration

### `.env`
```
GCP_URL=https://casino.int.a8r.games
SCRIPT_URL={GCP_URL}/public/sg.js
WALLET_URL=https://api.staging.betu.io/api/v3/casino/softswiss/event/development
AUTH_TOKEN=z0mgzk2s3z6s95oa
CASINO_ID=betu
```

### Postman 
https://www.getpostman.com/collections/75d469e263f69b11bbd8

### Docs
- [softswiss](https://docs.softswiss.com/display/GA/Universal+Game+Content+API) 


### Flows
Sẽ có 4 actor chính: `FE`, `BE`, `GCP - (Game Content Provider)`, `Aggregator`.
- `GCP` là nơi cung cấp **UI** cho `FE` để hiện thị, xử lý bet từ FE, trả về kết quả win/lost/rollback cho `Aggregator`
- `Aggregator` là trung gian tổng hợp lại các game từ `GCP`, webhook với BE 
- `FE` là nơi hiện thị UI (iframe, canvas,...) của `GCP`, auth với `BE`
- `BE` là nơi tiếp nhận các api bets từ `Aggregator`, trả về balance cho `Aggregator`

