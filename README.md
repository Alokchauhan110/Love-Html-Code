<!--
==================================================================
README.md - Project Documentation
(Blogspot will ignore this entire section)
==================================================================

# 💖 A Beautiful, Animated Blogspot Post for Your Girlfriend

This project contains the complete HTML, CSS, and JavaScript code for a single, beautiful, and interactive Blogspot post designed to be a romantic gift. It's filled with animations and personal touches to create a memorable experience.

**Live Demo:** [Link to Your Published Blogspot Post](https://your-blog-name.blogspot.com/)

---

## ✨ Features

This isn't just a simple blog post. It's a complete, self-contained web experience with all the following features built-in:

*   **Romantic Design:** A soft, pink gradient background with elegant, easy-to-read fonts.
*   **Stunning Animations:**
    *   Softly falling hearts in the background.
    *   A gently "beating" heart in the main title.
    *   Fade-in animations for all content sections as you scroll.
*   **Interactive Music Player:** A "Play Our Song" button to play a custom background song.
*   **Personal Memories Section:** Showcase your favorite moments with circular photos and descriptions.
*   **"Reasons I Love You" List:** A beautifully styled list to share your personal feelings.
*   **Dynamic Photo Slideshow:** An interactive carousel to browse through your favorite pictures.
*   **Secret Message:** A special button that reveals a hidden love quote or personal note.
*   **Live Countdown Timer:** A real-time countdown to a special date (like an anniversary or birthday).
*   **Symbolic Scroll Animation:** A boy and girl silhouette on the sides of the screen who move closer together as the user scrolls down the page, meeting at the end.
*   **Fully Responsive:** Looks great on both desktop computers and mobile phones, with all bugs and overlapping issues fixed.

---

## 🚀 Setup Guide

This code is designed to be pasted directly into a single Blogspot post.

1.  **Create a New Post:** In your Blogspot dashboard, click **New Post**.
2.  **Switch to HTML View:** This is the most important step. In the post editor, click the editor view icon (it might look like `< >` or a pencil) and select **HTML view**.
3.  **Copy & Paste:** Copy this entire file and paste it into the Blogspot HTML editor.
4.  **Customize:** Follow the customization guide below to add your own personal content.
5.  **Preview and Publish:** Use the "Preview" button to see how it looks. Once you're happy, hit "Publish"!

---

## 🔧 Customization Guide

All the content can be personalized. Look for the following sections in the code to make your changes.

### 1. Names and Basic Text
Change your names in the `<h1>` header and the final `<span>` signature. You can also edit the text in any of the paragraphs (`<p>`).

### 2. The Memories
Find the `.memory-card` sections. You can change the image `src`, the `<h3>` title, and the `<p>` description.

### 3. The Music 🎶
Find the `<audio>` tag and replace the `src` with a **direct link** to an `.mp3` file from a service like [archive.org](https://archive.org).

### 4. "Reasons I Love You" List
Find the `.reasons-list` section. Edit the text inside each `<li>` tag.

### 5. The Photo Slideshow
Find the `.carousel-track` section. Replace the `src` for each `<img>` tag with the URLs of your photos.

### 6. The Secret Message
Find the `#surprise-message` div and change the text inside.

### 7. The Countdown Timer
Find the `<script>` section at the very bottom. The first line of the `countdownFunction` is where you set the date. Use the format `YYYY-MM-DD`.

### 8. The Scrolling Characters
Replace the silhouette image links with your own transparent PNG files.

---

## 🌟 Credits

This project was envisioned and brought to life with passion and creativity.

*   **Maker:** **RexonBlood**
*   **Telegram Channel:** [**RexonBlack**](https://t.me/RexonBlack)

The initial code structure and features were assisted by AI. The final vision, customization, and implementation were driven by the maker.

---

Made with ❤️, for love.

-->

<!-- Start of the beautiful blog post code - FINAL VERSION WITH ALL FEATURES & FIXES -->
<style>
    /* --- FONTS & BASIC STYLES --- */
    @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Lato:wght@300;400&display=swap');

    .love-letter-container {
        font-family: 'Lato', sans-serif;
        background: linear-gradient(135deg, #ffdde1, #ee9ca7);
        color: #333;
        padding: 20px 10px;
        margin: -20px;
        overflow: hidden;
        position: relative;
    }

    /* --- FALLING HEARTS BACKGROUND --- */
    .falling-hearts { position: absolute; top: 0; left: 0; width: 100%; height: 100%; overflow: hidden; z-index: 1; }
    .heart { color: rgba(255, 255, 255, 0.6); font-size: 24px; position: absolute; animation: fall 15s infinite linear; }
    .heart:nth-child(1){ left: 10%; animation-delay: 0s; font-size: 20px; }
    .heart:nth-child(2){ left: 20%; animation-delay: 2s; animation-duration: 12s; }
    .heart:nth-child(3){ left: 30%; animation-delay: 4s; font-size: 18px; }
    .heart:nth-child(4){ left: 40%; animation-delay: 1s; animation-duration: 18s; }
    .heart:nth-child(5){ left: 50%; animation-delay: 6s; }
    .heart:nth-child(6){ left: 60%; animation-delay: 8s; font-size: 22px; }
    .heart:nth-child(7){ left: 70%; animation-delay: 3s; animation-duration: 13s; }
    .heart:nth-child(8){ left: 80%; animation-delay: 5s; font-size: 16px; }
    .heart:nth-child(9){ left: 90%; animation-delay: 7s; }

    @keyframes fall {
      0% { top: -10%; transform: rotate(0deg); }
      100% { top: 110%; transform: rotate(360deg); }
    }

    /* --- CONTENT STYLES --- */
    .love-letter-content { max-width: 800px; margin: 0 auto; padding: 20px; background: rgba(255, 255, 255, 0.9); border-radius: 15px; box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1); position: relative; z-index: 3; }

    /* --- ANIMATIONS --- */
    @keyframes fadeInUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes heartbeat { 0%, 100% { transform: scale(1); } 50% { transform: scale(1.3); } }
    .animated { animation: fadeInUp 1s ease-out forwards; opacity: 0; }
    
    /* --- SCROLL-BASED ANIMATION CHARACTERS --- */
    .character {
        position: fixed;
        bottom: 0;
        height: 150px;
        z-index: 2;
        transition: left 0.2s ease-out, right 0.2s ease-out;
        pointer-events: none;
    }
    .character img { height: 100%; width: auto; }
    #boy { left: 5%; }
    #girl { right: 5%; }

    /* --- TYPOGRAPHY & ELEMENTS --- */
    .love-letter-header h1 { font-family: 'Dancing Script', cursive; font-size: 3.5em; text-align: center; color: #d6336c; margin: 0; line-height: 1.2; }
    .love-letter-header .heart-icon { color: #d6336c; font-size: 1em; display: inline-block; animation: heartbeat 1.5s infinite ease-in-out; }
    .intro-paragraph, .closing-message p { font-size: 1.2em; line-height: 1.6; text-align: center; padding: 10px 20px; }
    .divider { border: 0; height: 1px; background-image: linear-gradient(to right, rgba(214, 51, 108, 0), rgba(214, 51, 108, 0.75), rgba(214, 51, 108, 0)); margin: 40px 0; }
    
    /* --- MEMORIES SECTION --- */
    .memory-card { display: flex; align-items: center; background: #fff; margin-bottom: 25px; border-radius: 10px; box-shadow: 0 5px 15px rgba(0,0,0,0.05); padding: 20px; }
    .memory-card:nth-child(even) { flex-direction: row-reverse; }
    .memory-card img { width: 150px; height: 150px; border-radius: 50%; object-fit: cover; border: 4px solid #f8cdda; flex-shrink: 0; }
    .memory-text { padding: 0 30px; }
    .memory-text h3 { font-family: 'Dancing Script', cursive; color: #c2255c; font-size: 2em; margin-bottom: 5px; }

    /* --- REASONS LIST --- */
    .reasons-list h2 { text-align: center; font-family: 'Dancing Script', cursive; font-size: 2.5em; color: #d6336c; line-height: 1.4; }
    .reasons-list ul { list-style: none; padding: 0; margin-top: 20px; }
    .reasons-list li { font-size: 1.1em; margin-bottom: 15px; display: flex; align-items: flex-start; line-height: 1.5; }
    .heart-bullet { color: #d6336c; margin-right: 10px; font-size: 1em; }
    
    /* --- GALLERY / SLIDESHOW --- */
    .love-letter-gallery h2 { text-align: center; font-family: 'Dancing Script', cursive; font-size: 2.5em; color: #d6336c; line-height: 1.3; }
    .carousel { position: relative; width: 100%; max-width: 600px; margin: auto; overflow: hidden; border-radius: 15px; box-shadow: 0 8px 20px rgba(0,0,0,0.1); }
    .carousel-track { display: flex; transition: transform 0.5s ease-in-out; }
    .slide { min-width: 100%; box-sizing: border-box; }
    .slide img { width: 100%; height: 400px; object-fit: cover; display: block; }
    .carousel-button { position: absolute; top: 50%; transform: translateY(-50%); background-color: rgba(255, 255, 255, 0.7); border: none; font-size: 2em; color: #d6336c; cursor: pointer; padding: 0 15px; border-radius: 50%; z-index: 10; height: 50px; width: 50px; line-height: 50px; }
    .carousel-button:hover { background-color: white; }
    .prev { left: 10px; }
    .next { right: 10px; }
    
    /* --- OTHER FEATURES --- */
    .play-button { background-color: #d6336c; color: white; border: none; padding: 12px 25px; font-size: 1em; font-family: 'Lato', sans-serif; border-radius: 50px; cursor: pointer; transition: background-color 0.3s, transform 0.2s; box-shadow: 0 4px 15px rgba(214, 51, 108, 0.4); }
    .play-button:hover { background-color: #c2255c; transform: scale(1.05); }
    .surprise-box { text-align: center; margin-top: 30px; }
    #surprise-message { display: none; margin-top: 20px; padding: 20px; background: #fff5f7; border: 1px dashed #ee9ca7; border-radius: 10px; font-style: italic; color: #555; }
    .countdown-timer h2 { text-align: center; font-family: 'Dancing Script', cursive; font-size: 2.5em; color: #d6336c; margin-bottom: 20px;}
    #countdown-display { display: grid; grid-template-columns: repeat(4, 1fr); justify-content: center; text-align: center; gap: 10px; }
    .countdown-block { background: #fff5f7; padding: 10px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05); }
    .countdown-block span { font-size: 2em; color: #c2255c; font-weight: bold; }
    .countdown-block p { font-size: 0.8em; margin: 0; color: #888; text-transform: uppercase; letter-spacing: 0.5px; }

    /* --- RESPONSIVE DESIGN --- */
    @media (max-width: 768px) {
        .character { height: 100px; }
        .love-letter-header h1 { font-size: 2.5em; }
        .memory-card, .memory-card:nth-child(even) { flex-direction: column; text-align: center; }
        .memory-card img { margin-bottom: 15px; }
        .memory-text { padding: 0; }
        .slide img { height: 300px; }
        .closing-message h2, .reasons-list h2, .countdown-timer h2, .love-letter-gallery h2 { font-size: 2.2em; }
        .memory-text h3 { font-size: 1.8em; }
        .countdown-block span { font-size: 1.5em; }
        .countdown-block p { font-size: 0.7em; }
    }
</style>

<div class="love-letter-container">
    <div class="falling-hearts">
        <div class="heart">♥</div><div class="heart">❤</div><div class="heart">♥</div><div class="heart">❤</div><div class="heart">♥</div><div class="heart">❤</div><div class="heart">♥</div><div class="heart">❤</div><div class="heart">♥</div>
    </div>
    
    <div id="boy" class="character">
        <img src="https://i.ibb.co/L5rKCMJ/boy-silhouette.png" alt="Boy silhouette">
    </div>
    <div id="girl" class="character">
        <img src="https://i.ibb.co/3zdYv1P/girl-silhouette.png" alt="Girl silhouette">
    </div>

    <div class="love-letter-content">
        <header class="love-letter-header animated"><h1>To My Dearest Riya Jogi <span class="heart-icon">♥</span></h1></header>
        <p class="intro-paragraph animated">I wanted to create something special just for you, a little corner of the internet that's all about us. Every day with you feels like a beautiful dream, and this is my little way of saying how much you mean to me.</p>
        <div class="animated" style="text-align:center; margin: 20px 0;">
            <audio id="romance-song" src="https://archive.org/download/tumare-bina-song/%20Tumare%20bina%20song%20.mp3"></audio>
            <button id="play-button" class="play-button">Play Our Song</button>
        </div>
        <hr class="divider animated">
        <div class="memory-card animated"><img src="https://i.postimg.cc/KzRdP18Y/e81384690240d07bd5dd4d1b3521b40b.jpg" alt="A meaningful photo of us"><div class="memory-text"><h3>The Day We Met</h3><p>I'll never forget the first time I saw you...</p></div></div>
        <div class="memory-card animated"><img src="https://i.postimg.cc/L6kDrpyD/05b15e4e38d92581aec0ae7424bda2bf.jpg" alt="A photo from a fun trip"><div class="memory-text"><h3>Our First Trip</h3><p>Remember that crazy road trip?...</p></div></div>
        <hr class="divider animated">
        <div class="reasons-list animated"><h2>A Few Reasons Why I Love You</h2><ul><li><span class="heart-bullet">❤</span>Because you have the most beautiful smile...</li><li><span class="heart-bullet">❤</span>Because you laugh at my silly jokes...</li><li><span class="heart-bullet">❤</span>Because you always know how to make me feel better.</li><li><span class="heart-bullet">❤</span>Because of the way you look at me.</li></ul></div>
        <hr class="divider animated">
        <div class="love-letter-gallery animated"><h2>Our Favorite Moments</h2><div class="carousel"><div class="carousel-track"><div class="slide"><img src="https://i.postimg.cc/BQHjQZHW/cb8a66dcb1cdf1221d9ccd45fcab12f3.jpg" alt="Gallery Photo 1"></div><div class="slide"><img src="https://i.postimg.cc/g0vsVbf1/541d3d1e91038317a2f8804974c07612.jpg" alt="Gallery Photo 2"></div><div class="slide"><img src="https://i.postimg.cc/44b3r2gZ/4d1cdbc138620be6257f5e4c1f51c724.jpg" alt="Gallery Photo 3"></div><div class="slide"><img src="https://i.postimg.cc/Qd7wyP2J/332798bf94aecfee68981aa74d4b82c3.jpg" alt="Gallery Photo 4"></div><div class="slide"><img src="https://i.postimg.cc/KYRNWg3S/25b2f31cc4e66352d44edccbd1825e66.jpg" alt="Gallery Photo 5"></div><div class="slide"><img src="https://i.postimg.cc/SxCwj3Nt/2373df03d944e2f99e9b35fada058212.jpg" alt="Gallery Photo 6"></div></div><button class="carousel-button prev">‹</button><button class="carousel-button next">›</button></div></div>
        <hr class="divider animated">
        <div class="surprise-box animated"><button id="surprise-button" class="play-button">A Final Thought for You...</button><div id="surprise-message"><p>"In all the world, there is no heart for me like yours. In all the world, there is no love for you like mine."<br>- Maya Angelou</p></div></div>
        <hr class="divider animated">
        <div class="countdown-timer animated"><h2>Countdown to Our Next Adventure</h2><div id="countdown-display"><div class="countdown-block"><span id="days">0</span><p>Days</p></div><div class="countdown-block"><span id="hours">0</span><p>Hours</p></div><div class="countdown-block"><span id="minutes">0</span><p>Minutes</p></div><div class="countdown-block"><span id="seconds">0</span><p>Seconds</p></div></div></div>
        <hr class="divider animated">
        <div class="closing-message animated"><h2>You are my everything, Riya Jogi.</h2><p>Thank you for filling my life with so much joy, laughter, and love. I can't wait to see what our next chapter holds.<br><br>Forever yours,<br><span style="font-family: 'Dancing Script', cursive; font-size: 1.5em;">Chulbul Pandey</span></p></div>
    </div>

    <script>
        const song=document.getElementById("romance-song"),playButton=document.getElementById("play-button");playButton.addEventListener("click",()=>{song.paused?(song.play(),playButton.textContent="Pause Song"):(song.pause(),playButton.textContent="Play Our Song")});const countdownDate=new Date("2026-06-14T00:00:00").getTime(),countdownFunction=setInterval(()=>{const e=(new Date).getTime(),t=countdownDate-e;document.getElementById("days").innerText=Math.floor(t/864e5),document.getElementById("hours").innerText=Math.floor(t%864e5/36e5),document.getElementById("minutes").innerText=Math.floor(t%36e5/6e4),document.getElementById("seconds").innerText=Math.floor(t%6e4/1e3),t<0&&(clearInterval(countdownFunction),document.getElementById("countdown-display").innerHTML="<p style='font-size:1.5em; color:#d6336c;'>The special day is here!</p>")},1e3);const track=document.querySelector(".carousel-track"),slides=Array.from(track.children),nextButton=document.querySelector(".next"),prevButton=document.querySelector(".prev");nextButton.addEventListener("click",()=>{const e=track.querySelector(".current-slide")||slides[0];let t=e.nextElementSibling;t||(t=slides[0]),track.style.transform="translateX(-"+t.getBoundingClientRect().width*slides.indexOf(t)+"px)",e.classList.remove("current-slide"),t.classList.add("current-slide")}),prevButton.addEventListener("click",()=>{const e=track.querySelector(".current-slide")||slides[0];let t=e.previousElementSibling;t||(t=slides[slides.length-1]),track.style.transform="translateX(-"+t.getBoundingClientRect().width*slides.indexOf(t)+"px)",e.classList.remove("current-slide"),t.classList.add("current-slide")});const surpriseButton=document.getElementById("surprise-button"),surpriseMessage=document.getElementById("surprise-message");surpriseButton.addEventListener("click",()=>{surpriseMessage.style.display="block"===surpriseMessage.style.display?"none":"block"});const boy=document.getElementById("boy"),girl=document.getElementById("girl");window.addEventListener("scroll",()=>{const e=document.documentElement.scrollHeight-window.innerHeight;if(e<=0)return;const t=Math.min(1,Math.max(0,window.scrollY/e)),n=5+37*t;boy.style.left=n+"%",girl.style.right=n+"%"});
    </script>
</div>