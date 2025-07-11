<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>학생식당</title>
  <style>
    h5 { color: #1368BD; }

    .item {
      flex: 0 0 calc(20% - 40px);
      box-sizing: border-box;
      color: #000;
      text-align: center;
      font-family: Pretendard;
      font-size: 24px;
      font-weight: 600;
      position: relative;
      border-radius: 10px;
      border: 1px solid #1368BD;
      background: #FCFDFF;
      padding: 10px;
      height: 270px;
      width: 200px;
    }

    #menu {
      display: flex;
      flex-wrap: wrap;
      gap: 40px;
      margin: 40px;
      justify-content: flex-start;
    }

    img {
      width: 130px;
      height: 130px;
      border-radius: 10px;
    }

    p { font-size: small; }

    header {
      width: 100%;
      background-color: #fff;
      padding: 20px 40px;
      border-bottom: 1px solid #ccc;
    }

    .header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      max-width: 1280px;
      margin: 0 auto;
    }

    header img {
      height: 60px;
      object-fit: contain;
    }

    .category-boxes {
      display: flex;
      gap: 12px;
    }

    .category {
      padding: 8px 16px;
      border: 2px solid #1368BD;
      border-radius: 12px;
      background-color: #FCFDFF;
      font-family: Pretendard;
      font-size: 16px;
      font-weight: 600;
      color: #1368BD;
      white-space: nowrap;
      text-align: center;
    }

    #blue {
      background-color: #1368BD;
    }

    #blue > a {
      text-decoration: none;
      color: white;
    }

    #nonblue > a {
      text-decoration: none;
      color: #1368BD;
    }

    nav {
      width: 100%;
      height: 54px;
      display: flex;
      padding: 5px;
      font-family: Pretendard;
      font-size: 22px;
      font-weight: 500;
      border-radius: 10px;
    }

    nav a {
      flex: 1;
      border: 1px solid black;
      border-radius: 10px;
      text-align: center;
      text-decoration: none;
      color: #000;
      background-color: #FCFDFF;
      font-size: 20px;
      transition: 0.2s;
    }

    footer {
      width: 100%;
      height: 300px;
      background-color: #F2F4F7;
      color: #1368BD;
    }
  </style>
 <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-app.js"></script>
<script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-database.js"></script>

<script>
const firebaseConfig = {
  apiKey: "AIzaSyCtndOk6P4J9r37qil6wqHGaLiEeTzEU6E",
  authDomain: "handong-eats.firebaseapp.com",
  databaseURL: "https://handong-eats-default-rtdb.asia-southeast1.firebasedatabase.app",
  projectId: "handong-eats",
  storageBucket: "handong-eats.firebasestorage.app",
  messagingSenderId: "418250431277",
  appId: "1:418250431277:web:0a8215e6118788ca1591a4"
};
firebase.initializeApp(firebaseConfig);
    const database = firebase.database();
  </script>
</head>
<body>

<header>
  <div class="header">
    <img src="logo_BLUE.svg" style="width:175px;">
    <div class="category-boxes">
      <div id="blue" class="category"><a href="#">#식당</a></div>
      <div id="nonblue" class="category"><a href="#">#카페</a></div>
      <div id="nonblue" class="category"><a href="#">#매점*편의점</a></div>
    </div>
  </div>
</header>

<nav>
  <a href="cafeteria.html" style="background-color:#000; color:white">편의점</a>
  <a href="moms-kitchen.html">매점</a>
</nav>

<h5>영업시간= 주중-11:00~19:30 / 주말=14:00~21:00</h5>

