# htmltt.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pink Letter</title>

<style>
body{
    margin:0;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    background:#0f172a;
    font-family:Arial,sans-serif;
    overflow:hidden;
}

.envelope{
    position:relative;
    width:300px;
    height:200px;
    cursor:pointer;
}

.base{
    position:absolute;
    width:100%;
    height:100%;
    background:#e5e7eb;
    border-radius:0 0 10px 10px;
}

.flap{
    position:absolute;
    top:0;
    width:0;
    height:0;
    border-left:150px solid transparent;
    border-right:150px solid transparent;
    border-top:100px solid #cbd5e1;
    transform-origin:top;
    transition:1s;
}

.letter{
    position:absolute;
    left:15px;
    top:20px;
    width:270px;
    height:160px;
    padding:15px;
    box-sizing:border-box;
    border-radius:10px;
    
    /* 💗 PINK BACKGROUND */
    background:linear-gradient(135deg,#ffb6c1,#ffc0cb,#ffe4e1);
    
    transform:translateY(40px);
    transition:1s;
    opacity:0;
    overflow:auto;
    box-shadow:0 0 20px rgba(255,192,203,0.6);
}

.open .flap{
    transform:rotateX(180deg);
}

.open .letter{
    transform:translateY(-120px);
    opacity:1;
}

#text{
    color:#111827;
    font-size:16px;
    line-height:1.5;
    white-space:pre-wrap;
}

.note{
    color:white;
    margin-top:20px;
}
</style>
</head>

<body>

<div class="envelope" onclick="openLetter()">
    <div class="base"></div>
    <div class="flap"></div>

    <div class="letter">
        <div id="text"></div>
    </div>
</div>

<div class="note">📩 Click the envelope</div>

<script>
const message = `Hey Sakshi,

I just wanted to say that I hope you're okay. I'm sorry things turned out this way. I never wanted to cause you any trouble or make things difficult for you or your family.

Please don't be sad or cry because of me. Take care of yourself, focus on your happiness, and keep smiling.

I respect your mom's decision, so I'm stepping away. I genuinely wish you the best in life.

Take care of yourself and be happy.

- Pratik`;

let opened = false;

function openLetter(){
    if(opened) return;
    opened = true;

    document.querySelector('.envelope').classList.add('open');

    setTimeout(() => {
        let i = 0;
        const speed = 35;

        function typeWriter(){
            if(i < message.length){
                document.getElementById("text").innerHTML += message.charAt(i);
                i++;
                setTimeout(typeWriter, speed);
            }
        }
        typeWriter();
    }, 1000);
}
</script>

</body>
</html>
