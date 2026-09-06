<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>iPod Forum</title>

<style>
*{
  box-sizing:border-box;
  -webkit-tap-highlight-color:transparent;
}

body{
  margin:0;
  background:#cfcfcf;
  font-family:Arial,Helvetica,sans-serif;
  color:#222;
}

#app{
  width:100%;
  max-width:520px;
  min-height:100vh;
  margin:auto;
  background:#f5f5f5;
  box-shadow:0 0 20px #777;
}

/* BARRA SUPERIOR */

.navbar{
  height:55px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:0 10px;

  background:
    linear-gradient(
      #fafafa,
      #bcbcbc
    );

  border-bottom:1px solid #777;
}

.navbar h1{
  margin:0;
  font-size:20px;
  text-shadow:0 1px white;
}

.navbutton{
  border:1px solid #777;
  border-radius:7px;

  padding:7px 11px;

  font-weight:bold;

  background:
    linear-gradient(
      #fff,
      #bbb
    );

  cursor:pointer;
}

.navbutton:active{
  background:#999;
}

/* CONTENIDO */

.screen{
  padding:12px;
}

.hidden{
  display:none!important;
}

/* BUSCADOR */

.search{
  width:100%;

  padding:11px;

  border:1px solid #999;
  border-radius:9px;

  font-size:16px;

  margin-bottom:14px;
}

/* SECCIONES */

.section{
  margin-bottom:20px;
}

.section-title{
  color:#555;

  font-size:13px;

  font-weight:bold;

  margin:8px 10px;

  text-transform:uppercase;
}

/* LISTAS */

.list{
  background:white;

  border:1px solid #aaa;

  border-radius:10px;

  overflow:hidden;
}

.item{
  padding:14px;

  border-bottom:1px solid #ddd;

  background:
    linear-gradient(
      #fff,
      #eee
    );

  cursor:pointer;
}

.item:last-child{
  border-bottom:0;
}

.item:active{
  background:#ccc;
}

.item-title{
  font-size:16px;
  font-weight:bold;
}

.item-info{
  margin-top:5px;

  color:#777;

  font-size:12px;
}

/* TARJETAS */

.card{
  background:white;

  border:1px solid #aaa;

  border-radius:10px;

  padding:14px;

  margin-bottom:12px;
}

/* INPUTS */

input,
textarea,
select{

  width:100%;

  padding:11px;

  margin-top:6px;
  margin-bottom:12px;

  border:1px solid #999;

  border-radius:9px;

  background:white;

  font-size:15px;
}

textarea{
  min-height:110px;

  resize:vertical;
}

/* BOTÓN GRANDE */

.bigbutton{

  width:100%;

  padding:12px;

  border:1px solid #777;

  border-radius:9px;

  font-size:16px;

  font-weight:bold;

  background:
    linear-gradient(
      #fff,
      #aaa
    );

  cursor:pointer;
}

.bigbutton:active{
  background:#999;
}

/* PERFIL */

.profile{
  display:flex;

  align-items:center;

  gap:12px;
}

.avatar{

  width:50px;
  height:50px;

  border-radius:50%;

  display:flex;

  justify-content:center;
  align-items:center;

  font-size:22px;

  font-weight:bold;

  background:
    linear-gradient(
      #eee,
      #999
    );

  border:1px solid #777;
}

.username{
  font-weight:bold;
}

/* RESPUESTAS */

.reply{

  background:white;

  border:1px solid #aaa;

  border-radius:9px;

  padding:12px;

  margin-bottom:8px;
}

.reply-user{
  font-weight:bold;
}

.reply-date{
  color:#888;

  font-size:11px;

  margin-top:3px;
}

.reply-body,
.topic-body{

  margin-top:9px;

  white-space:pre-wrap;

  word-break:break-word;
}

/* VACÍO */

.empty{

  padding:25px 15px;

  text-align:center;

  color:#777;
}

/* MENSAJES */

.message{

  padding:10px;

  border-radius:8px;

  margin-bottom:10px;

  background:#e4f0ff;

  border:1px solid #9bb9dd;
}

/* FILA */

.row{

  display:flex;

  align-items:center;

  justify-content:space-between;
}

.back{
  margin-bottom:12px;
}
</style>
</head>


<body>

<div id="app">

