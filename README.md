<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=900, initial-scale=1.0" />
<title>난이도 선택</title>
<style>
body {
background: #fbfbff;
min-height: 100vh;
width: 100vw;
display: flex;
justify-content: center;
align-items: center;
margin: 0;
}

.level-select-container {
position: relative;
width: 900px;
height: 650px;
background: #F8F6FF;
border-radius: 32px;
box-shadow: 0 4px 32px rgba(0,0,0,0.08);
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
margin: auto;
overflow: hidden;
}

/* 나가기 버튼 (컨테이너 안, 왼쪽 위) */
.exit-btn {
position: absolute;
top: 20px;
left: 40px;
background: none;
border: none;
padding: 0;
z-index: 200;
cursor: pointer;
width: 80px;
height: 80px;
display: flex;
align-items: center;
justify-content: center;
transition: filter 0.18s;
}
.exit-btn img {
width: 100%;
height: auto;
display: block;
pointer-events: none;
user-select: none;
}
.exit-btn:hover,
.exit-btn:focus {
filter: brightness(1.15) drop-shadow(0 2px 8px #a18fff55);
}

/* 타이틀 이미지 */
.level-title-img {
position: absolute;
top: 34px;
left: 50%;
transform: translateX(-50%);
width: 380px;
max-width: 80vw;
z-index: 10;
user-select: none;
pointer-events: none;
animation: popIn 0.8s cubic-bezier(.6,-0.28,.74,.05), bounceTitle 2.2s 1.2s infinite alternate;
}

/* 팝인/바운스 애니메이션 */
@keyframes popIn {
0% { opacity: 0; transform: translateX(-50%) scale(0.7);}
70% { opacity: 1; transform: translateX(-50%) scale(1.12);}
100% { opacity: 1; transform: translateX(-50%) scale(1);}
}
@keyframes bounceTitle {
0% { transform: translateX(-50%) scale(1);}
60% { transform: translateX(-50%) scale(1.04);}
100% { transform: translateX(-50%) scale(1);}
}

/* 화살표 이미지 */
.level-arrow {
position: absolute;
left: 130px;
top: 50px;
width: 100px;
height: 110px;
transition: top 0.23s cubic-bezier(.4,2,.6,1);
pointer-events: none;
z-index: 2;
display: none;
transform: rotate(90deg);
}

/* 버튼 세로 정렬 */
.level-btns {
display: flex;
flex-direction: column;
gap: 35px;
margin-left: 130px;
margin-top: 80px;
}

/* 난이도 버튼 - 크기 키움 */
.level-btn {
background: #f3ebff;
top: 20px;
left: 50px;
border: none;
padding: 0;
outline: none;
cursor: pointer;
border-radius: 25px;
box-shadow: 0 6px 18px rgba(120,100,255,0.10);
transition: box-shadow 0.2s, background 0.2s;
width: 500px;
height: 130px;
display: flex;
align-items: center;
justify-content: center;
position: relative;
font-size: 1.1em;
}
.level-btn:hover,
.level-btn:focus {
box-shadow: 0 10px 32px rgba(41, 27, 130, 0.15);
background: #ede6ff;
}

/* 버튼 안의 난이도 이미지 - 크기 키움 */
.level-btn img {
width: 300px;
height: auto;
pointer-events: none;
user-select: none;
display: block;
}

/* 반응형 대응 */
@media (max-width: 700px) {
.level-select-container {
width: 98vw;
min-width: 320px;
min-height: 360px;
padding-left: 0;
}
.level-title-img {
width: 48vw;
min-width: 120px;
top: 16px;
}
.level-btn {
width: 80vw;
height: 16vw;
min-height: 64px;
}
.level-btn img {
width: 58vw;
min-width: 120px;
}
.level-btns {
margin-left: 0;
margin-top: 10vw;
gap: 6vw;
}
.exit-btn {
top: 10px;
left: 10px;
width: 38px;
height: 38px;
}
}
</style>
</head>
<body>
<div class="level-select-container">
<!-- 나가기 버튼 (컨테이너 안, 왼쪽 위) -->
<button class="exit-btn" id="exitBtn" title="나가기">
<img src="img/exit.png" alt="나가기" />
</button>
<!-- 타이틀 이미지 -->
<img src="img/level-title.png" class="level-title-img" alt="난이도 선택" />
<img src="img/hand-arrow.png" alt="화살표" class="level-arrow" id="levelArrow" />
<div class="level-btns">
<button class="level-btn" data-index="0">
<img src="img/easy.png" alt="초급(유치원)" />
</button>
<button class="level-btn" data-index="1">
<img src="img/normal.png" alt="중급(초1~2)" />
</button>
<button class="level-btn" data-index="2">
<img src="img/hard.png" alt="고급(초3)" />
</button>
</div>
</div>
<script>
const levelBtns = document.querySelectorAll('.level-btn');
const arrow = document.getElementById('levelArrow');

levelBtns.forEach((btn) => {
btn.addEventListener('mouseenter', () => {
// 40px 더 위로 올림
arrow.style.top = (btn.offsetTop + btn.offsetHeight/2 - arrow.offsetHeight/2 - 40) + "px";
arrow.style.display = 'block';
});
btn.addEventListener('mouseleave', () => {
arrow.style.display = 'none';
});
});

// 나가기 버튼 클릭 시 fnum-game.html로 이동
document.getElementById('exitBtn').onclick = function() {
window.location.href = 'fnum-game.html';
};
</script>
</body>
</html>
