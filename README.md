<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>VELO RACE X</title>

<style>
/* =========================
   GLOBAL
========================= */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    scroll-behavior:smooth;
}

body{
    font-family:Arial, sans-serif;
    background:#050505;
    color:white;
    overflow-x:hidden;
}

/* =========================
   CSS VARIABLES
========================= */

:root{
    --red:#ff003c;
    --blue:#00e5ff;
    --yellow:#ffe600;
    --dark:#111;
    --glass:rgba(255,255,255,0.08);
}

/* =========================
   BACKGROUND ANIMATION
========================= */

body::before{
    content:"";
    position:fixed;
    inset:0;
    background:
    radial-gradient(circle at top left,var(--red),transparent 40%),
    radial-gradient(circle at bottom right,var(--blue),transparent 40%);
    animation:bgMove 10s infinite alternate ease-in-out;
    z-index:-2;
    filter:blur(120px);
}

@keyframes bgMove{
    0%{transform:scale(1) rotate(0deg);}
    100%{transform:scale(1.2) rotate(10deg);}
}

/* =========================
   HERO
========================= */

.hero{
    height:100vh;
    position:relative;
    display:flex;
    align-items:center;
    justify-content:center;
    overflow:hidden;
}

.hero video,
.hero img{
    position:absolute;
    width:100%;
    height:100%;
    object-fit:cover;
    animation:zoomBg 15s infinite alternate;
}

@keyframes zoomBg{
    from{transform:scale(1);}
    to{transform:scale(1.2);}
}

.overlay{
    position:absolute;
    inset:0;
    background:rgba(0,0,0,0.5);
}

.hero-content{
    position:relative;
    z-index:2;
    text-align:center;
    animation:fadeInUp 2s ease;
}

.hero h1{
    font-size:90px;
    letter-spacing:5px;
    text-transform:uppercase;
    animation:
        neon 2s infinite alternate,
        shake 4s infinite;
}

.hero p{
    margin-top:20px;
    font-size:24px;
    opacity:0;
    animation:fadeText 2s forwards 1s;
}

.btn{
    display:inline-block;
    margin-top:40px;
    padding:18px 40px;
    border-radius:50px;
    text-decoration:none;
    color:white;
    background:linear-gradient(45deg,var(--red),var(--blue));
    transition:0.4s;
    position:relative;
    overflow:hidden;
}

.btn:hover{
    transform:scale(1.1) rotate(-2deg);
    box-shadow:0 0 40px var(--blue);
}

.btn::before{
    content:"";
    position:absolute;
    width:200%;
    height:200%;
    background:rgba(255,255,255,0.2);
    transform:rotate(45deg);
    left:-120%;
    top:-120%;
    transition:1s;
}

.btn:hover::before{
    left:100%;
    top:100%;
}

/* =========================
   SECTIONS
========================= */

section{
    padding:120px 10%;
}

.title{
    font-size:60px;
    margin-bottom:50px;
    text-align:center;
    animation:glow 2s infinite alternate;
}

/* =========================
   CARDS
========================= */

.cards{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(300px,1fr));
    gap:40px;
}

.card{
    background:var(--glass);
    backdrop-filter:blur(20px);
    border:1px solid rgba(255,255,255,0.1);
    border-radius:25px;
    overflow:hidden;
    position:relative;
    transition:0.5s;
    animation:float 5s infinite ease-in-out;
}

.card:hover{
    transform:
        translateY(-20px)
        scale(1.05)
        rotate(1deg);
}

.card img{
    width:100%;
    height:400px;
    object-fit:contain;
    transition:1s;
}

.card:hover img{
    transform:scale(1.2) rotate(2deg);
    filter:brightness(1.2);
}

.card-content{
    padding:30px;
}

.card h3{
    font-size:30px;
    margin-bottom:15px;
}

/* =========================
   PARALLAX
========================= */

.parallax{
    height:80vh;
    background: url("your-bike-image.jpg") center/cover fixed;
    display:flex;
    align-items:center;
    justify-content:center;
    position:relative;
}

