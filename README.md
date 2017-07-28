<!-- CSS media query on a link element -->
<html>
<head>
<script type="text/javascript">
var img = new Image();

// 변수
// 스크롤될 이미지, 방향, 속도를 바꾸려면 변수값을 바꾼다.

img.src = 'https://mdn.mozillademos.org/files/4553/Capitan_Meadows,_Yosemite_National_Park.jpg';
var CanvasXSize = 800;
var CanvasYSize = 800;
var speed = 10; // 값이 작을 수록 빨라진다
var scale = 1.05;
var y = 0; // 수직 옵셋

// 주요 프로그램

var dx = 0.75;
var imgW;
var imgH;
var x = 0;
var clearX;
var clearY;
var ctx;

img.onload = function() {
    imgW = img.width*scale;
    imgH = img.height*scale;
    if (imgW > CanvasXSize) { x = CanvasXSize-imgW; } // 캔버스보다 큰 이미지
    if (imgW > CanvasXSize) { clearX = imgW; } // 캔버스보다 큰 이미지
    else { clearX = CanvasXSize; }
    if (imgH > CanvasYSize) { clearY = imgH; } // 캔버스보다 큰 이미지
    else { clearY = CanvasYSize; }
    // 캔버스 요소 얻기
    ctx = document.getElementById('canvas').getContext('2d');
    // 새로 그리기 속도 설정
    return setInterval(draw, speed);
}

function draw() {
    // 캔버스를 비운다
    ctx.clearRect(0,0,clearX,clearY);
    // 이미지가 캔버스보다 작거나 같다면 (If image is <= Canvas Size)
    if (imgW <= CanvasXSize) {
        // 재설정, 처음부터 시작
        if (x > (CanvasXSize)) { x = 0; }
        // 추가 이미지 그리기
        if (x > (CanvasXSize-imgW)) { ctx.drawImage(img,x-CanvasXSize+1,y,imgW,imgH); }
    }
    // 이미지가 캔버스보다 크다면 (If image is > Canvas Size)
    else {
        // 재설정, 처음부터 시작
        if (x > (CanvasXSize)) { x = CanvasXSize-imgW; }
        // 추가 이미지 그리기
        if (x > (CanvasXSize-imgW)) { ctx.drawImage(img,x-imgW+1,y,imgW,imgH); }
    }
    // 이미지 그리기
    ctx.drawImage(img,x,y,imgW,imgH);
    // 움직임 정도
    x += dx;
}
</script>
<style>
canvas { 
border: 1px solid black;
}
h1 {
  color: blue;
  background-color: yellow;
  border: 1px solid black;
}

p {
  color: red;
}

li {
  text-shadow: 2px 2px 3px purple;
}
p2 {
  color: green;
}

</style>
</head>
<body>
<h1>Hello World!</h1>

<p>This is a paragraph.</p>
<p2>ghjkgjkg</p2>

<ul>
  <li>This is</li>
  <li>A list</li>
</ul>
<canvas id="canvas" width="800" height="200">
<p>ㅇㅏㅁㅜㅁㅏㄹ ㄷㅐㅈㅏㄴㅊㅣ</p>
</canvas>
</body>
</html>
