# 通常購入: Step1 商品
|![画面](../../../images/regular_purchase_1_products.png)|  
|:-:|

## Action

| Action No. | Action名 | 概要 | 画面 | 遷移先 | 中継API | 
| --- | --- | --- | --- | --- | --- |
| A | 商品情報取得 | 商品コードから商品名と単価を取得する | 1 | own | [item.Sku/get_skus__sku_code_](http://3.114.104.100/#/item.Sku/get_skus__sku_code_) |
| B | カート作成・商品追加 | 追加するボタン1回目押下時、通常購入カートを作成し商品とその個数をカートに追加する | 1 | own | [order.Cart/post_carts](http://3.114.104.100/#/order.Cart/post_carts) |
| C | 商品追加・変更・削除 | 追加するボタン2回目以降押下時、商品コードと数量からカートに賞品を追加する | 2 | own | [order.Cart/put_carts__cart_code_](http://3.114.104.100/#/order.Cart/put_carts__cart_code_) |
| D | 配送料・カート金額・還元ポイントを取得 | カートに関する情報を取得 | 2 | own | [order.Cart/post_carts__cart_code___calculate](http://3.114.104.100/#/order.Cart/post_carts__cart_code___calculate) |
| E | ページ遷移（Step2） | ページ遷移（Step2） | 3 | 通常購入: Step2 配送 | なし |

## 中継API
### A: 商品情報取得

| API名 | リンク |
| --- | --- |
| 注文データ取得API | [item.Sku/get_skus__sku_code_](http://3.114.104.100/#/item.Sku/get_skus__sku_code_) |  

#### Request

| 必須 | 物理名 | 型（桁） | 論理名(David) | 論理名（Prismatix） |
| --- | --- | --- | --- | --- |
| 〇 | sku_code | string | SKUコード | 同左 |

#### Response

| 必須 | 物理名 | 型（桁） | 論理名(David) | 論理名（Prismatix） |
| --- | --- | --- | --- | --- |
| 〇 | sku_name | string | 社内登録名称（愛称） | SKU名 |
|  | base_price_ex_vat(Excelの方がbase_price_ex_batとなってました。) | number | 基本価格(税抜) | 同左 |
|  | base_price_in_vat(Excelの方がbase_price_in_batとなってました。) | number | 基本価格(税込) | 同左 |

### B: カート作成・商品追加

| API名 | リンク |
| --- | --- |
| カート作成API | [order.Cart/post_carts](http://3.114.104.100/#/order.Cart/post_carts) |  

#### Request

| 必須 | 物理名 | 型（桁） | 論理名(David) | 論理名（Prismatix） |
| --- | --- | --- | --- | --- |
| 〇 | cart_code(Excelなし) |  |  |  |
| 〇 | visitor_code | string | 訪問者コード | 同左 |
| 〇 | application_code(Excelなし) |  |  |  |
| 〇 | order_type(Excelなし) |  |  |  |
| 〇 | payment_executor(Excelなし) |  |  |  |
| 〇 | auto_allocation_flag(Excelなし) |  |  |  |
| 〇 | currency_code | string | 通貨コード (ISO 4217 に準拠) | 同左 |
| 〇 | store_code | string | 対応店舗 | 同左 |
| 〇 | attributes[sales_channel_type] (Excelなし) |  |  |  |
| 〇 | attributes[sales_channel_code] (Excelなし) |  |  |  |
| 〇 | attributes[sales_channel_name] (Excelなし) |  |  |  |
| 〇 | sku_code | string | SKUコード | 同左 |
| 〇 | quantity(Excelなし) |  |  |  |
|  | sku_name | string | 社内登録名称（愛称） | SKU名 |
|  | customer_code | string | 会員コード | 同左 |

#### Response

| 必須 | 物理名 | 型（桁） | 論理名(David) | 論理名（Prismatix） |
| --- | --- | --- | --- | --- |
| 〇 | cart_code(Excelなし) |  |  |  |

### C: 商品追加・変更・削除

| API名 | リンク |
| --- | --- |
| 商品操作API | [order.Cart/put_carts__cart_code_](http://3.114.104.100/#/order.Cart/put_carts__cart_code_) |  

#### Request

| 必須 | 物理名 | 型（桁） | 論理名(David) | 論理名（Prismatix） |
| ---| --- | --- | --- | --- |
| 〇 | cart_code(Excelなし) |  |  |  |
| 〇 | entry_index(Excelなし) |  |  |  |
| 〇 | sku_code | string | SKUコード | 同左 |
| 〇 | store_code | string | 対応店舗 | 同左 |
| 〇 | quantity(Excelなし) |  |  |  |

#### Response

| 必須 | 物理名 | 型（桁） | 論理名(David) | 論理名（Prismatix） |
| --- | --- | --- | --- | --- |
|  | (status_code) |  |  |  |
|  | sku_entries[entry_index] (Excelなし) |  |  |  |
|  | sku_entries[sku_code] | string | SKUコード | 同左 |
|  | sku_entries[sku_name] | string | 社内登録名称（愛称） | SKU名 |
|  | sku_entries[quantity] (Excelなし) |  |  |  |
|  | sku_entries[price_ex_vat] | decimal | 税抜売価 | 同左 |
|  | sku_entries[price_in_vat] | decimal | 税込売価 | 同左 |


### D: 配送料・カート金額・還元ポイントを取得

| API名 | リンク |
| --- | --- |
| カート情報取得API | [order.Cart/post_carts__cart_code___calculate](http://3.114.104.100/#/order.Cart/post_carts__cart_code___calculate) |  

#### Request

| 必須 | 物理名 | 型（桁） | 論理名(David) | 論理名（Prismatix） |
| --- | --- | --- | --- | --- |
|  | apply_discount_flag(Excelなし) |  |  |  |
|  | amount_fields_for_coupon_applicable_condition(Excelなし) |  |  |  |

#### Response

| 必須 | 物理名 | 型（桁） | 論理名(David) | 論理名（Prismatix） |
| --- | --- | --- | --- | --- |
| 〇 | order_vat_details[tax_code] | string | 税コード | 同左 |
| 〇 | order_vat_details[tax_name] | string | 税名 | 同左 |
| 〇 | order_vat_details[tax_rate] | number | 税率 | 税率 (0.0<=、1.0で100%) |
| 〇 | order_vat_details[sku_in_vat] (Excelなし) |  |  |  |
| 〇 | order_vat_details[addon_service_in_vat] (Excelなし) |  |  |  |
| 〇 | order_vat_details[discount_in_vat] (Excelなし) |  |  |  |
| 〇 | order_vat_details[point_in_vat] (Excelなし) |  |  |  |
| 〇 | order_vat_details[adjustment_in_vat] (Excelなし) |  |  |  |
| 〇 | order_vat_details[delivery_fee_in_vat] (Excelなし) |  |  |  |
| 〇 | order_vat_details[subtotal_ex_vat] (Excelなし) |  |  |  |
| 〇 | order_vat_details[subtotal_in_vat] (Excelなし) |  |  |  |
|  | cart_code(Excelなし) |  |  |  |
|  | point Variation Value(Excelなし) |  |  |  |

## 質問事項
| Action NO.| Request or Response | 質問内容 |
| ---| --- | --- |
| A | Request | currency_code はどのExcelファイルを参照すれば良いのか(表には価格リソースのものを記入)
| A | Request | store_code はどのExcelファイルを参照すれば良いのか(表には単品リソース20191202-01のものを記入)
| A | Request | customer_code はどのExcelファイルを参照すれば良いのか(表には会員リソース_20191102-01のものを記入)
| C | Request | store_code はどのExcelファイルを参照すれば良いのか(表には単品リソース20191202-01のものを記入)
| C | Response | sku_entries[sku_code] はどのExcelファイルを参照すれば良いのか(表には単品リソース20191202-01のものを記入したが恐らく参照するExcelファイルが違い、尚且つ参照するべきExcelファイルが存在しない)
| C | Response | sku_entries[sku_name] はどのExcelファイルを参照すれば良いのか(表には単品リソース20191202-01のものを記入したが恐らく参照するExcelファイルが違い、尚且つ参照するべきExcelファイルが存在しない)
| C | Response | sku_entries[price_ex_vat] はどのExcelファイルを参照すれば良いのか(表には価格リソース20191126-01のものを記入したが恐らく参照するExcelファイルが違い、尚且つ参照するべきExcelファイルが存在しない)
| C | Response | sku_entries[price_in_vat] はどのExcelファイルを参照すれば良いのか(表には価格リソース20191126-01のものを記入したが恐らく参照するExcelファイルが違い、尚且つ参照するべきExcelファイルが存在しない)
| D | Response | order_vat_details[tax_code] はどのExcelファイルを参照すれば良いのか(表には税リソースのものを記入したが恐らく参照するExcelファイルが違い、尚且つ参照するべきExcelファイルが存在しない)
| D | Response | order_vat_details[tax_name] はどのExcelファイルを参照すれば良いのか(表には税リソースのものを記入したが恐らく参照するExcelファイルが違い、尚且つ参照するべきExcelファイルが存在しない)
| D | Response | order_vat_details[tax_rate] はどのExcelファイルを参照すれば良いのか(表には税リソースのものを記入したが恐らく参照するExcelファイルが違い、尚且つ参照するべきExcelファイルが存在しない)
| D | Response | なぜ point Variation Value だけスネークケースではないのか