.parallax::before{
    content:"";
    position:absolute;
    inset:0;
    background:rgba(0,0,0,0.5);
}

.parallax h2{
    position:relative;
    z-index:2;
    font-size:80px;
    animation:slideIn 2s ease;
}

.parallax img{ 
    width:100%;
    height:400px;
    object-fit:contain;
    transition:1s;
}


/* =========================
   MARQUEE
========================= */

.marquee{
    white-space:nowrap;
    overflow:hidden;
    background:var(--red);
    padding:20px 0;
}

.marquee h2{
    display:inline-block;
    padding-left:100%;
    animation:marquee 15s linear infinite;
    font-size:50px;
}

/* =========================
   FOOTER
========================= */

footer{
    padding:80px;
    text-align:center;
    background:#000;
}

/* =========================
   PARTICLES
========================= */

.particle{
    position:absolute;
    width:10px;
    height:10px;
    background:white;
    border-radius:50%;
    animation:particleMove 10s linear infinite;
    opacity:0.5;
}

/* =========================
   KEYFRAMES
========================= */

@keyframes fadeInUp{
    from{
        opacity:0;
        transform:translateY(80px);
    }
    to{
        opacity:1;
        transform:translateY(0);
    }
}

@keyframes fadeText{
    to{
        opacity:1;
    }
}

@keyframes neon{
    from{
        text-shadow:
        0 0 10px var(--red),
        0 0 20px var(--red);
    }
    to{
        text-shadow:
        0 0 20px var(--blue),
        0 0 40px var(--blue);
    }
}

@keyframes shake{
    0%,100%{transform:translateX(0);}
    25%{transform:translateX(-2px);}
    50%{transform:translateX(2px);}
    75%{transform:translateX(-2px);}
}

@keyframes glow{
    from{
        text-shadow:0 0 10px var(--yellow);
    }
    to{
        text-shadow:0 0 30px var(--yellow);
    }
}

@keyframes float{
    0%,100%{
        transform:translateY(0);
    }
    50%{
        transform:translateY(-15px);
    }
}

@keyframes slideIn{
    from{
        opacity:0;
        transform:translateX(-200px);
    }
    to{
        opacity:1;
        transform:translateX(0);
    }
}

@keyframes marquee{
    from{
        transform:translateX(0);
    }
    to{
        transform:translateX(-100%);
    }
}

@keyframes particleMove{
    from{
        transform:translateY(100vh) scale(0);
    }
    to{
        transform:translateY(-100vh) scale(2);
    }
}

/* =========================
   RESPONSIVE
========================= */

@media(max-width:900px){

.hero h1{
    font-size:50px;
}

.title{
    font-size:40px;
}

.parallax h2{
    font-size:50px;
}

}

</style>
</head>

<body>

<!-- PARTICLES -->
<div class="particle" style="left:10%; animation-delay:0s;"></div>
<div class="particle" style="left:30%; animation-delay:2s;"></div>
<div class="particle" style="left:50%; animation-delay:4s;"></div>
<div class="particle" style="left:70%; animation-delay:1s;"></div>
<div class="particle" style="left:90%; animation-delay:3s;"></div>

<!-- HERO -->
<header class="hero">

    <!-- ВСТАВЬ СВОЕ ВИДЕО ИЛИ КАРТИНКУ -->
    <img src="layer1.png" alt="">

    <div class="overlay"></div>

    <div class="hero-content">
        <h1>VELO RACE X</h1>
        <p>Скорость. Адреналин. Легенды велогонок.</p>
        <a href="#gallery" class="btn">Смотреть гонки</a>
    </div>

</header>

<!-- MARQUEE -->
<div class="marquee">
    <h2>
        ⚡ BIKE RACING ⚡ EXTREME SPEED ⚡ CHAMPIONS ⚡ DOWNHILL ⚡
    </h2>
</div>

