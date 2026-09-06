<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>iPod Forum</title>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
*{
  box-sizing:border-box;
  -webkit-tap-highlight-color:transparent;
}

body{
  margin:0;
  background:#d5d5d5;
  font-family:Arial,Helvetica,sans-serif;
  color:#222;
}

#app{
  max-width:520px;
  min-height:100vh;
  margin:auto;
  background:#f5f5f5;
  box-shadow:0 0 20px #777;
}

.navbar{
  height:55px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:0 10px;
  background:linear-gradient(#fafafa,#bdbdbd);
  border-bottom:1px solid #777;
}

.navbar h1{
  margin:0;
  font-size:20px;
  text-shadow:0 1px white;
}

button{
  cursor:pointer;
}

.navbutton{
  border:1px solid #777;
  border-radius:7px;
  padding:7px 12px;
  font-weight:bold;
  background:linear-gradient(#fff,#bbb);
}

.screen{
  padding:12px;
}

.hidden{
  display:none!important;
}

.search,
input,
textarea,
select{
  width:100%;
  border:1px solid #999;
  border-radius:9px;
  padding:11px;
  font-size:15px;
  background:white;
}

.search{
  margin-bottom:14px;
}

textarea{
  min-height:110px;
  resize:vertical;
  margin:6px 0 14px;
}

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

.list{
  background:white;
  border:1px solid #aaa;
  border-radius:10px;
  overflow:hidden;
}

.item{
  padding:14px;
  border-bottom:1px solid #ddd;
  background:linear-gradient(#fff,#eee);
  cursor:pointer;
}

.item:last-child{
  border-bottom:0;
}

.item:active{
  background:#ccc;
}

.item-title{
  font-weight:bold;
  font-size:16px;
}

.item-info{
  color:#777;
  font-size:12px;
  margin-top:5px;
}

.empty{
  padding:25px 15px;
  text-align:center;
  color:#777;
}

.card{
  background:white;
  border:1px solid #aaa;
  border-radius:10px;
  padding:14px;
  margin-bottom:12px;
}

.bigbutton{
  width:100%;
  padding:12px;
  border:1px solid #777;
  border-radius:9px;
  font-size:16px;
  font-weight:bold;
  background:linear-gradient(#fff,#aaa);
}

.back{
  margin-bottom:12px;
}

.row{
  display:flex;
  align-items:center;
  justify-content:space-between;
}

.profile{
  display:flex;
  align-items:center;
  gap:12px;
}

.avatar{
  width:48px;
  height:48px;
  border-radius:50%;
  display:flex;
  justify-content:center;
  align-items:center;
  font-size:22px;
  font-weight:bold;
  background:linear-gradient(#eee,#999);
  border:1px solid #777;
}

.username{
  font-weight:bold;
}

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
  white-space:pre-wrap;
  word-break:break-word;
  margin-top:9px;
}

.error,
.success{
  padding:10px;
  border-radius:8px;
  margin-bottom:10px;
}

.error{
  color:#900;
  background:#ffe0e0;
  border:1px solid #d88;
}

.success{
  color:#075b07;
  background:#dff5df;
  border:1px solid #8ac58a;
}

label{
  font-size:13px;
  font-weight:bold;
  color:#555;
}
</style>
</head>

<body>

<div id="app">

<header class="navbar">

<button class="navbutton" onclick="goHome()">
Inicio
</button>

<h1 id="pageTitle">
iPod Forum
</h1>

<button class="navbutton" onclick="showProfile()">
Perfil
</button>

</header>

<div class="screen">

<div id="message"></div>


<!-- ================= HOME ================= -->

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

<div class="item" onclick="openCategory('Música')">
🎵 Música
</div>

<div class="item" onclick="openCategory('Juegos')">
🎮 Juegos
</div>

<div class="item" onclick="openCategory('Apps')">
📱 Apps
</div>

<div class="item" onclick="openCategory('Off-topic')">
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


<!-- ================= PERFIL ================= -->

<div id="profilePage" class="hidden">

<div
  id="profileBox"
  class="card">
</div>

</div>


<!-- ================= CREAR HILO ================= -->

<div id="createTopicPage" class="hidden">

<button
  class="navbutton back"
  onclick="goHome()">
← Volver
</button>

<div class="card">

<h2>Nuevo hilo</h2>

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


<!-- ================= CATEGORÍA ================= -->

<div id="categoryPage" class="hidden">

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


<!-- ================= HILO ================= -->

<div id="topicPage" class="hidden">

<button
  class="navbutton back"
  onclick="goHome()">
← Volver
</button>

<div id="topicContent"></div>

<div class="section-title">
Respuestas
</div>

<div id="replies"></div>


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
====================================================
CONFIGURACIÓN DE SUPABASE

CAMBIA SOLAMENTE ESTAS DOS VARIABLES.

NO USES LA SERVICE_ROLE KEY.

Usa la Publishable key / anon key.
====================================================
*/

const SUPABASE_URL =
"TU_PROJECT_URL";

const SUPABASE_KEY =
"TU_PUBLISHABLE_KEY";


const supabaseClient =
window.supabase.createClient(
  SUPABASE_URL,
  SUPABASE_KEY
);


/*
====================================================
ESTADO
====================================================
*/

let currentUser =
localStorage.getItem("forum_username") || null;

let currentTopic = null;

let topics = [];


/*
====================================================
SEGURIDAD
====================================================
*/

function escapeHTML(text){

  const div =
  document.createElement("div");

  div.textContent =
  text;

  return div.innerHTML;
}


/*
====================================================
MENSAJES
====================================================
*/

function showMessage(
  text,
  type="error"
){

  const box =
  document.getElementById("message");

  box.innerHTML =
  `<div class="${type}">
    ${escapeHTML(text)}
  </div>`;

  setTimeout(()=>{
    box.innerHTML="";
  },3500);
}


/*
====================================================
OCULTAR PANTALLAS
====================================================
*/

function hideAll(){

  document
  .getElementById("home")
  .classList.add("hidden");

  document
  .getElementById("profilePage")
  .classList.add("hidden");

  document
  .getElementById("createTopicPage")
  .classList.add("hidden");

  document
  .getElementById("categoryPage")
  .classList.add("hidden");

  document
  .getElementById("topicPage")
  .classList.add("hidden");
}


/*
====================================================
INICIO
====================================================
*/

async function goHome(){

  hideAll();

  document
  .getElementById("home")
  .classList.remove("hidden");

  document
  .getElementById("pageTitle")
  .textContent="iPod Forum";

  await loadTopics();
}


/*
====================================================
CARGAR HILOS
====================================================
*/

async function loadTopics(){

  const {
    data,
    error
  } =
  await supabaseClient
  .from("topics")
  .select("*")
  .order(
    "created_at",
    {ascending:false}
  );


  if(error){

    console.error(error);

    showMessage(
      "No se pudieron cargar los hilos."
    );

    return;
  }


  topics =
  data || [];

  renderTopics();
}


/*
====================================================
MOSTRAR HILOS
====================================================
*/

function renderTopics(){

  const container =
  document.getElementById("topics");

  const search =
  (
    document.getElementById("search")
    .value || ""
  ).toLowerCase();


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
        ${escapeHTML(topic.title)}
      </div>

      <div class="item-info">
        ${escapeHTML(topic.category)}
        ·
        ${escapeHTML(topic.username)}
      </div>

    </div>

  `).join("");
}


/*
====================================================
PERFIL
====================================================
*/

function showProfile(){

  hideAll();

  document
  .getElementById("profilePage")
  .classList.remove("hidden");

  document
  .getElementById("pageTitle")
  .textContent="Perfil";

  renderProfile();
}


function renderProfile(){

  const box =
  document.getElementById("profileBox");


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
        placeholder="Nombre de usuario">

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
          ${escapeHTML(currentUser)}
        </div>

        <div style="color:#777">
          Miembro del foro
        </div>

      </div>

    </div>

    <br>

    <button
      class="bigbutton"
      onclick="logout()">

      Cambiar perfil

    </button>

  `;
}


async function createProfile(){

  const username =
  document
  .getElementById("username")
  .value
  .trim();


  if(username.length < 3){

    showMessage(
      "El nombre debe tener al menos 3 caracteres."
    );

    return;
  }


  const {
    error
  } =
  await supabaseClient
  .from("profiles")
  .insert({
    username:username
  });


  if(error){

    if(error.code==="23505"){

      showMessage(
        "Ese nombre de usuario ya existe."
      );

    }else{

      console.error(error);

      showMessage(
        "No se pudo crear el perfil."
      );

    }

    return;
  }


  currentUser =
  username;

  localStorage.setItem(
    "forum_username",
    username
  );


  showMessage(
    "Perfil creado correctamente.",
    "success"
  );

  renderProfile();
}


function logout(){

  currentUser=null;

  localStorage.removeItem(
    "forum_username"
  );

  renderProfile();

  showMessage(
    "Perfil desconectado.",
    "success"
  );
}


/*
====================================================
NUEVO HILO
====================================================
*/

function showCreateTopic(){

  if(!currentUser){

    showMessage(
      "Primero debes crear un perfil."
    );

    showProfile();

    return;
  }


  hideAll();

  document
  .getElementById("createTopicPage")
  .classList.remove("hidden");

  document
  .getElementById("pageTitle")
  .textContent="Nuevo hilo";
}


async function createTopic(){

  if(!currentUser){

    showMessage(
      "Primero crea un perfil."
    );

    return;
  }


  const category =
  document
  .getElementById("topicCategory")
  .value;


  const title =
  document
  .getElementById("topicTitle")
  .value
  .trim();


  const body =
  document
  .getElementById("topicBody")
  .value
  .trim();


  if(!title || !body){

    showMessage(
      "Completa el título y el mensaje."
    );

    return;
  }


  const {
    error
  } =
  await supabaseClient
  .from("topics")
  .insert({

    category:category,

    title:title,

    body:body,

    username:currentUser

  });


  if(error){

    console.error(error);

    showMessage(
      "No se pudo publicar el hilo."
    );

    return;
  }


  document
  .getElementById("topicTitle")
  .value="";


  document
  .getElementById("topicBody")
  .value="";


  showMessage(
    "Hilo publicado.",
    "success"
  );


  setTimeout(
    goHome,
    700
  );
}


/*
====================================================
CATEGORÍAS
====================================================
*/

function openCategory(category){

  hideAll();

  document
  .getElementById("categoryPage")
  .classList
  .remove("hidden");


  document
  .getElementById("pageTitle")
  .textContent =
  category;


  document
  .getElementById("categoryTitle")
  .textContent =
  category;


  const container =
  document
  .getElementById("categoryTopics");


  const filtered =
  topics.filter(
    topic =>
    topic.category === category
  );


  if(!filtered.length){

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
        ${escapeHTML(topic.title)}
      </div>

      <div class="item-info">
        ${escapeHTML(topic.username)}
      </div>

    </div>

  `).join("");
}


/*
====================================================
ABRIR HILO
====================================================
*/

async function openTopic(id){

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


  currentTopic=id;

  hideAll();

  document
  .getElementById("topicPage")
  .classList
  .remove("hidden");


  document
  .getElementById("pageTitle")
  .textContent =
  "Hilo";


  document
  .getElementById("topicContent")
  .innerHTML = `

    <div class="card">

      <div class="item-info">
        ${escapeHTML(topic.category)}
      </div>

      <h2>
        ${escapeHTML(topic.title)}
      </h2>

      <div class="item-info">
        Por ${escapeHTML(topic.username)}
      </div>

      <div class="topic-body">
        ${escapeHTML(topic.body)}
      </div>

    </div>

  `;


  await loadReplies(id);
}


/*
====================================================
RESPUESTAS
====================================================
*/

async function loadReplies(topicId){

  const container =
  document
  .getElementById("replies");


  const {
    data,
    error
  } =
  await supabaseClient
  .from("replies")
  .select("*")
  .eq("topic_id",topicId)
  .order(
    "created_at",
    {ascending:true}
  );


  if(error){

    console.error(error);

    return;
  }


  if(!data || !data.length){

    container.innerHTML =

    `<div class="empty">
      Todavía no hay respuestas.
    </div>`;

    return;
  }


  container.innerHTML =

  data.map(reply => `

    <div class="reply">

      <div class="reply-user">
        ${escapeHTML(reply.username)}
      </div>

      <div class="reply-date">
        ${new Date(
          reply.created_at
        ).toLocaleString()}
      </div>

      <div class="reply-body">
        ${escapeHTML(reply.body)}
      </div>

    </div>

  `).join("");
}


async function sendReply(){

  if(!currentUser){

    showMessage(
      "Primero debes crear un perfil."
    );

    showProfile();

    return;
  }


  const textarea =
  document
  .getElementById("replyBody");


  const body =
  textarea
  .value
  .trim();


  if(!body){

    showMessage(
      "Escribe una respuesta."
    );

    return;
  }


  const {
    error
  } =
  await supabaseClient
  .from("replies")
  .insert({

    topic_id:currentTopic,

    body:body,

    username:currentUser

  });


  if(error){

    console.error(error);

    showMessage(
      "No se pudo publicar la respuesta."
    );

    return;
  }


  textarea.value="";

  await loadReplies(
    currentTopic
  );
}


/*
====================================================
TIEMPO REAL

Cuando alguien crea un hilo o responde,
los demás usuarios pueden recibirlo sin
tener que recargar la página.
====================================================
*/

supabaseClient
.channel("forum-topics")

.on(
  "postgres_changes",
  {
    event:"INSERT",
    schema:"public",
    table:"topics"
  },

  payload => {

    topics.unshift(
      payload.new
    );

    renderTopics();

  }

)

.subscribe();


supabaseClient
.channel("forum-replies")

.on(
  "postgres_changes",
  {
    event:"INSERT",
    schema:"public",
    table:"replies"
  },

  payload => {

    if(
      currentTopic &&
      payload.new.topic_id === currentTopic
    ){

      loadReplies(
        currentTopic
      );

    }

  }

)

.subscribe();


/*
====================================================
ARRANCAR
====================================================
*/

goHome();

</script>

</body>
</html>
