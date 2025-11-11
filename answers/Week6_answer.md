## 문제 1

> **🧚쿠팡과 같은 쇼핑몰에서 회원이 상품을 결제하면, 장바구니에 담긴 상품 수량은 자동으로 차감되어야 합니다. 아래와 같은 테이블이 있다고 가정합니다.**

| **테이블명** | **컬럼명**                    | **설명**                  |
| ------------ | ----------------------------- | ------------------------- |
| Cart         | cart_id, product_id, quantity | 장바구니 정보 (수량 포함) |
| Product      | product_id, stock_quantity    | 상품 재고 수량            |

> **장바구니에 담긴 상품이 결제될 때, Product 테이블의 재고(stock_quantity)가 자동으로 감소하도록 트리거를 작성하세요.**
>
> > **(Cart의 quantity만큼 Product의 stock_quantity가 줄어듭니다.)**



~~~sql
CREATE TRIGGER trg_update_stock
AFTER DELETE ON Cart
FOR EACH ROW
BEGIN
    UPDATE Product
    SET stock_quantity = stock_quantity - OLD.quantity
    WHERE product_id = OLD.product_id;
END;
~~~