<header class="navbar">

<button
  class="navbutton"
  onclick="goHome()">

Inicio

</button>


<h1 id="pageTitle">
iPod Forum
</h1>


<button
  class="navbutton"
  onclick="showProfile()">

Perfil

</button>

</header>


<div class="screen">

<div id="message"></div>


<!-- =========================
     INICIO
========================= -->

<div id="home">

<input
  id="search"
  class="search"
  placeholder="Buscar hilos..."
  oninput="renderTopics()"
>


<div class="section">

<div class="section-title">
Categorías
</div>


<div class="list">

<div
  class="item"
  onclick="openCategory('Música')">

🎵 Música

</div>


<div
  class="item"
  onclick="openCategory('Juegos')">

🎮 Juegos

</div>


<div
  class="item"
  onclick="openCategory('Apps')">

📱 Apps

</div>


<div
  class="item"
  onclick="openCategory('Off-topic')">

💬 Off-topic

</div>

</div>

</div>


<div class="section">

<div class="row">

<div class="section-title">
Hilos recientes
</div>


<button
  class="navbutton"
  onclick="showCreateTopic()">

Nuevo

</button>

</div>


<div
  id="topics"
  class="list">

</div>

</div>

</div>



<!-- =========================
     PERFIL
========================= -->

<div
  id="profilePage"
  class="hidden">


<div
  id="profileBox"
  class="card">

</div>


</div>



<!-- =========================
     CREAR HILO
========================= -->

<div
  id="createTopicPage"
  class="hidden">


<button
  class="navbutton back"
  onclick="goHome()">

← Volver

</button>


<div class="card">

<h2>
Nuevo hilo
</h2>


<label>
Categoría
</label>


<select id="topicCategory">

<option>Música</option>

<option>Juegos</option>

<option>Apps</option>

<option>Off-topic</option>

</select>


<label>
Título
</label>


<input
  id="topicTitle"
  maxlength="100"
  placeholder="Título del hilo"
>


<label>
Mensaje
</label>


<textarea
  id="topicBody"
  placeholder="Escribe tu mensaje..."
></textarea>


<button
  class="bigbutton"
  onclick="createTopic()">

Publicar hilo

</button>

</div>

</div>



<!-- =========================
     CATEGORÍA
========================= -->

<div
  id="categoryPage"
  class="hidden">


<button
  class="navbutton back"
  onclick="goHome()">

← Volver

</button>


<h2 id="categoryTitle"></h2>


<div
  id="categoryTopics"
  class="list">

</div>

</div>



<!-- =========================
     HILO
========================= -->

<div
  id="topicPage"
  class="hidden">


<button
  class="navbutton back"
  onclick="goHome()">

← Volver

</button>


<div
  id="topicContent">

</div>


<div class="section-title">
Respuestas
</div>


<div id="replies">

</div>


<div class="card">

<h3>
Responder
</h3>


<textarea
  id="replyBody"
  placeholder="Escribe una respuesta..."
></textarea>


<button
  class="bigbutton"
  onclick="sendReply()">

Responder

</button>

</div>

</div>

</div>

</div>



<script>

/*
=========================================
DATOS LOCALES
=========================================
*/

let currentUser =
localStorage.getItem(
  "ipod_forum_username"
);


let topics =
JSON.parse(
  localStorage.getItem(
    "ipod_forum_topics"
  ) || "[]"
);


let replies =
JSON.parse(
  localStorage.getItem(
    "ipod_forum_replies"
  ) || "[]"
);


let currentTopic =
null;


/*
=========================================
GUARDAR
=========================================
*/

function saveData(){

  localStorage.setItem(
    "ipod_forum_topics",
    JSON.stringify(topics)
  );


  localStorage.setItem(
    "ipod_forum_replies",
    JSON.stringify(replies)
  );
}


/*
=========================================
SEGURIDAD
=========================================
*/

function escapeHTML(text){

  const div =
  document.createElement("div");

  div.textContent =
  text;

  return div.innerHTML;
}


/*
=========================================
MENSAJE
=========================================
*/

function showMessage(text){

  const box =
  document.getElementById(
    "message"
  );


  box.innerHTML =
  `<div class="message">
    ${escapeHTML(text)}
  </div>`;


  setTimeout(()=>{

    box.innerHTML="";

  },3000);
}