<div id="menu">
  <div class="item">
    <img src="banana.jpeg" alt="바나나">
    <p>바나나</p>
    <p>600원</p>
    <button onclick="toggleSoldOut('banana-status')">완판 처리</button>
    <div id="banana-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="bul.jpeg" alt="비비고 불고기비빔밥">
    <p>비비고 불고기비빔밥</p>
    <p>3,180원</p>
    <button onclick="toggleSoldOut('bul-status')">완판 처리</button>
    <div id="bul-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="buldak.jpeg" alt="불닭볶음면">
    <p>불닭볶음면</p>
    <p>1,300원</p>
    <button onclick="toggleSoldOut('buldak-status')">완판 처리</button>
    <div id="buldak-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="dak.jpeg" alt="숯불향 닭강정">
    <p>숯불향 닭강정</p>
    <p>3,100원</p>
    <button onclick="toggleSoldOut('dak-status')">완판 처리</button>
    <div id="dak-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="dakbok.jpeg" alt="비비고 닭가슴살 볶음밥">
    <p>비비고 닭가슴살 볶음밥</p>
    <p>6,350원</p>
    <button onclick="toggleSoldOut('dakbok-status')">완판 처리</button>
    <div id="dakbok-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="egg.jpeg" alt="날계란">
    <p>날계란</p>
    <p>300원</p>
    <button onclick="toggleSoldOut('egg-status')">완판 처리</button>
    <div id="egg-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="fruit.jpeg" alt="과일컵">
    <p>과일컵</p>
    <p>2,900원</p>
    <button onclick="toggleSoldOut('fruit-status')">완판 처리</button>
    <div id="fruit-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="ggmandoo.jpeg" alt="고기포자만두">
    <p>고기포자만두</p>
    <p>1,000원</p>
    <button onclick="toggleSoldOut('ggmandoo-status')">완판 처리</button>
    <div id="ggmandoo-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="gimchi.jpeg" alt="스팸김치볶음밥">
    <p>스팸김치볶음밥</p>
    <p>3,400원</p>
    <button onclick="toggleSoldOut('gimchi-status')">완판 처리</button>
    <div id="gimchi-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="gimchiman.jpeg" alt="김치포자만두">
    <p>김치포자만두</p>
    <p>1,000원</p>
    <button onclick="toggleSoldOut('gimchiman-status')">완판 처리</button>
    <div id="gimchiman-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="gor.jpeg" alt="김치포자만두">
    <p>고메고르곤졸라 피자</p>
    <p>6,980원</p>
    <button onclick="toggleSoldOut('gor-status')">완판 처리</button>
    <div id="gor-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="jadoo.jpeg" alt="김치포자만두">
    <p>자두 5개</p>
    <p>2,000원</p>
    <button onclick="toggleSoldOut('jadoo-status')">완판 처리</button>
    <div id="jadoo-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="jinsoon.jpeg" alt="김치포자만두">
    <p>진라면 순한맛</p>
    <p>1,000원</p>
    <button onclick="toggleSoldOut('jinsoon-status')">완판 처리</button>
    <div id="jinsoon-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="nak.jpeg" alt="김치포자만두">
    <p>비비고 낙지비빔밥</p>
    <p>6,350원</p>
    <button onclick="toggleSoldOut('nak-status')">완판 처리</button>
    <div id="nak-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="orange.jpg" alt="김치포자만두">
    <p>오렌지</p>
    <p>900원</p>
    <button onclick="toggleSoldOut('orange-status')">완판 처리</button>
    <div id="orange-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="ramyeon.jpeg" alt="김치포자만두">
    <p>라면용기</p>
    <p>800원</p>
    <button onclick="toggleSoldOut('ramyeon-status')">완판 처리</button>
    <div id="ramyeon-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="stake.jpeg" alt="김치포자만두">
    <p>고메함박스테이크</p>
    <p>4,500원</p>
    <button onclick="toggleSoldOut('stake-status')">완판 처리</button>
    <div id="stake-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="watermelon.jpeg" alt="김치포자만두">
    <p>수박컵</p>
    <p>2,500원</p>
    <button onclick="toggleSoldOut('watermelon-status')">완판 처리</button>
    <div id="watermelon-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>

  <div class="item">
    <img src="yeol.jpeg" alt="김치포자만두">
    <p>열라면</p>
    <p>1,000원</p>
    <button onclick="toggleSoldOut('yeol-status')">완판 처리</button>
    <div id="yeol-status" class="sold-out" style="display: none;">✅ 완판되었습니다</div>
  </div>
  <!-- 필요한 만큼 항목을 계속 추가 -->
</div>

<footer>
            <footer style="background-color: #F2F4F7; color: #1368BD; height: 300px; width: 100%; margin: 0 ; padding-right: 0;;">
            <img src="logo_BLUE.svg" alt="HANDONG EATS" style="position: relative; width: 280px; top: 68px; left: 80px;">
<br><br><br>
            <p style=" font-size: 18px; position: relative; top: 120px; margin-left: 80px; background-color: #F2F4F7;>2025-Summer 프론트엔드 입문</p>
            <p style="font-size: 12px; position: relative; top: 130px; margin-left: 80px;">
                <div style="background-color: #F2F4F7;">22300038 구본서 &nbsp; &nbsp; &nbsp;
                22400020 고윤 &nbsp; &nbsp; &nbsp;
                22001073 하엘림 &nbsp; &nbsp; &nbsp;
                22400190 김채은 &nbsp; &nbsp; &nbsp;
                22101034 박주현</p> </div>
        </footer>
  </p>
        </footer>

<script>

  function toggleSoldOut(id) {
    const status = document.getElementById(id);
    const isSoldOut = status.style.display === "none";
    status.style.display = isSoldOut ? "block" : "none";

    // ✅ Firebase에 상태 저장
    firebase.database().ref("soldout/" + id).set(isSoldOut);
  }

  // ✅ 페이지 로딩 시 Firebase에서 상태 불러오기
  window.onload = function() {
    const ref = firebase.database().ref("soldout");
    ref.once("value", (snapshot) => {
      const soldOutData = snapshot.val();
      if (soldOutData) {
        for (const id in soldOutData) {
          const isSoldOut = soldOutData[id];
          const status = document.getElementById(id);
          if (status) {
            status.style.display = isSoldOut ? "block" : "none";
          }
        }
      }
    });
  };
</script>

</body>
</html>

