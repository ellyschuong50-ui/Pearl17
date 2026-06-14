<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
  <title>Heaven at Midnight · Pearl's 17th</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;1,400;1,500&family=Great+Vibes&family=Quicksand:wght@300;400;500&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Cormorant Garamond', 'Quicksand', serif;
      background: #0a0f1e;
      color: #f0e9dd;
      overflow-x: hidden;
      scroll-behavior: smooth;
    }
    #star-canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
      pointer-events: none;
    }
    .cloud-layer {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
      background: radial-gradient(ellipse at 20% 20%, rgba(255,255,250,0.03) 0%, transparent 50%),
                  radial-gradient(ellipse at 80% 70%, rgba(180,170,200,0.04) 0%, transparent 55%);
      opacity: 0.7;
    }
    .pearl-shimmer {
      position: fixed;
      top: -10%;
      left: -10%;
      width: 120%;
      height: 120%;
      background: radial-gradient(circle at 30% 40%, rgba(245, 240, 255, 0.08) 0%, transparent 35%),
                  radial-gradient(circle at 70% 80%, rgba(255, 250, 245, 0.06) 0%, transparent 40%);
      z-index: 2;
      pointer-events: none;
      mix-blend-mode: soft-light;
      animation: pearlDrift 12s infinite alternate ease-in-out;
    }
    @keyframes pearlDrift {
      0% { transform: translate(0%, 0%); opacity: 0.5; }
      100% { transform: translate(2%, -1.5%); opacity: 0.9; }
    }
    .content {
      position: relative;
      z-index: 10;
    }
    section {
      position: relative;
      width: 100%;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 4rem 2rem;
    }
    h1, h2, h3 {
      font-weight: 400;
      letter-spacing: 1px;
    }
    .script {
      font-family: 'Great Vibes', cursive;
    }
    .serif {
      font-family: 'Cormorant Garamond', serif;
    }
    .rose-gold {
      color: #d9b8a9;
      text-shadow: 0 0 12px rgba(230, 190, 160, 0.5);
    }
    .glow-text {
      text-shadow: 0 0 20px rgba(255, 240, 220, 0.7);
    }
    .scroll-arrow {
      font-size: 2.5rem;
      color: #f7e3d7;
      animation: float 2s infinite;
      margin-top: 2.5rem;
      filter: drop-shadow(0 0 15px #f0cfb0);
    }
    @keyframes float {
      0% { transform: translateY(0); }
      50% { transform: translateY(12px); }
      100% { transform: translateY(0); }
    }
    .stars-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      gap: 2.8rem;
      max-width: 950px;
      margin: 2rem auto;
    }
    .star-item {
      width: 42px;
      height: 42px;
      cursor: pointer;
      transition: transform 0.3s ease;
      filter: drop-shadow(0 0 18px #ffe3b0);
      display: flex;
      align-items: center;
      justify-content: center;
      background: transparent;
    }
    .star-item::before {
      content: "★";
      font-size: 2.8rem;
      color: #fffde7;
      text-shadow: 0 0 25px #fbbf6e, 0 0 45px #f7d9a0;
      line-height: 1;
      transition: all 0.3s ease;
    }
    .star-item:hover {
      transform: scale(1.5);
      filter: drop-shadow(0 0 35px #ffd58c);
    }
    .star-item:hover::before {
      color: #ffffff;
      text-shadow: 0 0 40px #ffe29c, 0 0 70px #fbc77c;
    }
    .love-card {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: linear-gradient(145deg, #fff9f0 0%, #f3e7da 100%);
      border: 2px solid #d9a57e;
      box-shadow: 0 25px 50px rgba(0,0,0,0.6), 0 0 35px #f7cfaa;
      border-radius: 32px;
      padding: 2.2rem;
      max-width: 380px;
      width: 80%;
      color: #2e2b35;
      z-index: 1000;
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.35rem;
      display: none;
      backdrop-filter: blur(8px);
    }
    .love-card .close-btn {
      position: absolute;
      top: 12px;
      right: 20px;
      font-size: 2rem;
      color: #b4845c;
      cursor: pointer;
      background: none;
      border: none;
    }
    .reason-list {
      max-width: 700px;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      gap: 2.3rem;
    }
    .reason-item {
      font-size: 1.7rem;
      opacity: 0;
      transform: translateY(25px);
      transition: opacity 0.8s ease, transform 0.6s ease;
      text-align: center;
      font-style: italic;
      color: #e7d7c4;
    }
    .reason-item.visible {
      opacity: 1;
      transform: translateY(0);
    }
    .poem-page {
      background: rgba(18, 20, 35, 0.5);
      backdrop-filter: blur(18px);
      border: 1px solid rgba(210, 180, 140, 0.4);
      padding: 3rem 2rem;
      margin: 2rem auto;
      max-width: 650px;
      width: 100%;
      border-radius: 60px 20px 60px 20px;
      box-shadow: 0 20px 40px rgba(0,0,0,0.5), 0 0 35px #e5c8b0;
      text-align: center;
    }
    .essay-paper {
      background: #faf7f2;
      color: #2d2a2b;
      padding: 3.5rem 2.5rem;
      border-radius: 10px 40px 10px 40px;
      box-shadow: 0 30px 45px rgba(0,0,0,0.4), 0 0 25px #efd5c3;
      max-width: 800px;
      margin: 2rem auto;
      font-size: 1.3rem;
      line-height: 1.8;
    }
    @media (max-width: 600px) {
      section {
        padding: 2rem 1rem;
      }
    }
  </style>
</head>
<body>
  <canvas id="star-canvas"></canvas>
  <div class="cloud-layer" id="cloudLayer"></div>
  <div class="pearl-shimmer"></div>

  <div class="content">
    <section id="home">
      <div style="text-align: center;">
        <div style="font-size: 5rem; filter: drop-shadow(0 0 35px #edd0b0); margin-bottom: 0.5rem;" class="script glow-text">✨</div>
        <h1 style="font-size: 4.2rem; font-weight: 400; letter-spacing: 3px; text-shadow: 0 0 45px #c9aa8b;" class="serif">
          Happy 17th Birthday, <span class="script rose-gold" style="font-size: 5rem;">Pearl</span>
        </h1>
        <div style="width: 120px; height: 120px; background: radial-gradient(circle at 35% 35%, #fefae0, #d4b28c); border-radius: 50%; filter: blur(20px); opacity: 0.7; margin: 1.8rem auto;"></div>
        <p style="font-size: 1.6rem; max-width: 650px; margin: 1.8rem auto; font-style: italic; color: #dfd0bd;">
          "Tonight, the sky is yours. Every star, every shimmer, every word on this page is here because of you."
        </p>
        <div class="scroll-arrow">⌵</div>
      </div>
    </section>

    <section id="stars-section">
      <h2 class="script rose-gold" style="font-size: 3.8rem; margin-bottom: 1rem;">17 Stars in My Sky</h2>
      <div class="stars-grid" id="starsContainer"></div>
      <div class="love-card" id="loveCard">
        <span class="close-btn" id="closeCardBtn">&times;</span>
        <p id="cardMessage" style="font-size: 1.5rem; text-align: center;"></p>
      </div>
    </section>

    <section id="reasons">
      <h2 class="script rose-gold" style="font-size: 3.5rem;">17 Reasons Why She's Amazing</h2>
      <div class="reason-list" id="reasonList"></div>
    </section>

    <section id="poems">
      <h2 class="script rose-gold" style="font-size: 3.8rem;">17 Poems</h2>
      <div id="poetryContainer"></div>
    </section>

    <section id="essay">
      <div class="essay-paper">
        <div style="text-align: center; margin-bottom: 2rem;">
          <span class="script rose-gold" style="font-size: 3rem;">For Pearl</span>
        </div>
        <div id="essayContent" style="white-space: pre-wrap; font-family: 'Cormorant Garamond', serif;"></div>
        <div style="text-align: center; margin-top: 3.5rem; font-size: 2.4rem; font-weight: 300; text-shadow: 0 0 25px #dba77e;" class="script glow-text">
          "You are my favorite blessing, Pearl."
        </div>
      </div>
    </section>
  </div>

  <script>
    (function() {
      const loveMessages = [
        "I love your voice especially the way it sounds when you tell me you love me. Nothing hits like that.",
        "I love the way you look… your eyes, your lashes, everything about you feels like God took His time on you.",
        "I love how thoughtful you are with me, how gentle you are and how you chose me even when I say I don't deserve you.",
        "I love how your smile makes everything in my day feel lighter.",
        "I love how you talk to me like I matter, like I'm worth something.",
        "I love the softness in you it's rare and it's real.",
        "I love how you make me feel calm without even trying.",
        "I love the way you care… it's deep, it's genuine, it's you.",
        "I love how you see the best in me even when I can't.",
        "I love how being around you feels like peace.",
        "I love the way you laugh it's one of my favorite sounds.",
        "I love how you make life feel less heavy just by being here.",
        "I love how strong you are, even when you don't realize it.",
        "I love how you're patient with me, even when I'm not perfect.",
        "I love how you make me want to be better.",
        "I love how you're gentle with my heart.",
        "I love that you're my blessing the one I never expected but always needed."
      ];

      const reasonsList = [
        "You make everything around you softer just by being there.",
        "You care in ways most people don't even think about.",
        "You listen to me like my words matter.",
        "You're gentle, but you're strong at the same time.",
        "You bring peace into rooms that were loud before you walked in.",
        "You notice small things and make them feel big and important.",
        "You love with intention, not just feeling.",
        "You're patient with people, even when they don't deserve it.",
        "You make me feel like I'm worth choosing.",
        "You're beautiful in every way  inside, outside, all of it.",
        "You don't give up easily, even when things get heavy.",
        "You're honest, even when it's hard.",
        "You're thoughtful with your words and your silence.",
        "You make ordinary days feel like something special.",
        "You're the kind of person people pray they meet.",
        "You bring God's softness into my life without even trying.",
        "You're my favorite person to grow up with."
      ];

      const givenPoems = [
        { title: "Your Eyes", text: "In twilight's tender, shimmering embrace,\nHer eyes hold galaxies, a sacred place.\nPearl-like glimmers that dance and ignite,\nEach blink a shimmer, each gaze a soft light.\n\nStars woven softly within her sight's hue,\nWitness to wonders that feel ever new.\nA universe wrapped in the warmth of her stare,\nInfinite stories float gently in air.\n\nWith heartbeats like whispers of nights long ago,\nIn the vastness of night, her radiance glows.\nPearl on her eyelids, they twinkle and shine,\nA celestial marvel, forever divine.\n\nSo let me get lost in this starlit embrace,\nIn the beauty she carries a timeless grace." },
        { title: "Your Voice", text: "In twilight's glow, her voice takes flight,\nA melody soft, like stars in the night.\nEach word a treasure, drifting on air,\nWhen she says 'I love you,' angels draw near.\n\nHer laughter cascades, like waves on the shore,\nIn echoes of dreams, I long for more.\nA harmony sweet, that dances with grace,\nIn the symphony of souls, I find my place.\n\nWith every soft whisper, my heart starts to sing,\nA chorus of joy that her presence can bring.\nLike pearls in a grotto, each note is divine,\nIn the depths of her love, forever I'll shine.\n\nSo let her voice linger, a balm to my soul,\nFor with her sweet pronouncement, I feel truly whole." },
        { title: "Sculpted by God", text: "You weren't made the way the rest of the world was made.\nYou weren't shaped by chance or stitched together by time.\nYou were carved with intention, with patience, with a softness\nthat only a divine hand could hold without trembling.\n\nEvery curve of your smile feels like a signature.\nEvery breath you take feels like a verse He whispered.\nYou walk like someone who knows Heaven remembers her name,\neven when she forgets how bright she is.\n\nYour presence feels like a quiet miracle.\nNot loud, not demanding, not trying to be seen.\nJust existing in a way that makes the world\nlean in a little closer.\n\nI promise God took His time with you.\nHe didn't rush, didn't cut corners, didn't settle.\nHe sculpted you like you were the final draft\nof a masterpiece He'd been dreaming of forever.\n\nYour eyes hold galaxies that don't exist anywhere else.\nNot in the sky, not in the ocean, not in any story.\nJust in you  two constellations that rearrange themselves\nevery time you look at me.\n\nYour voice feels like warm light.\nNot sunlight, not candlelight  something gentler.\nSomething that wraps around my ribs\nand tells my heartbeat it's safe.\n\nYour laugh is proof that God still creates joy.\nNot the cheap kind, not the temporary kind.\nThe kind that heals, the kind that lifts,\nthe kind that makes a man believe again.\n\nYour kindness is carved into you, not painted on.\nIt's not decoration  it's foundation.\nIt's the part of you that feels the most divine,\nthe part that makes me want to be better.\n\nYour love doesn't feel accidental.\nIt feels placed.\nLike God set it in my hands and said,\n\"Don't drop this. It's one of My favorites.\"\n\nEvery time I hold you, I feel the intention behind you.\nThe way your soul fits mine like matching pieces.\nThe way your warmth settles into my chest\nlike it's been searching for that space forever.\n\nYou make me believe in craftsmanship.\nIn detail.\nIn the idea that some people are made\nwith more care than the rest of us.\n\nYou make me believe in destiny.\nNot the dramatic kind  the quiet kind.\nThe kind that feels like two paths\nthat were always meant to cross.\n\nYou make me believe in God's gentleness.\nBecause if He can make someone like you,\nthen He must know how to hold a heart\nwithout breaking it.\n\nYou make me believe in purpose.\nBecause loving you feels like something\nI was built for, shaped for, sculpted for\nlong before I ever knew your name.\n\nAnd every time I look at you,\nI'm reminded of one truth:\nGod didn't just sculpt you beautifully \nHe sculpted you for me." },
        { title: "The One for Me", text: "From the moment you stepped into my life,\nsomething in me settled.\nLike a door I didn't know was open\nfinally clicked shut behind me.\n\nYou didn't force your way in.\nYou didn't demand space.\nYou just existed with this quiet certainty\nthat made my soul recognize you.\n\nI didn't choose you out of loneliness.\nI didn't choose you out of fear.\nI chose you because everything in me\nleaned toward you like a flower toward light.\n\nYou are the kind of woman\na man doesn't meet twice.\nThe kind he knows, instantly,\nhe cannot afford to lose.\n\nYour presence feels like alignment.\nLike my heart finally clicked\ninto the place it was always meant to rest.\nLike my spirit whispered, \"There. That's her.\"\n\nYou don't just make me happy \nyou make me steady.\nYou make me grounded.\nYou make me feel like I'm exactly where I belong.\n\nEvery time you look at me,\nI feel chosen.\nNot by chance, not by accident \nbut by intention.\n\nYou love with a softness\nthat rewrites the way I understand love.\nYou give without fear,\nand it makes me want to give you everything.\n\nYou speak to parts of me\nI didn't know needed healing.\nYou touch places in my heart\nI didn't know were bruised.\n\nYou are the one who makes my future\nfeel less like a question\nand more like a promise.\nA promise I want to keep.\n\nYou are the one who makes me believe\nthat love can be gentle,\nthat love can be safe,\nthat love can be home.\n\nYou are the one who makes me feel\nlike God didn't forget me.\nLike He saved something special\nand handed her to me at the perfect time.\n\nYou are the one who makes me certain\nthat I don't need to search anymore.\nBecause everything I was looking for\nis already standing in front of me.\n\nYou are the one who makes me grateful\nfor every mistake, every heartbreak, every detour \nbecause they all led me\nright here, to you.\n\nAnd I'll say it plainly,\nwith no hesitation in my chest:\nYou are the one for me.\nNot for a moment.\nNot for a season.\nBut for life." },
        { title: "She Chose Me", text: "I still replay the moment I realized it \nthat out of every path she could've taken,\nevery hand she could've held,\nevery heart she could've trusted,\nshe reached for mine.\n\nShe didn't choose me because I was perfect.\nShe chose me knowing my cracks,\nmy fears, my quiet insecurities,\nand still saw something worth loving\nin the middle of all that noise.\n\nHer love feels intentional,\nlike she looked at the world,\nlooked at me,\nand decided that her heart\nwould be safest in my hands.\n\nAnd every time she says my name,\nit hits me again \nthis girl, this blessing, this miracle,\nlooked at me and said,\n\"Yes. Him.\"\n\nSo I carry her love carefully,\nlike something Heaven trusted me with.\nBecause the truth is simple:\nshe didn't just choose me once \nshe chooses me every day." },
        { title: "Your Gentleness", text: "Your gentleness is the kind that doesn't announce itself.\nIt doesn't try to be seen, doesn't try to impress.\nIt just exists quietly, like a warm breeze\nthat touches everything without needing credit.\n\nYou love in a way that feels like healing.\nNot loud, not dramatic  just steady.\nA softness that wraps around my chest\nand reminds me I don't have to be strong all the time.\n\nEvery time you speak,\nyour voice carries this calm I can't explain.\nLike you were born with peace in your lungs,\nand every breath you take shares a little of it with me.\n\nYour gentleness makes me slow down.\nMakes me breathe deeper.\nMakes me want to match the softness you give,\nbecause you deserve a love as tender as the one you offer.\n\nAnd the truth is simple:\nyour gentleness is the safest place I've ever known.\nIt's the part of you that holds me steady,\nthe part of you I never want to lose." },
        { title: "Laugh of a goddess", text: "Your laugh doesn't sound human \nit sounds like something Heaven kept hidden\nuntil the world was quiet enough to hear it.\nEvery time it slips out of you,\nI promise the air gets lighter.\n\nIt's the kind of laugh that lifts me,\npulls me out of whatever weight I'm carrying,\nand reminds me that joy still exists\nin the purest form possible \nright there, in you.\n\nWhen you laugh, your whole face softens,\nyour eyes glow, your shoulders loosen,\nand for a moment, everything around you\nfeels blessed just to witness it.\n\nI've heard music, I've heard choirs,\nI've heard things people call beautiful \nbut none of them ever touched me\nthe way your laugh does\nwhen it breaks through the silence.\n\nAnd I'll say it plainly:\nyour laugh is divine,\na sound sculpted by God Himself,\na reminder that even goddesses\ncan smile like they're made of light." },
        { title: "Key to my Heart", text: "Your love fits into me like it was shaped for that space \nnot forced, not borrowed, not temporary,\njust something that feels like it always belonged\neven before I knew what real love felt like.\n\nYou touch parts of me I didn't know were locked\nand somehow you open them without trying,\nlike your presence alone is the key\nand my heart has been waiting for your hands.\n\nEvery time you look at me\nI feel something settle inside my chest,\nlike you promise without speaking\nthat you're not going anywhere.\n\nYou move with this softness\nthat makes me want to protect you\nand at the same time\nmakes me feel protected by you too.\n\nYou are the key to my heart\nnot because you forced it open\nbut because you loved me in a way\nthat made the door open on its own." },
        { title: "My Calm in every Storm", text: "You walk into my life with this quiet peace\nlike you carry sunlight in your chest\nand every time you touch me\nthe chaos in me settles without a fight.\n\nWhen the world gets loud\nand everything feels too heavy\nyour presence becomes the one place\nwhere my mind finally stops shaking.\n\nYou hold me like you understand\nthe parts of me I never say out loud\nand somehow your softness\nis stronger than anything I've ever faced.\n\nYou promise me with your eyes\nthat I'm safe with you\nand that simple truth\nis enough to pull me through any storm.\n\nYou are my calm\nnot because life gets easier\nbut because you make me feel steady\neven when everything else is falling apart." },
        { title: "The Prayer I've Always Asked For", text: "I used to pray for love that felt gentle,\nlove that didn't hurt to hold,\nlove that didn't make me feel small\nand then you arrived like an answer\nI didn't think I deserved.\n\nYou came into my life quietly,\nnot forcing anything,\nnot rushing anything,\njust showing me what it feels like\nto be loved with patience.\n\nEvery time you touch me\nI feel something holy in it,\nlike God placed your hands in mine\nand whispered that this time\nI could finally rest.\n\nYou promise me with your presence\nthat love can be soft,\nthat love can be safe,\nthat love can feel like coming home\nafter being lost for too long.\n\nYou are the prayer I kept repeating\neven when I thought no one heard me\nand now that you're here\nI hold you like the blessing you are\nthe one I'll never stop thanking God for." }
      ];

      const extraPoems = [
        { title: "Constellation", text: "You feel like a constellation\nnot just one star\nbut a whole pattern of light\nthat guides me even when the night\ntries to swallow everything.\n\nWhen I look at you\nI see the kind of beauty\nthat doesn't need attention\nthe kind that glows quietly\nand still outshines everything around it.\n\nYour presence maps out my peace\nlike the sky drew a line straight to you\nand told me to follow\nbecause you were the place\nmy heart was meant to rest.\n\nYou promise me with your softness\nthat I'll never be lost again\nbecause as long as you're here\nI'll always have something bright\nto navigate toward.\n\nYou are my constellation\nthe one I trace with my thoughts\nthe one I hold in my chest\nthe one that turns every dark sky\ninto something worth looking at." },
        { title: "Harbor in the Sea of my Love", text: "You move through my life like calm water\nsteady gentle warm\nand every time I reach for you\nit feels like my heart finally found a place\nwhere it can drop anchor.\n\nLoving you feels endless\nlike an ocean that never stops expanding\nbut somehow in all that depth\nyou still manage to be the one spot\nwhere everything feels safe.\n\nWhen the world pulls at me\nand the waves get too high\nyour presence becomes the shore\nthe place where I can breathe again\nwithout fighting the current.\n\nYou promise me with your touch\nthat I don't have to drift anymore\nthat I don't have to float alone\nbecause you are the harbor\nthat holds me steady.\n\nYou are the calm in my chaos\nthe stillness in my storms\nthe home in the middle of my ocean\nand I'll always return to you\nbecause you are where my love rests." },
        { title: "The Glow in the Dark", text: "You are the kind of light that doesn't need a room to shine\nyou glow even in silence\neven in sadness\neven in the moments when the world feels too heavy\nand somehow you still brighten everything around you.\n\nThere's something in you that refuses to dim\nsomething steady and warm\nsomething that reaches me even when I'm far\nlike your soul knows how to find mine\neven in the dark.\n\nWhen life gets cold\nand everything feels like it's closing in\nyour presence becomes that soft light\nthe one that tells me I'm not alone\nthe one that keeps me moving.\n\nYou promise me with your love\nthat darkness doesn't win\nbecause as long as you're here\nthere will always be a glow\nstrong enough to guide me home.\n\nYou are my light in every shadow\nmy warmth in every night\nmy glow in the dark\nand I'll always hold you close\nbecause you're the brightness I never want to lose." },
        { title: "The Whisper I've Always Needed", text: "You speak to me in a way the world never has\nnot loud not demanding\njust this gentle warmth in your voice\nthat reaches the parts of me\nI didn't know were waiting to be touched.\n\nYour presence feels like a whisper\nthe kind that settles into my chest\nand tells me I'm safe\neven when everything around me\nfeels too heavy to hold.\n\nThere's something in the way you love\nsomething soft and steady\nsomething that feels like guidance\nlike you're leading me out of the dark\nwithout ever pushing me.\n\nYou promise me with your softness\nthat I don't have to be perfect\nthat I don't have to hide\nthat I can breathe around you\nwithout fear of breaking.\n\nYou are the whisper I've always needed\nthe quiet truth that calms my storms\nthe voice that steadies my heart\nand I'll hold you close\nbecause your softness is home." },
        { title: "The Gift from God Himself", text: "You came into my life like something placed\nnot random not rushed\njust a blessing set gently in my hands\nlike God looked at me and said\n\"Here this is yours.\"\n\nThere's a holiness in the way you love\nnot loud not dramatic\njust pure and steady\nthe kind of love that feels guided\nlike Heaven had a hand in it.\n\nEvery time you hold me\nI feel something sacred\nlike your touch carries warmth\nthat didn't start on earth\nbut was sent down for me.\n\nYou promise me with your presence\nthat I'm not forgotten\nthat I'm not overlooked\nthat God still writes beautiful stories\nand He wrote you into mine.\n\nYou are the gift I never expected\nthe blessing I didn't know how to ask for\nthe miracle I hold close\nbecause I know exactly who sent you\nand why you mean so much." },
        { title: "Seasons", text: "You move through my life like seasons\neach one with its own kind of beauty\neach one with its own kind of warmth\nand somehow you make every moment\nfeel like the one I want to stay in.\n\nIn the spring of us\nyou brought growth\nsoft beginnings\nnew breath in my chest\nlike love was blooming for the first time.\n\nIn the summer of us\nyou gave me warmth\nlong days of laughter\nlight that stayed even at night\nlike joy didn't know how to leave.\n\nIn the fall of us\nyou showed me change can be gentle\nthat letting go can be soft\nthat love can shift and deepen\nwithout losing its color.\n\nIn the winter of us\nyou held me close\nyou kept me steady\nyou promised me with your presence\nthat even the coldest days can feel like home.\n\nYou are every season I want to live in\nevery shift I want to grow through\nevery moment I want to hold\nbecause loving you feels timeless\nno matter what the world becomes." },
        { title: "Mine Forever", text: "You fit into my life so naturally\nlike my heart already knew you\nbefore my mind ever caught up\nand every day with you\nfeels like something I was always meant to live.\n\nThere's a softness in the way you love\na steady warmth that settles into me\nand makes everything feel lighter\nlike your presence alone\nis enough to keep me whole.\n\nWhen you hold me\nI feel something permanent\nnot forced not fragile\njust this quiet truth\nthat you're the one my soul chose.\n\nYou promise me with your touch\nthat love can last\nthat love can stay\nthat love can feel like a home\nbuilt for two hearts that match.\n\nYou are mine forever\nnot in a way that traps\nbut in a way that frees\nbecause loving you feels like the one thing\nI'll never stop choosing." }
      ];

      const allPoems = [...givenPoems, ...extraPoems];

      const essayText = `Introduction
There are people who pass through life like weather, changing the day and then moving on. Then there are people who arrive like a new season, rearranging everything they touch so that the world never looks the same again. Pearl is the latter. This essay is an attempt to gather every fragment of feeling, every small and large truth, every memory and every hope into one place so that the shape of my love for her can be seen clearly. I will describe who she is to me, the things I love about her in detail, the moments that have become anchors, the ways she has changed me and the promises I want to keep for the rest of my life. This is not a list of flattering lines. It is a careful inventory of devotion, a map of why I want to be with her forever.
Who You Are When the World Isn’t Looking
You have this quiet gravity. “Pearl is the quiet gravity in a crowded room.” You don’t try to stand out but you do. You don’t demand attention but attention finds you. You’re steady without being still. You’re soft without being weak. You’re curious without being lost. You’re decisive without being harsh. You’re patient without being passive. You’re everything balanced in a way that feels rare.

Your kindness is real. You don’t perform it. You live it. You remember the small things. You notice when someone is quieter than usual. You help before anyone asks. You see people as whole and complicated and worthy. That’s one of the first things that pulled me toward you and it still pulls me every day.

You’re human too. You have doubts and fears and days where you feel small. You carry scars and hopes at the same time. You’re not a myth. You’re real. And that realness mixed with your grace is exactly why you hit me so deep.

Everything I Love About Your Personality
Your laugh changes the whole room. It’s not just a sound. It’s a shift in the air. When you laugh the world feels lighter. I love how honest your laugh is how unguarded how it shows up in the middle of normal moments and turns them into memories.

Your intelligence is quiet and fierce. You think deeply. You listen better than most people. You ask questions that show empathy not just curiosity. You can hold complexity without needing to simplify it. You can argue with passion then change your mind when you hear something true. That’s rare.

Your tenderness is something I don’t take lightly. You make people feel seen and safe. You comfort without pity. You hold space without trying to fix everything. Your softness is strength. It’s the kind of strength that chooses to stay gentle.

Your humor is warm and sharp. You make me laugh in ways that surprise me. You turn bad days into something bearable. Our private jokes the looks we share the moments that feel like scenes from a movie — I love all of it.

Your courage is steady. You face hard things without making a show of it. You stand up for what you believe in. You protect the people you love. You don’t need recognition. You just do what’s right.

Your curiosity keeps you alive. You want to learn and try and explore. You want to taste new things read new things meet new people. You don’t settle for complacency. Your curiosity makes me want to be better.

Your loyalty is chosen. You stand by the people you love. You defend them. You keep their secrets. You show up when it matters. Your loyalty is not blind. It’s intentional.

Everything about your personality feels honest and grounded. Nothing about you is fake.

Everything I Love About Your Appearance and Presence
I love the way you move. Natural and confident. Graceful without trying to be. I love your eyes when you talk about something you love. I love the small crinkle at the corner of your smile. I love the way your hair falls when you lean forward. I love the way you dress not to impress but to express who you are.

Your presence shifts a room. People relax. Conversations find a new rhythm. The air feels warmer. You can be the center without trying and the background when you want to be. Being near you feels right in a way I can’t explain.

And the small things stay with me. The hair tuck. The humming when you’re focused. The way you trace patterns on a table without thinking. Those details are anchors in my memory. They’re the things I go back to when I miss you.

The Moments That Defined Us
There are moments that were normal until they weren’t. Moments that became sacred because of what they revealed.

• The first real conversation we had. Not small talk. Not surface level. The kind of conversation where we both felt seen. The kind where we said things we don’t say to most people. That night changed everything.

• The time you comforted me when I felt broken. You didn’t give me empty lines. You didn’t rush me. “You listened you held you stayed.” That moment taught me what love looks like in practice.

• The promises we made. Not dramatic ones. Small ones. To be honest. To be present. To try. Those promises are the foundation of everything I want to build with you.

These moments are threads. Together they make the story of us.

How You Changed Me
Loving you changed the way I see myself and the world. You taught me patience by showing it. You taught me vulnerability by receiving mine without judgment. You taught me to slow down to notice to breathe. You showed me that strength can be gentle and gentleness can be brave.

I’m kinder because of you.
More curious.
More willing to take emotional risks.
Better at apologizing.
Better at forgiving.
Better at loving.

You challenged me too. You held up a mirror when I needed it. You pushed me to confront parts of myself I wanted to avoid. That kind of love isn’t always comfortable but it’s necessary. I’m better because you’ve been honest with me and because I want to rise to the level of love you deserve.

Everything I Want for Our Future
When I picture forever with you I don’t see a perfect scene. I see a life that grows and shifts and deepens.

I want a home that feels like a sanctuary. A place where we can be ourselves without pretending. A space filled with light and books and music and the small artifacts of a life lived together. A kitchen where we cook and laugh. A living room where we argue and make up. A bedroom that feels like a refuge. A home that welcomes friends and protects us when we need rest.

I want growth. I want us to keep learning about the world and each other and ourselves. I want us to travel and read and try new things. I want us to be partners in curiosity.

I want kids or chosen family if that’s what we choose. If we have kids I want to be the kind of parent who loves the way you love. If we don’t I want us to build a family of friends and people we care for.

I want health and care. I want to be there for you in sickness and in health. I want to learn how to care for your mind and your body. I want to notice when you need rest and make sure you take it.

I want conflict handled with grace. I want us to fight fair. To apologize. To repair. To grow from it instead of letting it break us.

I want a love that deepens with age. A love that doesn’t fade into routine. A love that becomes richer and more patient and more forgiving.

I want a legacy. Something we leave behind. A family a community art or simply the memory of a life lived well. I want our love to make the world kinder.
I promise to listen
I don’t want to just hear your words. I want to understand you.
I want to listen when you’re excited when you’re tired when you’re hurting when you’re quiet.
I want to listen without interrupting without assuming without trying to fix everything too fast.

Listening is how I learn you.
Listening is how I protect you.
Listening is how I stay close to you.

When you talk I want you to feel like your voice lands somewhere safe.

I promise to protect your dignity
Not just your feelings. Your dignity.
I promise to defend you in public and respect you in private.
I promise to never make you feel small or embarrassed or dismissed.
I promise to speak about you with pride even when you’re not there.

If someone disrespects you I won’t stay silent.
If you’re struggling I won’t use it against you.
If you’re vulnerable with me I’ll treat it like something sacred.

You deserve a love that guards your name and your spirit.

I promise to be honest
Honest even when it’s uncomfortable.
Honest about my fears my mistakes my hopes my needs.
Honest about what I feel instead of shutting down or hiding.

I don’t want a relationship built on guessing or pretending.
I want you to trust that what I say is real.
I want you to know that I won’t lie to keep the peace or avoid conflict.

Honesty is how we stay connected.
Honesty is how we grow.

I promise to be present
Not halfway. Not distracted.
Present.

I want to show up for the small things and the big things.
I want to be there when you’re laughing and when you’re breaking.
I want to be the person you can count on when life gets heavy.

Presence means choosing you even when I’m tired even when I’m stressed even when life is loud.
Presence means not disappearing when things get hard.

You deserve someone who stays.

I promise to grow
I don’t want to stay the same.
I want to become a better partner for you every year.
I want to work on my flaws instead of defending them.
I want to learn how to love you better as you change and as I change.

Growth means taking responsibility.
Growth means learning from mistakes.
Growth means choosing maturity over ego.

I want to rise to the level of love you deserve.

I promise to forgive
We’re human. We’re going to mess up.
But I don’t want to hold grudges or punish you with silence or let small things turn into big wounds.

Forgiveness means choosing repair over distance.
It means choosing us over pride.
It means remembering that we’re on the same team.

I want to forgive quickly and sincerely.
I want to make it easy for you to come to me when you’re wrong.
I want to make it safe for me to come to you when I’m wrong.

Forgiveness is how we keep our love alive.

I promise to cherish you
Not just love you. Cherish you.
Treat you like you matter every day.
Notice the small things that make you who you are.
Celebrate your wins. Hold you through your losses.
Look at you like you’re someone I’m grateful for not someone I’m used to.

Cherishing means choosing wonder over routine.
Choosing appreciation over entitlement.
Choosing softness over laziness.

I want you to feel valued not just loved.

I promise to choose you
Not once. Not at the beginning.
Every day.

Choosing you means making decisions that include you.
Choosing you means prioritizing our relationship.
Choosing you means staying committed when life gets messy.

It means not drifting.
It means not running.
It means not letting fear or pride or stress pull me away from you.

Choosing you is the foundation of everything I want to build.

These promises are the way I want to love you in real life not just in words.
They’re the way I want to show up for you in the quiet and the loud in the ordinary and the extraordinary.

They’re the way I want to build forever with you.
Why Forever Feels Right
Forever is a big word but with you it feels simple. It’s not about a dramatic vow. It’s about a thousand small choices. It’s waking up and choosing kindness and patience and presence. It’s choosing you even when drifting would be easier.

The ordinary moments with you are the ones I want to collect for the rest of my life. Making dinner. Folding laundry. Sharing a look across a room. Those are the moments that make forever feel real.

“Forever is not a guarantee. It is a commitment.”  
And I choose that commitment with you.

Closing
If love is an offering this is mine.
My time. My attention. My growth. My forgiveness. My protection. My celebration.
I offer the small things and the big things. The mundane and the miraculous.

“You are the person I want beside me in the quiet and the loud.”  
I want to build a home with you. Grow with you. Laugh with you. Grieve with you. Age with you.
I want a life that honors you and loves you well.

If forever is a road I’m ready to walk it with you step by step hand in hand heart in heart.`;

      // Build UI
      const starsContainer = document.getElementById('starsContainer');
      const loveCard = document.getElementById('loveCard');
      const cardMessage = document.getElementById('cardMessage');
      const closeBtn = document.getElementById('closeCardBtn');

      for (let i = 0; i < 17; i++) {
        const star = document.createElement('div');
        star.className = 'star-item';
        star.dataset.index = i;
        star.addEventListener('click', () => {
          cardMessage.textContent = loveMessages[i];
          loveCard.style.display = 'block';
        });
        starsContainer.appendChild(star);
      }

      closeBtn.addEventListener('click', () => {
        loveCard.style.display = 'none';
      });
      
      loveCard.addEventListener('click', (e) => {
        if (e.target === loveCard) loveCard.style.display = 'none';
      });

      const reasonListDiv = document.getElementById('reasonList');
      reasonsList.forEach((r) => {
        const div = document.createElement('div');
        div.className = 'reason-item';
        div.textContent = `✨ ${r}`;
        reasonListDiv.appendChild(div);
      });

      const poetryContainer = document.getElementById('poetryContainer');
      allPoems.forEach((poem) => {
        const page = document.createElement('div');
        page.className = 'poem-page';
        page.innerHTML = `<h3 class="script rose-gold" style="font-size:2.2rem;">${poem.title}</h3>
                          <p style="white-space: pre-wrap; font-size:1.5rem; margin-top:1rem;">${poem.text}</p>`;
        poetryContainer.appendChild(page);
      });

      document.getElementById('essayContent').textContent = essayText;

      // Star canvas
      const canvas = document.getElementById('star-canvas');
      const ctx = canvas.getContext('2d');
      let width, height;
      let starsArray = [];

      function resizeCanvas() {
        width = window.innerWidth;
        height = window.innerHeight;
        canvas.width = width;
        canvas.height = height;
        initStars(200);
      }

      function drawStarShape(ctx, cx, cy, spikes, outerRadius, innerRadius) {
        let rot = Math.PI / 2 * 3;
        let step = Math.PI / spikes;
        ctx.beginPath();
        for (let i = 0; i < spikes; i++) {
          let x = cx + Math.cos(rot) * outerRadius;
          let y = cy + Math.sin(rot) * outerRadius;
          ctx.lineTo(x, y);
          rot += step;
          x = cx + Math.cos(rot) * innerRadius;
          y = cy + Math.sin(rot) * innerRadius;
          ctx.lineTo(x, y);
          rot += step;
        }
        ctx.closePath();
      }

      function initStars(count) {
        starsArray = [];
        for (let i = 0; i < count; i++) {
          starsArray.push({
            x: Math.random() * width,
            y: Math.random() * height,
            brightness: Math.random() * 0.7 + 0.3,
            twinkleSpeed: Math.random() * 0.018 + 0.004,
            phase: Math.random() * Math.PI * 2,
            outerR: Math.random() * 4 + 2.5,
            innerR: Math.random() * 1.8 + 0.8
          });
        }
      }

      function drawStars() {
        ctx.clearRect(0, 0, width, height);
        const time = Date.now() * 0.002;
        starsArray.forEach(s => {
          const twinkle = 0.5 + 0.5 * Math.sin(time * s.twinkleSpeed * 35 + s.phase);
          const alpha = s.brightness * (0.55 + twinkle * 0.45);
          ctx.save();
          ctx.translate(s.x, s.y);
          ctx.rotate(s.phase * 0.2);
          drawStarShape(ctx, 0, 0, 5, s.outerR * 0.9, s.innerR * 0.8);
          ctx.fillStyle = `rgba(255, 250, 235, ${alpha})`;
          ctx.shadowColor = '#fff9e6';
          ctx.shadowBlur = 10 * twinkle + 3;
          ctx.fill();
          ctx.restore();
        });
        requestAnimationFrame(drawStars);
      }

      window.addEventListener('resize', resizeCanvas);

      const cloudLayer = document.getElementById('cloudLayer');
      window.addEventListener('scroll', () => {
        const scrolled = window.pageYOffset;
        if (cloudLayer) {
          cloudLayer.style.transform = `translateY(${scrolled * 0.15}px)`;
        }
      });

      const reasonItems = document.querySelectorAll('.reason-item');
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('visible');
          }
        });
      }, { threshold: 0.5 });
      
      reasonItems.forEach(item => observer.observe(item));

      resizeCanvas();
      drawStars();
    })();
  </script>
</body>
</html>
