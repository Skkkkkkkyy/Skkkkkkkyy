# Skkkkkkkyy Welcome to My Profile!
<h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://instagram.com/안알려줄꺼야" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="안알려줄꺼야" height="30" width="40" /></a>
<a href="https://www.youtube.com/c/없" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/youtube.svg" alt="없" height="30" width="40" /></a>
<a href="https://discord.gg/hffvU4SR4G" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/discord.svg" alt="hffvU4SR4G" height="30" width="40" /></a>
</p>

<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.cprogramming.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg" alt="c" width="40" height="40"/> </a> <a href="https://www.java.com" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="java" width="40" height="40"/> </a> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40"/> </a> <a href="https://nodejs.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg" alt="nodejs" width="40" height="40"/> </a> <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> </p>

<p><img align="left" src="https://github-readme-stats.vercel.app/api/top-langs?username=skkkkkkkyy&show_icons=true&locale=en&layout=compact" alt="skkkkkkkyy" /></p>

<p>&nbsp;<img align="center" src="https://github-readme-stats.vercel.app/api?username=skkkkkkkyy&show_icons=true&locale=en" alt="skkkkkkkyy" /></p>
<!DOCTYPE html>

<html>
<head>
<link href="https://media.discordapp.net/attachments/954025837122945084/954025885130965012/logo_main.png" rel="shortcut icon" type="image/x-icon"/>
<title>ㅎ.</title>
<meta charset="utf-8"/>
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<meta content="WAPING WEB VENDING" property="og:title"/>
<meta content="실험사마 따라한것." property="og:description"/>
<meta content="https://media.discordapp.net/attachments/954025837122945084/954025885130965012/logo_main.png" property="og:image"/>
<meta content="#DBE6F6" data-react-helmet="true" name="theme-color"/>
<link href="https://fonts.googleapis.com" rel="preconnect"/>
<link crossorigin="" href="https://fonts.gstatic.com" rel="preconnect"/>
<link href="https://fonts.googleapis.com/css2?family=Jua&amp;display=swap" rel="stylesheet"/>
</head>
<style>
    body {
        margin: 0;
        width: 100%;
        height: 100%;
        color: rgb(255, 255, 255);
        font-family: 'Jua', sans-serif;
        font-size: 40px;
        overflow: hidden;
        background-color: #000000;
    }

    small {
        color: #cecece;
        opacity: 0.7;
        font-size: 15px;
    }

    #wave,
    #wrap {
        position: absolute;
        top: 0;
        left: 0;
    }

    #wrap {
        display: flex;
        flex-direction: column;
        width: 100%;
        height: 100%;
        overflow: hidden;
        align-items: center;
        justify-content: center;
        z-index: 1;
    }
</style>
<body>
<div id="wrap">
<img src="https://media.discordapp.net/attachments/954025837122945084/954025885130965012/logo_main.png"/>


<p>재미사마 따라한것.<br/>Support Server : https://discord.gg/hffvU4SR4G</p>
</div>
<canvas height="100" id="wave" width="100"></canvas>
<script type="module">

        export default class Wave {
            constructor(canvas, ctx, ext) {
                this.canvas = canvas;
                this.ctx = ctx;
                this.points = [];
                this.pointCount = 10;
                this.minRadius = 50;
                this.maxRadius = 100;
                this.minDeltaRadius = 5;
                this.maxDeltaRadius = 10;
                this.centerX = this.canvas.width / 2;
                this.centerY = this.canvas.height / 2;
                Object.assign(this, ext);
            }

            init(color = "lightblue") {
                this.color = color;
                let degree = 0;
                let deltaDegree = 360 / this.pointCount;
                for (let i = 0; i < this.pointCount; i++) {
                    let radius = this.randomInt(this.minRadius, this.maxRadius);
                    let x = this.centerX + radius * Math.cos(degree * Math.PI / 180);
                    let y = this.centerY + radius * Math.sin(degree * Math.PI / 180);
                    let deltaRadius = this.randomInt(this.minDeltaRadius, this.maxDeltaRadius);
                    this.points.push({
                        x: x,
                        y: y,
                        radius: radius,
                        deltaRadius: deltaRadius,
                        degree: degree
                    });
                    degree += deltaDegree;
                }
                requestAnimationFrame(this.animate.bind(this));
            }

            animate() {
                this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height);
                let prev = this.points[this.points.length - 1];
                this.ctx.beginPath();
                this.ctx.fillStyle = this.color;
                this.ctx.moveTo(prev.x, prev.y);
                this.points.forEach(point => {
                    // this.ctx.arc(point.x, point.y, 5, 0, Math.PI * 2, false);
                    this.ctx.quadraticCurveTo(prev.x, prev.y, (prev.x + point.x) / 2, (prev.y + point.y) / 2);
                    prev = { ...point };
                    point.radius += point.deltaRadius;
                    point.x = this.centerX + point.radius * Math.cos(point.degree * Math.PI / 180);
                    point.y = this.centerY + point.radius * Math.sin(point.degree * Math.PI / 180);
                });
                this.ctx.fill();
                this.ctx.closePath();
                requestAnimationFrame(this.animate.bind(this));
            }

            randomInt(m, M) {
                return Math.floor(Math.random() * (M - m + 1)) + m;
            }
        }


        window.onload = () => {
            let canvas = document.getElementById('wave');
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            let ctx = canvas.getContext('2d');
            let wave = new Wave(canvas, ctx);
            wave.init('#A0B8C5');
        }
    </script>
<script>
                    var keydownCtrl = 0;
                    var keydownShift = 0;
                    document.onkeydown=keycheck;
                    document.onkeyup=uncheckCtrlShift;
                    function keycheck()
                    {
                    switch(event.keyCode){ 
                    case 123:event.keyCode='';return false; break;
                    case 17:event.keyCode='';keydownCtrl=1;return false; break;
                    }
                    if(keydownCtrl) return false;
                    }
                    function uncheckCtrlShift()
                    {
                    if(event.keyCode==17)      keydownCtrl=0;
                    if(event.keyCode==16)      keydownShift=0;
                    }
                    function click()
                    {
                    if ((event.button==2) || (event.button==2)) 
                    {alert('깃허브!.\n지원 서버 : https://discord.gg/hffvU4SR4G');}
                }
                document.onmousedown=click;
                </script>
</body>
</html>
