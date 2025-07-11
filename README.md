<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>완판 테스트</title>

  <!-- Firebase SDK -->
  <script src="https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/10.12.0/firebase-database.js"></script>

  <style>
    .item { border: 1px solid #ccc; padding: 10px; width: 200px; text-align: center; }
    .sold-out { color: red; font-weight: bold; display: none; }
  </style>
</head>
<body>

  <div class="item">
    <img src="orange.jpg" alt="오렌지" width="150"><br>
    오렌지 (900원)<br>
    <button onclick="toggleSoldOut('orange-status')">완판 처리</button>
    <div id="orange-status" class="sold-out">✅ 완판되었습니다</div>
  </div>

  <script>
    // 🔁 본인의 firebaseConfig로 교체하세요
    const firebaseConfig = {
      apiKey: "AIzaSyDWeV7Rgtus6gfCesNGx5Mm0s2UFoK9VsU",
      authDomain: "handongeats.firebaseapp.com",
      databaseURL: "https://handongeats-default-rtdb.firebaseio.com",
      projectId: "handongeats",
      storageBucket: "handongeats.appspot.com",
      messagingSenderId: "881457108225",
      appId: "1:881457108225:web:ea9687fc1a0872f8853700",
      measurementId: "G-RRHR296G2R"
    };

    // Firebase 초기화
    const app = firebase.initializeApp(firebaseConfig);
    const db = firebase.database();

    // 상태 토글 함수
    function toggleSoldOut(id) {
      const el = document.getElementById(id);
      const isSoldOut = el.style.display === "none";
      el.style.display = isSoldOut ? "block" : "none";
      db.ref("items/" + id).set(isSoldOut);
    }

    // 페이지 로드 시 상태 불러오기
    window.onload = function () {
      const id = "orange-status";
      db.ref("items/" + id).once("value").then((snapshot) => {
        if (snapshot.exists() && snapshot.val() === true) {
          document.getElementById(id).style.display = "block";
        }
      });
    };
  </script>
</body>
</html>

