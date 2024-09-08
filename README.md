<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ABAAS BW </title>
    <style>
        body {
            font-family: Arial, sans-serif;
            direction: rtl;
            text-align: right;
        }
        .result {
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <h1>Bw </h1>
    <label for="letterInput">أدخل حرفاً:</label>
    <input type="text" id="letterInput" maxlength="1" oninput="showResults()">
    
    <div class="result">
        <h3>نتائج:</h3>
        <p><strong>اسم إنسان:</strong> <span id="person"></span></p>
        <p><strong>حيوان:</strong> <span id="animal"></span></p>
        <p><strong>نبات:</strong> <span id="plant"></span></p>
        <p><strong>جماد:</strong> <span id="object"></span></p>
        <p><strong>دولة:</strong> <span id="country"></span></p>
    </div>

    <script>
        const data = {
            'ض': { person: 'ضحى', animal: 'ضبع', plant: 'ضمران', object: 'ضوء', country: 'ضومينيكا' },
            'ص': { person: 'صالح', animal: 'صقر', plant: 'صبار', object: 'صندوق', country: 'صربيا' },
            'ث': { person: 'ثامر', animal: 'ثعلب', plant: 'ثوم', object: 'ثوب', country: 'ثيساليا' },
            'ق': { person: 'قاسم', animal: 'قرد', plant: 'قرنفل', object: 'قلم', country: 'قطر' },
            'ف': { person: 'فاطمة', animal: 'فيل', plant: 'فراولة', object: 'فرن', country: 'فنزويلا' },
            'غ': { person: 'غسان', animal: 'غزال', plant: 'غار', object: 'غطاء', country: 'غانا' },
            'ع': { person: 'علي', animal: 'عصفور', plant: 'عنب', object: 'عجلة', country: 'عمان' },
            'ه': { person: 'هالة', animal: 'هدهد', plant: 'هليون', object: 'هاتف', country: 'هولندا' },
            'خ': { person: 'خالد', animal: 'خروف', plant: 'خيار', object: 'خاتم', country: 'خنكاريا' },
            'ح': { person: 'حسين', animal: 'حصان', plant: 'حبق', object: 'حبل', country: 'حوران' },
            'ج': { person: 'جمال', animal: 'جمل', plant: 'جرجير', object: 'جرس', country: 'جامايكا' },
            'ش': { person: 'شادي', animal: 'شمبانزي', plant: 'شعير', object: 'شمعة', country: 'شام' },
            'س': { person: 'سعاد', animal: 'سنجاب', plant: 'سنط', object: 'سرير', country: 'سويسرا' },
            'ي': { person: 'يحيى', animal: 'يمامة', plant: 'ياسمين', object: 'يد', country: 'يابان' },
            'ب': { person: 'بدر', animal: 'بطة', plant: 'بقدونس', object: 'بندقية', country: 'بلجيكا' },
            'ل': { person: 'ليلى', animal: 'لبؤة', plant: 'ليمون', object: 'لعبة', country: 'لبنان' },
            'ا': { person: 'أحمد', animal: 'أسد', plant: 'أرز', object: 'إبرة', country: 'ألمانيا' },
            'ت': { person: 'تامر', animal: 'تمساح', plant: 'تمر', object: 'تلفاز', country: 'تركيا' },
            'ن': { person: 'نبيل', animal: 'نسر', plant: 'نعناع', object: 'نظارة', country: 'نرويج' },
            'م': { person: 'مروان', animal: 'ماعز', plant: 'مشمش', object: 'مقعد', country: 'مصر' },
            'ك': { person: 'كمال', animal: 'كلب', plant: 'كيوي', object: 'كتاب', country: 'كندا' },
            'ط': { person: 'طارق', animal: 'طاووس', plant: 'طرخون', object: 'طاولة', country: 'طاجيكستان' },
            'ذ': { person: 'ذيب', animal: 'ذئب', plant: 'ذرة', object: 'ذهب', country: 'ذمار' },
            'ء': { person: 'آمنة', animal: '---', plant: '---', object: '---', country: '---' },
            'ؤ': { person: '---', animal: '---', plant: '---', object: '---', country: '---' },
            'ر': { person: 'رشيد', animal: 'رنة', plant: 'روز', object: 'رمح', country: 'روسيا' },
            'ى': { person: 'ياسين', animal: '---', plant: '---', object: '---', country: '---' },
            'ة': { person: '---', animal: '---', plant: '---', object: '---', country: '---' },
            'و': { person: 'وليد', animal: 'وز', plant: 'ورد', object: 'ورقة', country: 'ويلز' },
            'ز': { person: 'زكريا', animal: 'زرافة', plant: 'زعتر', object: 'زر', country: 'زامبيا' },
            'ظ': { person: 'ظاهر', animal: 'ظبي', plant: 'ظفرة', object: 'ظرف', country: 'ظفار' },
            'د': { person: 'داليا', animal: 'دلفين', plant: 'دوار الشمس', object: 'درع', country: 'دنمارك' }
        };

        function showResults() {
            const letter = document.getElementById('letterInput').value;
            const result = data[letter];

            if (result) {
                document.getElementById('person').textContent = result.person;
                document.getElementById('animal').textContent = result.animal;
                document.getElementById('plant').textContent = result.plant;
                document.getElementById('object').textContent = result.object;
                document.getElementById('country').textContent = result.country;
            } else {
                document.getElementById('person').textContent = '';
                document.getElementById('animal').textContent = '';
                document.getElementById('plant').textContent = '';
                document.getElementById('object').textContent = '';
                document.getElementById('country').textContent = '';
            }
        }
    </script>
</body>
</html>