<!-- RIDERS -->
<section>

    <h2 class="title">ТОП ГОНЩИКИ</h2>

    <div class="cards">

        <div class="card">
            <img src="image1.png" alt="">
            <div class="card-content">
                <h3>Speed Hunter</h3>
                <p>Безумная скорость и опасные трассы.</p>
            </div>
        </div>

        <div class="card">
            <img src="layer3.png" alt="">
            <div class="card-content">

                <h3>Night Rider</h3>
                <p>Гонки ночью под неоновыми огнями.</p>
            </div>
        </div>

        <div class="card">
            <img src="intro.jpg" alt="">
            <div class="card-content">
                <h3>Mountain King</h3>
                <p>Экстремальные спуски и прыжки.</p>
            </div>
        </div>

    </div>

</section>

<!-- PARALLAX -->
<section class="parallax">
    <img src="logo1.png" alt="">
    <h2>NO LIMITS</h2>
</section>

<!-- SECTION INFO RACES -->
<section id="races">

    <h2 class="title">ЛЕГЕНДАРНЫЕ ГОНКИ</h2>

    <div class="race-container">

        <!-- CARD 1 -->
        <div class="race-card race-left">

            <img src="bpdy text3.png" class="interface-decor interface-1">


            <div class="race-image">
                <img src="race1.jpg" alt="">
            </div>

            <div class="race-info">
                <span class="race-number">01</span>

                <h3>DOWNHILL MADNESS</h3>

                <p>
                    Самые опасные спуски в мире.
                    Скорость более 90 км/ч.
                    Гонщики летят через скалы,
                    грязь и огромные трамплины.
                </p>

                <div class="race-stats">

                    <div class="stat">
                        <h4>95 KM/H</h4>
                        <span>МАКС СКОРОСТЬ</span>
                    </div>

                    <div class="stat">
                        <h4>12 KM</h4>
                        <span>ТРАССА</span>
                    </div>

                    <div class="stat">
                        <h4>EXTREME</h4>
                        <span>УРОВЕНЬ</span>
                    </div>

                </div>

            </div>

        </div>

        <!-- CARD 2 -->
        <div class="race-card race-right">

            <img src="body text3.png" class="interface-decor interface-2">


            <div class="race-image">
                <img src="race2.jpg" alt="">
            </div>

            <div class="race-info">
                <span class="race-number">02</span>

                <h3>NEON NIGHT RIDE</h3>

                <p>
                    Ночные городские гонки под
                    неоновыми огнями мегаполиса.
                    Адреналин, скорость и
                    полное безумие.
                </p>

                <div class="race-stats">

                    <div class="stat">
                        <h4>80 KM/H</h4>
                        <span>СКОРОСТЬ</span>
                    </div>

                    <div class="stat">
                        <h4>URBAN</h4>
                        <span>ГОРОД</span>
                    </div>

                    <div class="stat">
                        <h4>NIGHT</h4>
                        <span>РЕЖИМ</span>
                    </div>

                </div>

            </div>

        </div>

        <!-- CARD 3 -->
        <div class="race-card race-left">

            <div class="race-image">
                <img src="race3.jpg" alt="">
            </div>

            <div class="race-info">
                <span class="race-number">03</span>

                <h3>MOUNTAIN KINGS</h3>

                <p>
                    Гонки по горным вершинам,
                    где один неверный поворот
                    решает всё.
                </p>

                <div class="race-stats">

                    <div class="stat">
                        <h4>3000M</h4>
                        <span>ВЫСОТА</span>
                    </div>

                    <div class="stat">
                        <h4>HARDCORE</h4>
                        <span>РЕЖИМ</span>
                    </div>

                    <div class="stat">
                        <h4>ICE WIND</h4>
                        <span>ПОГОДА</span>
                    </div>

                </div>

            </div>

        </div>

    </div>

</section>

<!-- FOOTER -->
<footer>
    <h2>VELO RACE X © 2022</h2>
    <p>Самые безумные гонки велосипедистов.</p>
</footer>

</body>
</html>
