<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Truy Cập Cloud Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f9;
        }
        .container {
            text-align: center;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            background-color: #fff;
        }
        input[type="text"] {
            padding: 10px;
            width: 200px;
            margin-bottom: 10px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }
        button {
            padding: 10px 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .message {
            margin-top: 10px;
            color: red;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Nhập Key để Truy Cập</h2>
        <input type="text" id="keyInput" placeholder="Nhập key tại đây">
        <button onclick="validateKey()">Xác nhận</button>
        <p id="errorMessage" class="message"></p>
    </div>

    <script>
        const correctKey = "key_12345";  // Thay "key_12345https://github.com/Noathecker/c-cc/blob/main/README.mdhttps://github.com/Noathecker/c-cc/blob/main/README.md" bằng key đúng của bạn

        function validateKey() {
            const enteredKey = document.getElementById('keyInput').value.trim();
            const errorMessage = document.getElementById('errorMessage');

            // Kiểm tra nếu key đã được nhập đúng trong 24 giờ
            const storedKey = localStorage.getItem('accessKey');
            const storedTime = localStorage.getItem('accessTime');
            const currentTime = new Date().getTime();

            if (storedKey && storedTime) {
                // Kiểm tra nếu key vẫn còn hiệu lực trong 24 giờ
                if (currentTime - storedTime < 24 * 60 * 60 * 1000) {
                    window.location.href = "https://sites.google.com/view/cloudgamefree";
                    return;
                } else {
                    // Hết thời gian lưu key
                    localStorage.removeItem('accessKey');
                    localStorage.removeItem('accessTime');
                }
            }

            // Kiểm tra key nhập vào
            if (enteredKey === correctKey) {
                // Lưu key và thời gian vào localStorage
                localStorage.setItem('accessKey', enteredKey);
                localStorage.setItem('accessTime', currentTime);
                window.location.href = "https://sites.google.com/view/cloudgamefree";
            } else {
                // Hiển thị thông báo lỗi
                errorMessage.textContent = "Key không đúng. Vui lòng thử lại.";
            }
        }
    </script>
</body>
</html>