/*
=========================================
OCULTAR PÁGINAS
=========================================
*/

function hideAll(){

  [
    "home",
    "profilePage",
    "createTopicPage",
    "categoryPage",
    "topicPage"

  ].forEach(id=>{

    document
      .getElementById(id)
      .classList
      .add("hidden");

  });

}


/*
=========================================
INICIO
=========================================
*/

function goHome(){

  hideAll();


  document
    .getElementById("home")
    .classList
    .remove("hidden");


  document
    .getElementById("pageTitle")
    .textContent =
    "iPod Forum";


  renderTopics();

}


/*
=========================================
MOSTRAR HILOS
=========================================
*/

function renderTopics(){

  const container =
  document.getElementById(
    "topics"
  );


  const search =
  (
    document
      .getElementById("search")
      .value || ""
  )
  .toLowerCase();


  const filtered =
  topics.filter(topic =>

    topic.title
      .toLowerCase()
      .includes(search)

    ||

    topic.body
      .toLowerCase()
      .includes(search)

  );


  if(filtered.length===0){

    container.innerHTML =

    `<div class="empty">

      Todavía no hay hilos.

      <br><br>

      Sé el primero en crear uno.

    </div>`;

    return;
  }


  container.innerHTML =

  filtered.map(topic => `

    <div
      class="item"
      onclick="openTopic(${topic.id})">

      <div class="item-title">

        ${escapeHTML(
          topic.title
        )}

      </div>


      <div class="item-info">

        ${escapeHTML(
          topic.category
        )}

        ·

        ${escapeHTML(
          topic.username
        )}

      </div>

    </div>

  `).join("");

}


/*
=========================================
PERFIL
=========================================
*/

function showProfile(){

  hideAll();


  document
    .getElementById("profilePage")
    .classList
    .remove("hidden");


  document
    .getElementById("pageTitle")
    .textContent =
    "Perfil";


  renderProfile();

}


function renderProfile(){

  const box =
  document.getElementById(
    "profileBox"
  );


  if(!currentUser){

    box.innerHTML = `

      <h2>
        Crear perfil
      </h2>

      <p>
        Elige el nombre que utilizarás
        en el foro.
      </p>


      <input
        id="username"
        maxlength="20"
        placeholder="Nombre de usuario"
      >


      <button
        class="bigbutton"
        onclick="createProfile()">

        Crear perfil

      </button>

    `;

    return;
  }


  box.innerHTML = `

    <div class="profile">

      <div class="avatar">

        ${escapeHTML(
          currentUser
            .charAt(0)
            .toUpperCase()
        )}

      </div>


      <div>

        <div class="username">

          ${escapeHTML(
            currentUser
          )}

        </div>


        <div
          style="color:#777">

          Miembro del foro

        </div>

      </div>

    </div>


    <br>


    <button
      class="bigbutton"
      onclick="changeProfile()">

      Cambiar perfil

    </button>

  `;

}


function createProfile(){

  const input =
  document.getElementById(
    "username"
  );


  const username =
  input.value.trim();


  if(username.length < 3){

    showMessage(
      "El nombre debe tener al menos 3 caracteres."
    );

    return;
  }


  currentUser =
    username;


  localStorage.setItem(
    "ipod_forum_username",
    username
  );


  showMessage(
    "Perfil creado."
  );


  renderProfile();

}


function changeProfile(){

  currentUser =
    null;


  localStorage.removeItem(
    "ipod_forum_username"
  );


  renderProfile();

}


/*
=========================================
CREAR HILO
=========================================
*/

function showCreateTopic(){

  if(!currentUser){

    showMessage(
      "Primero crea tu perfil."
    );


    showProfile();

    return;
  }


  hideAll();


  document
    .getElementById(
      "createTopicPage"
    )
    .classList
    .remove("hidden");


  document
    .getElementById(
      "pageTitle"
    )
    .textContent =
    "Nuevo hilo";

}


