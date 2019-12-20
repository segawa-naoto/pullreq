# 通常購入: 確定

## Action

| Action No. | Action名 | 概要 | 画面 | 遷移先 | 中継API | 
| --- | --- | --- | --- | --- | --- |
| A | 注文確定 | 通常購入カートを注文確定状態にする | 2 | own | [order.Cart/post_carts__cart_code___finalize_checkout](http://3.114.104.100/#/order.Cart/post_carts__cart_code___finalize_checkout) |


## 中継API

### A: 注文確定

| カート仮引当API名 | リンク |
| --- | --- |
| 注文確定API | [order.Cart/post_carts__cart_code___finalize_checkout](http://3.114.104.100/#/order.Cart/post_carts__cart_code___finalize_checkout) |  

#### Request

| 必須 | 物理名 | 型（桁） | 論理名(David) | 論理名（Prismatix） |
| ---| --- | --- | --- | --- |
| 〇 | cart_code(Excelなし) |  |  |  |
|  | checkout_timestamp(Excelなし) |  |  |  |

#### Response

| 必須 | 物理名 | 型（桁） | 論理名(David) | 論理名（Prismatix） |
| ---| --- | --- | --- | --- |
|  | (status_code) |  |  |  |