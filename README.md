<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>음식 주문 폼</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            padding: 20px;
            max-width: 500px;
            margin: auto;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        .menu-section {
            background-color: #fff;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin: 8px 0;
            font-size: 16px;
        }
        .total {
            font-size: 20px;
            font-weight: bold;
            color: #d9534f;
            text-align: center;
        }
        button {
            display: block;
            width: 100%;
            padding: 10px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>

<h1>🍗 음식 주문 폼 🍺</h1>

<div class="menu-section">
    <h2>📋 메인 메뉴</h2>
    <label>
        <input type="checkbox" id="mainDish" checked disabled>
        닭도리탕 - 26,000원
    </label>
</div>

<div class="menu-section">
    <h2>🍜 추가 음식</h2>
    <label><input type="checkbox" class="addon" data-price="3000"> 라면 - 3,000원</label>
    <label><input type="checkbox" class="addon" data-price="4000"> 우동 - 4,000원</label>
    <label><input type="checkbox" class="addon" data-price="5000"> 칼국수 - 5,000원</label>
</div>

<div class="menu-section">
    <h2>🍺 술</h2>
    <label><input type="checkbox" class="addon" data-price="4000"> 카스 - 4,000원</label>
    <label><input type="checkbox" class="addon" data-price="5000"> 진로 - 5,000원</label>
</div>

<div class="total">총 금액: 26,000원</div>

<button onclick="submitOrder()">주문하기</button>

<script>
    const basePrice = 26000; // 닭도리탕 기본 가격
    const addons = document.querySelectorAll('.addon');
    const totalDisplay = document.querySelector('.total');

    addons.forEach(addon => {
        addon.addEventListener('change', updateTotal);
    });

    function updateTotal() {
        let total = basePrice;
        addons.forEach(addon => {
            if (addon.checked) {
                total += parseInt(addon.dataset.price);
            }
        });
        totalDisplay.textContent = `총 금액: ${total.toLocaleString()}원`;
    }

    function submitOrder() {
        let orderDetails = '주문 내역:\n- 닭도리탕 (26,000원)';
        addons.forEach(addon => {
            if (addon.checked) {
                orderDetails += `\n- ${addon.parentElement.textContent.trim()}`;
            }
        });
        orderDetails += `\n\n${totalDisplay.textContent}`;
        alert(orderDetails);
    }
</script>

</body>
</html>
