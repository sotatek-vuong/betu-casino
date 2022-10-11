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
[Sequence Diagram](https://mermaidjs.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoic2VxdWVuY2VEaWFncmFtXG4gICAgcGFydGljaXBhbnQgUCBhcyBQbGF5ZXJcbiAgICBwYXJ0aWNpcGFudCBDIGFzIENhc2lub1xuICAgIHBhcnRpY2lwYW50IEEgYXMgQWdncmVnYXRvclxuICAgIHBhcnRpY2lwYW50IEcgYXMgR2FtZSBQcm92aWRlclxuXG4gICAgTm90ZSBvdmVyIEMsQTogT3BlbiBnYW1lIGZsb3dcblxuICAgIFAgLT4-KyBDOiBPcGVuIEdhbWVcbiAgICBDIC0-PisgQTogQ3JlYXRlIFNlc3Npb25cbiAgICBBIC0-PisgRzogQ3JlYXRlIFNlc3Npb25cbiAgICBHIC0tPj4tIEE6IGdhbWVfdXJsIGFuZCBvcHRpb25zXG4gICAgQSAtLT4-LSBDOiBnYW1lX3VybCBhbmQgb3B0aW9uc1xuICAgIEMgLS0-Pi0gUDogUmVkaXJlY3QgdG8gZ2FtZV91cmxcblxuICAgIFAgLT4-KyBHOiBPcGVuIGdhbWVfdXJsXG4gICAgRyAtPj4rIEE6IEdldCBCYWxhbmNlXG4gICAgQSAtPj4rIEM6IEdldCBCYWxhbmNlXG4gICAgQyAtLT4-LSBBOiBSZXR1cm4gQmFsYW5jZVxuICAgIEEgLS0-Pi0gRzogUmV0dXJuIEJhbGFuY2VcbiAgICBHIC0tPj4tIFA6IFNob3cgZ2FtZSBhbmQgcmVhZHkgdG8gcGxheVxuXG4gICAgTm90ZSBvdmVyIEMsQTogR2FtZSBwcm9jZXNzXG5cbiAgICBsb29wIEVhY2ggcm91bmRcbiAgICBQIC0-PisgRzogUGxheWVyIG1ha2VzIGJldFxuICAgIEcgLT4-KyBBOiBTZW5kIGJldFxuICAgIEEgLT4-KyBDOiBTZW5kIGJldFxuICAgIG5vdGUgbGVmdCBvZiBDOiBEZWNyZWFzZSBiYWxhbmNlXG4gICAgQyAtLT4-LSBBOiBcbiAgICBBIC0tPj4tIEc6IFxuICAgIG9wdCBJZiBwbGF5ZXIgd2luc1xuICAgIEcgLT4-KyBBOiBTZW5kIHdpblxuICAgIEEgLT4-KyBDOiBTZW5kIHdpblxuICAgIG5vdGUgbGVmdCBvZiBDOiBJbmNyZWFzZSBiYWxhbmNlXG4gICAgQyAtLT4-LSBBOiBcbiAgICBBIC0tPj4tIEc6IFxuICAgIGVuZCBcbiAgICBHIC0tPj4tIFA6IERpc3BsYXkgZ2FtZSBzdGF0ZSBhZnRlciBiZXQgYW5kIHdpblxuICAgIGVuZFxuXG4gICAgTm90ZSBvdmVyIEMsQTogSGFuZGxlIGZhaWx1cmVzXG5cbiAgICBQIC0-PisgRzogUGxheWVyIG1ha2VzIGJldFxuICAgIEcgLT4-KyBBOiBTZW5kIGJldFxuICAgIEEgLT4-KyBDOiBTZW5kIGJldFxuICAgIG5vdGUgbGVmdCBvZiBDOiBEZWNyZWFzZSBiYWxhbmNlXG4gICAgQyAtLXggRzogTm8gcmVzcG9uc2VcbiAgICBkZWFjdGl2YXRlIENcbiAgICBkZWFjdGl2YXRlIEFcbiAgICBHIC0tPj4tIFA6IFNob3cgZXJyb3IgdG8gcGxheWVyXG4gICAgbG9vcCBTZW5kIHJvbGxiYWNrIHdoaWxlIG5vIHJlc3VsdFxuICAgIGFjdGl2YXRlIEdcbiAgICBHIC0-PisgQTogUm9sbGJhY2sgYmV0XG4gICAgQSAtPj4rIEM6IFJvbGxiYWNrIGJldFxuICAgIG5vdGUgbGVmdCBvZiBDOiBDb3JyZWN0IGJhbGFuY2VcbiAgICBDIC0tPj4tIEE6IFxuICAgIEEgLS0-Pi0gRzogXG4gICAgZGVhY3RpdmF0ZSBHXG4gICAgZW5kXG4iLCJtZXJtYWlkIjp7InRoZW1lIjoiZGVmYXVsdCJ9fQ)


- `GCP` là nơi cung cấp **UI** cho `FE` để hiện thị, xử lý bet từ FE, trả về kết quả win/lost/rollback cho `Aggregator`
- `Aggregator` là trung gian tổng hợp lại các game từ `GCP`, webhook với BE 
- `FE` là nơi hiện thị UI (iframe, canvas,...) của `GCP`, auth với `BE`
- `BE` là nơi tiếp nhận các api bets từ `Aggregator`, trả về balance cho `Aggregator`


Freespins: 
- 1 user sẽ đc các round chơi miễn phí
- BE có thể create, cancel freespin cho 1 user.
- BE có thể quy ước số lượng, ngày hiệu lực,... (check API `/freespins/issue`)
- game hỗ trợ freespin sẽ có field `has_freespins` === true

Jackpot: 
- mỗi bet trích ra 1 phần `jackpot_contribution` vào pot
- game hỗ trợ freespin sẽ có field has_jackpot` === true
- get thông tin về các jackpot thông qua `Jackpot Feed`
NOTE: f casino issues freespins in multiple games a player will have freespins_quantity free games in total NOT freespins_quantity in each game.


- game provider - https://docs.softswiss.com/pages/viewpage.action?pageId=31263519
- aggregator - https://docs.softswiss.com/display/CASINOPUB/Client%27s+manual+for+creating+a+support+ticket
- game list - https://docs.softswiss.com/pages/viewpage.action?pageId=22184165
- balance/decimals - https://docs.google.com/spreadsheets/d/1lxe826OpM18IuepH8uqizDA2cWKLDPcHedfamzjsJg8/edit?usp=sharing

## Questions?
game:
- normal game?
- multiple game?
- ko multiple game?
game list is fixed?

