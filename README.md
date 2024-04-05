<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <title>Form to Google Sheets via Sheety</title>
</head>
<body>
    <form id="myForm">
        Ad: <input type="text" name="firstName" id="firstName">
        Soyad: <input type="text" name="lastName" id="lastName">
        <button type="button" onclick="submitToGoogleSheets()">Gönder</button>
    </form>

    <script>
        function submitToGoogleSheets() {
            var firstName = document.getElementById('firstName').value;
            var lastName = document.getElementById('lastName').value;

            var url = 'https://api.sheety.co/1d4b634456d1fc06eb77c0174190ca78/erkan/sayfa1';

            fetch(url, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': 'Bearer 97e79e05ba47eaf676a2222a18f6cdf0811a33f2'
                },
                body: JSON.stringify({ sayfa1: { Ad: firstName, Soyad: lastName } }) // 'sayfa1' Sheety'deki sayfanızın adıyla eşleşmeli
            })
            .then(response => response.json())
            .then(data => {
                console.log('Success:', data);
                alert('Veriler başarıyla gönderildi!');
            })
            .catch((error) => {
                console.error('Error:', error);
                alert('Veri gönderme hatası!');
            });
        }
    </script>
</body>
</html>