function createTopic(){

  if(!currentUser){

    showMessage(
      "Primero crea tu perfil."
    );

    return;
  }


  const category =
  document
    .getElementById(
      "topicCategory"
    )
    .value;


  const title =
  document
    .getElementById(
      "topicTitle"
    )
    .value
    .trim();


  const body =
  document
    .getElementById(
      "topicBody"
    )
    .value
    .trim();


  if(!title || !body){

    showMessage(
      "Completa el título y el mensaje."
    );

    return;
  }


  const topic = {

    id:
      Date.now(),

    category:
      category,

    title:
      title,

    body:
      body,

    username:
      currentUser,

    createdAt:
      new Date().toISOString()

  };


  topics.unshift(
    topic
  );


  saveData();


  document
    .getElementById(
      "topicTitle"
    )
    .value="";


  document
    .getElementById(
      "topicBody"
    )
    .value="";


  showMessage(
    "Hilo publicado."
  );


  setTimeout(
    goHome,
    500
  );

}


/*
=========================================
CATEGORÍA
=========================================
*/

function openCategory(
  category
){

  hideAll();


  document
    .getElementById(
      "categoryPage"
    )
    .classList
    .remove("hidden");


  document
    .getElementById(
      "pageTitle"
    )
    .textContent =
    category;


  document
    .getElementById(
      "categoryTitle"
    )
    .textContent =
    category;


  const container =
  document
    .getElementById(
      "categoryTopics"
    );


  const filtered =
  topics.filter(
    topic =>
      topic.category === category
  );


  if(filtered.length===0){

    container.innerHTML =

    `<div class="empty">

      No hay hilos en esta categoría.

    </div>`;

    return;
  }


  container.innerHTML =

  filtered.map(topic => `

    <div
      class="item"
      onclick="openTopic(${topic.id})">

      <div class="item-title">

        ${escapeHTML(
          topic.title
        )}

      </div>


      <div class="item-info">

        ${escapeHTML(
          topic.username
        )}

      </div>

    </div>

  `).join("");

}


/*
=========================================
ABRIR HILO
=========================================
*/

function openTopic(id){

  const topic =
  topics.find(
    t => t.id === id
  );


  if(!topic){

    showMessage(
      "No se encontró el hilo."
    );

    return;
  }


  currentTopic =
    id;


  hideAll();


  document
    .getElementById(
      "topicPage"
    )
    .classList
    .remove("hidden");


  document
    .getElementById(
      "pageTitle"
    )
    .textContent =
    "Hilo";


  document
    .getElementById(
      "topicContent"
    )
    .innerHTML = `

      <div class="card">

        <div class="item-info">

          ${escapeHTML(
            topic.category
          )}

        </div>


        <h2>

          ${escapeHTML(
            topic.title
          )}

        </h2>


        <div class="item-info">

          Por

          ${escapeHTML(
            topic.username
          )}

        </div>


        <div class="topic-body">

          ${escapeHTML(
            topic.body
          )}

        </div>

      </div>

    `;


  renderReplies();

}


/*
=========================================
RESPUESTAS
=========================================
*/

function renderReplies(){

  const container =
  document.getElementById(
    "replies"
  );


  const topicReplies =
  replies.filter(
    reply =>
      reply.topicId === currentTopic
  );


  if(topicReplies.length===0){

    container.innerHTML =

    `<div class="empty">

      Todavía no hay respuestas.

    </div>`;

    return;
  }


  container.innerHTML =

  topicReplies.map(reply => `

    <div class="reply">

      <div class="reply-user">

        ${escapeHTML(
          reply.username
        )}

      </div>


      <div class="reply-date">

        ${new Date(
          reply.createdAt
        ).toLocaleString()}

      </div>


      <div class="reply-body">

        ${escapeHTML(
          reply.body
        )}

      </div>

    </div>

  `).join("");

}


function sendReply(){

  if(!currentUser){

    showMessage(
      "Primero crea tu perfil."
    );


    showProfile();

    return;
  }


  const textarea =
  document.getElementById(
    "replyBody"
  );


  const body =
  textarea.value.trim();


  if(!body){

    showMessage(
      "Escribe una respuesta."
    );

    return;
  }


  const reply = {

    id:
      Date.now(),

    topicId:
      currentTopic,

    body:
      body,

    username:
      currentUser,

    createdAt:
      new Date().toISOString()

  };


  replies.push(
    reply
  );


  saveData();


  textarea.value="";


  renderReplies();

}


/*
=========================================
INICIAR
=========================================
*/

goHome();

</script>

</body>
</html>
