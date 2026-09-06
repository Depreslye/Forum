
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>iPod Touch Forum</title>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
*{box-sizing:border-box}

body{
 margin:0;
 background:#c9ced3;
 font-family:-apple-system,BlinkMacSystemFont,"Helvetica Neue",Arial,sans-serif;
 color:#111;
}

.app{
 max-width:520px;
 min-height:100vh;
 margin:auto;
 background:linear-gradient(#f8f8f8,#dfe3e7);
 box-shadow:0 0 30px #777;
}

.navbar{
 height:52px;
 display:flex;
 align-items:center;
 justify-content:space-between;
 padding:0 9px;
 color:white;
 background:linear-gradient(#707b86,#252d34);
 border-bottom:1px solid #111;
 position:sticky;
 top:0;
 z-index:10;
}

.navbar h1{
 margin:0;
 font-size:20px;
 text-shadow:0 -1px #000;
}

.button{
 border:1px solid #111;
 border-radius:7px;
 padding:7px 11px;
 color:white;
 font-weight:bold;
 background:linear-gradient(#737f89,#303940);
 box-shadow:inset 0 1px #aaa,0 1px 2px #111;
}

.content{
 padding:12px;
}

.search,
input,
textarea{
 width:100%;
 border:1px solid #999;
 border-radius:8px;
 padding:10px;
 font-family:inherit;
 font-size:15px;
 background:white;
 box-shadow:inset 0 1px 3px #bbb;
}

.search{
 margin-bottom:12px;
}

textarea{
 height:110px;
 resize:none;
}

.section{
 margin:12px 5px 5px;
 color:#555;
 font-size:13px;
 font-weight:bold;
 text-shadow:0 1px white;
}

.list{
 overflow:hidden;
 background:white;
 border:1px solid #999;
 border-radius:10px;
 box-shadow:0 1px 4px #999;
 margin-bottom:14px;
}

.row{
 display:flex;
 align-items:center;
 gap:10px;
 padding:11px;
 background:linear-gradient(#fff,#e9e9e9);
 border-bottom:1px solid #ccc;
 cursor:pointer;
}

.row:last-child{
 border-bottom:none;
}

.row:active{
 background:#ccc;
}

.icon{
 width:40px;
 height:40px;
 flex:none;
 display:flex;
 align-items:center;
 justify-content:center;
 border-radius:8px;
 color:white;
 font-size:21px;
 background:linear-gradient(#74b8ed,#1764a5);
 border:1px solid #15507e;
 box-shadow:inset 0 1px #fff,0 1px 2px #777;
}

.info{
 flex:1;
}

.title{
 font-size:16px;
 font-weight:bold;
}

.subtitle{
 margin-top:3px;
 color:#777;
 font-size:12px;
}

.arrow{
 color:#aaa;
 font-size:25px;
}

.topic{
 overflow:hidden;
 background:white;
 border:1px solid #999;
 border-radius:10px;
 box-shadow:0 1px 4px #999;
}

.post{
 padding:13px;
 border-bottom:1px solid #ccc;
}

.post:last-child{
 border-bottom:none;
}

.user{
 display:flex;
 align-items:center;
 gap:9px;
}

.avatar{
 width:36px;
 height:36px;
 border-radius:50%;
 display:flex;
 align-items:center;
 justify-content:center;
 color:white;
 font-weight:bold;
 background:linear-gradient(#ddd,#888);
 border:1px solid #777;
}

.username{
 font-weight:bold;
}

.date{
 color:#888;
 font-size:11px;
}

.post h2{
 font-size:19px;
 margin:12px 0 7px;
}

.post p{
 line-height:1.45;
 white-space:pre-wrap;
}

.composer{
 display:none;
 margin-top:10px;
 padding:10px;
 background:#eee;
 border:1px solid #999;
 border-radius:10px;
 box-shadow:0 1px 3px #888;
}

.composer input,
.composer textarea{
 margin-bottom:8px;
}

.empty{
 padding:30px;
 text-align:center;
 color:#777;
}

.footer{
 padding:20px;
 text-align:center;
 color:#777;
 font-size:11px;
}
</style>
</head>

<body>

<div class="app">

<header class="navbar">

<button
 id="back"
 class="button"
 style="display:none"
>
‹ Foro
</button>

<h1 id="pageTitle">Foro</h1>

<button
 id="newTopic"
 class="button"
>
Nuevo
</button>

</header>


<main class="content" id="content">

<input
 id="search"
 class="search"
 placeholder="Buscar en el foro..."
>


<div class="section">
CATEGORÍAS
</div>


<div class="list">

<div class="row"
 onclick="openCategory('Música')">

<div class="icon">♫</div>

<div class="info">

<div class="title">
Música
</div>

<div class="subtitle">
Álbumes, artistas y producción
</div>

</div>

<div class="arrow">›</div>

</div>


<div class="row"
 onclick="openCategory('Juegos')">

<div class="icon">🎮</div>

<div class="info">

<div class="title">
Juegos
</div>

<div class="subtitle">
Consolas, juegos y comunidad
</div>

</div>

<div class="arrow">›</div>

</div>


<div class="row"
 onclick="openCategory('Apps')">

<div class="icon">▦</div>

<div class="info">

<div class="title">
Apps
</div>

<div class="subtitle">
iOS, Android y software
</div>

</div>

<div class="arrow">›</div>

</div>


<div class="row"
 onclick="openCategory('Off-topic')">

<div class="icon">☁</div>

<div class="info">

<div class="title">
Off-topic
</div>

<div class="subtitle">
Habla de cualquier cosa
</div>

</div>

<div class="arrow">›</div>

</div>

</div>


<div class="section">
TEMAS RECIENTES
</div>


<div class="list" id="topics">

<div class="empty">
Cargando...
</div>

</div>


<div
 id="composer"
 class="composer"
>

<input
 id="username"
 placeholder="Tu nombre"
>

<input
 id="topicTitle"
 placeholder="Título del tema"
>

<textarea
 id="topicBody"
 placeholder="Escribe tu publicación..."
></textarea>

<button
 class="button"
 onclick="createTopic()"
>
Publicar tema
</button>

</div>


<div class="footer">
iPod Touch Forum · ✦
</div>

</main>

</div>


<script>

/*
========================================
SUPABASE
========================================

CAMBIA ESTAS DOS VARIABLES.

Ejemplo:

const SUPABASE_URL =
"https://abcdefgh.supabase.co";

const SUPABASE_KEY =
"tu_publishable_key";

NO uses la service_role key.
*/

const SUPABASE_URL =
"TU_PROJECT_URL";

const SUPABASE_KEY =
"TU_PUBLISHABLE_KEY";


const supabase =
window.supabase.createClient(
 SUPABASE_URL,
 SUPABASE_KEY
);


let currentCategory = null;


/*
========================================
UTILIDADES
========================================
*/

function safe(text){

 return String(text)
 .replaceAll("&","&amp;")
 .replaceAll("<","&lt;")
 .replaceAll(">","&gt;")
 .replaceAll('"',"&quot;")
 .replaceAll("'","&#039;");

}


/*
========================================
CARGAR TEMAS
========================================
*/

async function loadTopics(
 category=null,
 searchText=""
){

 let query =
 supabase
 .from("topics")
 .select("*")
 .order(
  "created_at",
  {ascending:false}
 );


 if(category){

  query =
  query.eq(
   "category",
   category
  );

 }


 if(searchText){

  query =
  query.ilike(
   "title",
   `%${searchText}%`
  );

 }


 const {
  data,
  error
 } = await query;


 if(error){

  console.error(error);

  document.getElementById(
   "topics"
  ).innerHTML = `
   <div class="empty">
    No se pudo conectar con el foro.
   </div>
  `;

  return;

 }


 renderTopics(data || []);

}


/*
========================================
MOSTRAR TEMAS
========================================
*/

function renderTopics(data){

 const box =
 document.getElementById(
  "topics"
 );


 box.innerHTML = "";


 if(data.length === 0){

  box.innerHTML = `
   <div class="empty">
    Todavía no hay publicaciones.
   </div>
  `;

  return;

 }


 data.forEach(topic => {

  const row =
  document.createElement(
   "div"
  );


  row.className = "row";


  row.innerHTML = `

   <div class="icon">
    💬
   </div>

   <div class="info">

    <div class="title">
     ${safe(topic.title)}
    </div>

    <div class="subtitle">
     ${safe(topic.username)}
     ·
     ${safe(topic.category)}
    </div>

   </div>

   <div class="arrow">
    ›
   </div>
  `;


  row.onclick = () =>
   openTopic(topic.id);


  box.appendChild(row);

 });

}


/*
========================================
CATEGORÍA
========================================
*/

async function openCategory(category){

 currentCategory =
 category;


 document.getElementById(
  "pageTitle"
 ).textContent =
 category;


 document.getElementById(
  "back"
 ).style.display =
 "block";


 document.getElementById(
  "content"
 ).innerHTML = `

  <div class="section">
   TEMAS EN ${safe(
    category.toUpperCase()
   )}
  </div>

  <div
   class="list"
   id="topics"
  >
   <div class="empty">
    Cargando...
   </div>
  </div>

  <div class="footer">
   iPod Touch Forum · ✦
  </div>

 `;


 await loadTopics(
  category
 );

}


/*
========================================
ABRIR TEMA
========================================
*/

async function openTopic(id){

 const {
  data:topic,
  error
 } =
 await supabase
 .from("topics")
 .select("*")
 .eq("id",id)
 .single();


 if(error || !topic)
  return;


 const {
  data:replies
 } =
 await supabase
 .from("replies")
 .select("*")
 .eq(
  "topic_id",
  id
 )
 .order(
  "created_at",
  {ascending:true}
 );


 document.getElementById(
  "pageTitle"
 ).textContent =
 "Tema";


 document.getElementById(
  "back"
 ).style.display =
 "block";


 document.getElementById(
  "newTopic"
 ).style.display =
 "none";


 let repliesHTML = "";


 (replies || []).forEach(
 reply => {

  repliesHTML += `

   <div class="post">

    <div class="user">

     <div class="avatar">
      ${safe(
       reply.username[0] || "?"
      )}
     </div>

     <div>

      <div class="username">
       ${safe(
        reply.username
       )}
      </div>

      <div class="date">
       ${new Date(
        reply.created_at
       ).toLocaleString()}
      </div>

     </div>

    </div>

    <p>
     ${safe(reply.body)}
    </p>

   </div>

  `;

 });


 document.getElementById(
  "content"
 ).innerHTML = `

  <div class="topic">

   <div class="post">

    <div class="user">

     <div class="avatar">
      ${safe(
       topic.username[0] || "?"
      )}
     </div>

     <div>

      <div class="username">
       ${safe(topic.username)}
      </div>

      <div class="date">
       ${new Date(
        topic.created_at
       ).toLocaleString()}
      </div>

     </div>

    </div>


    <h2>
     ${safe(topic.title)}
    </h2>


    <p>
     ${safe(topic.body)}
    </p>

   </div>


   ${repliesHTML}

  </div>


  <div
   class="composer"
   style="display:block"
  >

   <input
    id="replyUsername"
    placeholder="Tu nombre"
   >

   <textarea
    id="replyBody"
    placeholder="Escribe una respuesta..."
   ></textarea>

   <button
    class="button"
    onclick="sendReply(${id})"
   >
    Responder
   </button>

  </div>

 `;

}


/*
========================================
CREAR TEMA
========================================
*/

async function createTopic(){

 const username =
 document
 .getElementById(
  "username"
 )
 .value
 .trim();


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


 if(
  !username ||
  !title ||
  !body
 ){

  alert(
   "Completa todos los campos."
  );

  return;

 }


 const {
  error
 } =
 await supabase
 .from("topics")
 .insert({

  category:
   currentCategory ||
   "Off-topic",

  title:
   title,

  body:
   body,

  username:
   username

 });


 if(error){

  console.error(error);

  alert(
   "No se pudo publicar."
  );

  return;

 }


 document
 .getElementById(
  "topicTitle"
 ).value = "";


 document
 .getElementById(
  "topicBody"
 ).value = "";


 document
 .getElementById(
  "composer"
 ).style.display =
 "none";


 loadTopics(
  currentCategory
 );

}


/*
========================================
RESPONDER
========================================
*/

async function sendReply(
 topicId
){

 const username =
 document
 .getElementById(
  "replyUsername"
 )
 .value
 .trim();


 const body =
 document
 .getElementById(
  "replyBody"
 )
 .value
 .trim();


 if(
  !username ||
  !body
 ){

  alert(
   "Completa todos los campos."
  );

  return;

 }


 const {
  error
 } =
 await supabase
 .from("replies")
 .insert({

  topic_id:
   topicId,

  username:
   username,

  body:
   body

 });


 if(error){

  console.error(error);

  alert(
   "No se pudo enviar la respuesta."
  );

  return;

 }


 openTopic(
  topicId
 );

}


/*
========================================
BOTÓN NUEVO
========================================
*/

document
 .getElementById(
  "newTopic"
 )
 .onclick = () => {

 const composer =
 document.getElementById(
  "composer"
 );


 composer.style.display =
 composer.style.display ===
 "block"
  ? "none"
  : "block";

};


/*
========================================
BUSCADOR
========================================
*/

document
 .getElementById(
  "search"
 )
 .addEventListener(
  "input",
  event => {

   loadTopics(
    currentCategory,
    event.target.value
   );

  }
 );


/*
========================================
VOLVER
========================================
*/

document
 .getElementById(
  "back"
 )
 .onclick = () => {

  location.reload();

 };


/*
========================================
TIEMPO REAL
========================================
*/

supabase
 .channel("forum")
 .on(
  "postgres_changes",
  {
   event:"INSERT",
   schema:"public",
   table:"topics"
  },
  () => {

   loadTopics(
    currentCategory
   );

  }
 )
 .subscribe();


/*
========================================
INICIAR
========================================
*/

loadTopics();

</script>

</body>
</html>
