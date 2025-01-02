<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منعم AI</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-image: url('RR4.jpg');
            background-size: cover;
            background-position: center;
            color: #fff;
            text-align: center;
        }

        header {
            background: rgba(0, 0, 0, 0.7);
            padding: 10px;
        }

        header h1 {
            margin: 0;
            font-size: 2em;
        }

        main {
            padding: 20px;
        }

        .search-box {
            margin: 20px 0;
        }

        .search-box input {
            padding: 10px;
            width: 70%;
            border: none;
            border-radius: 5px;
        }

        .search-box button {
            padding: 10px;
            border: none;
            background-color: #007BFF;
            color: white;
            border-radius: 5px;
            cursor: pointer;
        }

        .api-button {
            margin: 20px 0;
            padding: 10px 20px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        footer {
            margin-top: 20px;
            padding: 10px;
            background: rgba(0, 0, 0, 0.7);
        }
    </style>
</head>
<body>
    <header>
        <h1>منعم AI</h1>
        <p>موقع ذكاء اصطناعي للمعلومات عن التسويق والمبيعات</p>
    </header>

    <main>
        <section>
            <h2>معلومات عن التسويق والمبيعات</h2>
            <p>
                التسويق هو عملية فهم احتياجات العملاء وتطوير استراتيجيات لتلبية هذه الاحتياجات. المبيعات تركز على تحويل هذه الاستراتيجيات إلى نتائج فعلية من خلال إتمام عمليات الشراء.
            </p>
        </section>

        <section class="search-box">
            <h2>البحث في الويب</h2>
            <input type="text" id="searchQuery" placeholder="أدخل كلمة للبحث...">
            <button onclick="searchWeb()">بحث</button>
        </section>

        <section>
            <h2>توليد الصور</h2>
            <button class="api-button" onclick="generateImage()">إنشاء صورة</button>
            <div id="imageResult"></div>
        </section>
    </main>

    <footer>
        <p>جميع الحقوق محفوظة © 2025 منعم AI</p>
    </footer>

    <script>
        function searchWeb() {
            const query = document.getElementById('searchQuery').value;
            if (query) {
                window.open(`https://www.google.com/search?q=${query}`, '_blank');
            } else {
                alert('يرجى إدخال كلمة للبحث.');
            }
        }

        async function generateImage() {
            try {
                const response = await fetch('https://api.example.com/generate-image', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({ prompt: 'صورة تسويقية مبتكرة' }),
                });

                if (response.ok) {
                    const data = await response.json();
                    const imageResult = document.getElementById('imageResult');
                    imageResult.innerHTML = `<img src="${data.imageUrl}" alt="Generated Image" style="max-width:100%;margin-top:10px;">`;
                } else {
                    alert('حدث خطأ أثناء توليد الصورة.');
                }
            } catch (error) {
                console.error(error);
                alert('فشل الاتصال بخادم التوليد.');
            }
        }
    </script>
</body>
</html>
