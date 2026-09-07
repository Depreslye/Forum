<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>iPod Community</title>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
*{box-sizing:border-box}
body{
  margin:0;
  font-family:-apple-system,BlinkMacSystemFont,"Helvetica Neue",Arial,sans-serif;
  background:linear-gradient(#dfe3e8,#b7bdc5);
  color:#111;
}
#app{
  max-width:430px;
  min-height:100vh;
  margin:auto;
  background:#f4f4f4;
  box-shadow:0 0 35px #555;
  position:relative;
}
.status{
  height:22px;
  background:#111;
  color:white;
  font-size:11px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:0 8px;
}
.navbar{
  height:46px;
  background:linear-gradient(#fafafa,#cfd2d5);
  border-bottom:1px solid #777;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:5px;
  position:sticky;
  top:0;
  z-index:5;
}
.navtitle{
  font-size:20px;
  font-weight:bold;
  text-shadow:0 1px white;
}
button,.button{
  border:1px solid #777;
  border-radius:7px;
  background:linear-gradient(#fff,#c8c8c8);
  padding:7px 11px;
  font-weight:bold;
  color:#111;
  box-shadow:0 1px 2px #888;
  cursor:pointer;
}
button:active{transform:scale(.97)}
.blue{
  background:linear-gradient(#64b8ff,#147bd1);
  color:white;
  border-color:#075da8;
  text-shadow:0 -1px #245;
}
.screen{padding-bottom:70px}
.list{
  background:white;
  border-top:1px solid #aaa;
  border-bottom:1px solid #aaa;
}
.row{
  min-height:55px;
  padding:9px 12px;
  border-bottom:1px solid #ccc;
  display:flex;
  align-items:center;
  gap:10px;
  cursor:pointer;
}
.row:last-child{border-bottom:0}
.row:active{background:#ddd}
.icon{
  width:38px;height:38px;
  border-radius:9px;
  background:linear-gradient(#eee,#aaa);
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:22px;
  flex-shrink:0;
}
.arrow{
  margin-left:auto;
  color:#888;
  font-size:25px;
}
.small{font-size:12px;color:#666}
.muted{color:#777}
.center{text-align:center;padding:30px 15px}
.card{
  margin:12px;
  background:white;
  border:1px solid #aaa;
  border-radius:9px;
  box-shadow:0 1px 3px #aaa;
  overflow:hidden;
}
.cardhead{
  background:linear-gradient(#fff,#ddd);
  padding:10px;
  font-weight:bold;
  border-bottom:1px solid #aaa;
}
.cardbody{padding:12px}
input,textarea,select{
  width:100%;
  padding:10px;
  border:1px solid #999;
  border-radius:6px;
  background:white;
  margin:5px 0 10px;
  font:inherit;
}
textarea{min-height:110px;resize:vertical}
label{
  font-size:13px;
  font-weight:bold;
}
.profile{
  padding:20px;
  text-align:center;
  background:linear-gradient(#fafafa,#ddd);
  border-bottom:1px solid #aaa;
}
.avatar{
  width:105px;
  height:105px;
  border-radius:22px;
  object-fit:cover;
  border:3px solid white;
  box-shadow:0 2px 7px #777;
  background:#bbb;
}
.avatar.smallAvatar{
  width:44px;height:44px;border-radius:10px;
  border:2px solid white;
}
.username{
  font-size:22px;
  font-weight:bold;
  margin-top:8px;
}
.bio{
  margin-top:5px;
  color:#555;
  white-space:pre-wrap;
}
.toolbar{
  display:flex;
  gap:8px;
  padding:10px;
}
.toolbar button{flex:1}
.hidden{display:none!important}
.message{
  padding:10px 12px;
  border-bottom:1px solid #ccc;
}
.message.me{
  background:#e8f4ff;
}
.bottom{
  position:fixed;
  bottom:0;
  width:100%;
  max-width:430px;
  height:57px;
  background:linear-gradient(#eee,#bbb);
  border-top:1px solid #777;
  display:flex;
  z-index:10;
}
.bottom button{
  flex:1;
  border:0;
  border-radius:0;
  background:transparent;
  box-shadow:none;
  font-size:11px;
}
.bottom button span{
  display:block;
  font-size:22px;
}
.error{
  margin:10px;
  padding:10px;
  background:#ffdede;
  border:1px solid #d88;
  border-radius:7px;
  color:#900;
}
.success{
  margin:10px;
  padding:10px;
  background:#e1ffe1;
  border:1px solid #8b8;
  border-radius:7px;
  color:#174d17;
}
.topicTitle{font-size:20px;font-weight:bold}
.post{
  padding:12px;
  border-bottom:1px solid #ccc;
}
.postUser{
  display:flex;
  align-items:center;
  gap:8px;
  margin-bottom:8px;
}
a{color:#06c}
</style>
</head>

<body>

<div id="app">

  <div class="status">
    <span>iPod</span>
    <span>Wi-Fi　🔋</span>
  </div>

  <div class="navbar">
    <button id="backBtn" class="hidden" onclick="goBack()">‹ Atrás</button>
    <div id="navTitle" class="navtitle">iPod Community</div>
    <button id="navAction" class="hidden"></button>
  </div>

  <div id="screen" class="screen"></div>

  <div class="bottom">
    <button onclick="showHome()"><span>🏠</span>Inicio</button>
    <button onclick="showForums()"><span>🗂️</span>Foros</button>
    <button onclick="showMessages()"><span>💬</span>Mensajes</button>
    <button onclick="showProfile()"><span>👤</span>Perfil</button>
  </div>

</div>

<script>
/* =========================================================
   CONFIGURACIÓN SUPABASE
   ========================================================= */

const SUPABASE_URL = "TU_SUPABASE_URL";
const SUPABASE_KEY = "TU_SUPABASE_PUBLISHABLE_KEY";

const sb = window.supabase.createClient(
  SUPABASE_URL,
  SUPABASE_KEY
);

let currentUser = null;
let currentProfile = null;
let currentView = "home";
let historyStack = [];


/* =========================================================
   UTILIDADES
   ========================================================= */

const screen = document.getElementById("screen");
const navTitle = document.getElementById("navTitle");
const backBtn = document.getElementById("backBtn");
const navAction = document.getElementById("navAction");

function esc(value){
  if(value === null || value === undefined) return "";
  return String(value)
    .replaceAll("&","&amp;")
    .replaceAll("<","&lt;")
    .replaceAll(">","&gt;")
    .replaceAll('"',"&quot;")
    .replaceAll("'","&#039;");
}

function avatar(url){
  return url || "data:image/svg+xml," + encodeURIComponent(`
    <svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
      <rect width="100%" height="100%" fill="#aaa"/>
      <circle cx="100" cy="75" r="40" fill="#ddd"/>
      <circle cx="100" cy="180" r="70" fill="#ddd"/>
    </svg>
  `);
}

function setTitle(title){
  navTitle.textContent = title;
}

function setBack(show=true){
  backBtn.classList.toggle("hidden",!show);
}

function message(text,type="error"){
  return `<div class="${type}">${esc(text)}</div>`;
}


/* =========================================================
   PERFIL
   ========================================================= */

async function ensureProfile(){

  if(!currentUser) return null;

  const {data,error} = await sb
    .from("profiles")
    .select("*")
    .eq("id",currentUser.id)
    .maybeSingle();

  if(error){
    console.error(error);
    return null;
  }

  if(data){
    currentProfile=data;
    return data;
  }

  /*
    Si el usuario acaba de confirmar su correo,
    se crea automáticamente el perfil.
  */

  const username =
    currentUser.user_metadata?.username ||
    "Usuario" + currentUser.id.slice(0,6);

  const {data:newProfile,error:createError} = await sb
    .from("profiles")
    .insert({
      id:currentUser.id,
      username:username,
      bio:"",
      country:"",
      website:"",
      avatar_url:""
    })
    .select()
    .single();

  if(createError){
    console.error(createError);
    return null;
  }

  currentProfile=newProfile;
  return newProfile;
}


/* =========================================================
   INICIO
   ========================================================= */

async function showHome(){

  currentView="home";
  setTitle("iPod Community");
  setBack(false);
  navAction.classList.add("hidden");

  const userText = currentUser
    ? `Sesión iniciada como ${esc(currentProfile?.username || "Usuario")}`
    : "No has iniciado sesión.";

  screen.innerHTML=`

    <div class="profile">
      <div style="font-size:50px">🎵</div>
      <div class="username">iPod Community</div>
      <div class="bio">
        Una comunidad con estética clásica de iPod touch.
      </div>
    </div>

    <div class="card">
      <div class="cardhead">Cuenta</div>
      <div class="cardbody">
        ${userText}
        <br><br>
        ${
          currentUser
          ? `<button class="blue" onclick="showProfile()">Ver mi perfil</button>
             <button onclick="logout()">Cerrar sesión</button>`
          : `<button class="blue" onclick="showLogin()">Iniciar sesión</button>
             <button onclick="showRegister()">Crear cuenta</button>`
        }
      </div>
    </div>

    <div class="list">
      <div class="row" onclick="showForums()">
        <div class="icon">🗂️</div>
        <div>
          <b>Foros</b>
          <div class="small">Habla con la comunidad</div>
        </div>
        <div class="arrow">›</div>
      </div>

      <div class="row" onclick="showMessages()">
        <div class="icon">💬</div>
        <div>
          <b>Mensajes</b>
          <div class="small">Mensajes privados</div>
        </div>
        <div class="arrow">›</div>
      </div>

      <div class="row" onclick="showUsers()">
        <div class="icon">👥</div>
        <div>
          <b>Usuarios</b>
          <div class="small">Ver perfiles de la comunidad</div>
        </div>
        <div class="arrow">›</div>
      </div>
    </div>
  `;
}


/* =========================================================
   LOGIN
   ========================================================= */

function showLogin(){

  currentView="login";
  setTitle("Iniciar sesión");
  setBack(true);

  screen.innerHTML=`

    <div class="card">
      <div class="cardhead">Cuenta</div>

      <div class="cardbody">

        <label>Email</label>
        <input id="loginEmail" type="email">

        <label>Contraseña</label>
        <input id="loginPassword" type="password">

        <button class="blue" onclick="login()">
          Iniciar sesión
        </button>

        <button onclick="showRegister()">
          Crear una cuenta
        </button>

        <div id="loginMsg"></div>

      </div>
    </div>
  `;
}

async function login(){

  const email=document.getElementById("loginEmail").value.trim();
  const password=document.getElementById("loginPassword").value;

  const msg=document.getElementById("loginMsg");

  if(!email || !password){
    msg.innerHTML=message("Completa todos los campos.");
    return;
  }

  const {error}=await sb.auth.signInWithPassword({
    email,
    password
  });

  if(error){
    msg.innerHTML=message(error.message);
    return;
  }

  await refreshSession();
  showHome();
}


/* =========================================================
   REGISTRO
   ========================================================= */

function showRegister(){

  currentView="register";
  setTitle("Crear cuenta");
  setBack(true);

  screen.innerHTML=`

    <div class="card">
      <div class="cardhead">Nueva cuenta</div>

      <div class="cardbody">

        <label>Nombre de usuario</label>
        <input id="regUsername" maxlength="30">

        <label>Email</label>
        <input id="regEmail" type="email">

        <label>Contraseña</label>
        <input id="regPassword" type="password">

        <button class="blue" onclick="register()">
          Crear cuenta
        </button>

        <div id="registerMsg"></div>

      </div>
    </div>
  `;
}

async function register(){

  const username=document.getElementById("regUsername").value.trim();
  const email=document.getElementById("regEmail").value.trim();
  const password=document.getElementById("regPassword").value;

  const msg=document.getElementById("registerMsg");

  if(username.length < 3){
    msg.innerHTML=message("El nombre debe tener al menos 3 caracteres.");
    return;
  }

  if(password.length < 6){
    msg.innerHTML=message("La contraseña debe tener al menos 6 caracteres.");
    return;
  }

  const {data,error}=await sb.auth.signUp({
    email,
    password,
    options:{
      data:{
        username:username
      },
      emailRedirectTo:window.location.href
    }
  });

  if(error){
    msg.innerHTML=message(error.message);
    return;
  }

  if(data.session){

    currentUser=data.user;

    await ensureProfile();

    msg.innerHTML=message(
      "Cuenta creada correctamente.",
      "success"
    );

    setTimeout(showHome,800);

  }else{

    msg.innerHTML=message(
      "Cuenta creada. Revisa tu email para confirmar la cuenta.",
      "success"
    );
  }
}


/* =========================================================
   LOGOUT
   ========================================================= */

async function logout(){

  await sb.auth.signOut();

  currentUser=null;
  currentProfile=null;

  showHome();
}


/* =========================================================
   PERFIL
   ========================================================= */

async function showProfile(){

  if(!currentUser){
    showLogin();
    return;
  }

  await ensureProfile();

  currentView="profile";
  setTitle("Mi perfil");
  setBack(false);

  const p=currentProfile;

  screen.innerHTML=`

    <div class="profile">

      <img
        id="profileAvatar"
        class="avatar"
        src="${avatar(p?.avatar_url)}"
      >

      <div class="username">
        ${esc(p?.username)}
      </div>

      <div class="bio">
        ${esc(p?.bio || "Sin descripción.")}
      </div>

    </div>

    <div class="card">

      <div class="cardhead">
        Información
      </div>

      <div class="cardbody">

        <b>País</b>
        <div>${esc(p?.country || "No especificado")}</div>
        <br>

        <b>Edad</b>
        <div>${p?.age || "No especificada"}</div>
        <br>

        <b>Web</b>
        <div>${esc(p?.website || "No especificada")}</div>

      </div>

    </div>

    <div class="toolbar">
      <button class="blue" onclick="editProfile()">
        Editar perfil
      </button>

      <button onclick="showUsers()">
        Usuarios
      </button>
    </div>
  `;
}


/* =========================================================
   EDITAR PERFIL
   ========================================================= */

function editProfile(){

  const p=currentProfile;

  screen.innerHTML=`

    <div class="card">

      <div class="cardhead">
        Editar perfil
      </div>

      <div class="cardbody">

        <label>Foto de perfil</label>
        <input
          id="avatarFile"
          type="file"
          accept="image/*"
        >

        <img
          id="previewAvatar"
          class="avatar"
          src="${avatar(p.avatar_url)}"
        >

        <label>Nombre de usuario</label>
        <input
          id="editUsername"
          maxlength="30"
          value="${esc(p.username)}"
        >

        <label>Descripción</label>
        <textarea id="editBio">${esc(p.bio)}</textarea>

        <label>Edad</label>
        <input
          id="editAge"
          type="number"
          min="1"
          max="120"
          value="${p.age || ""}"
        >

        <label>País</label>
        <input
          id="editCountry"
          value="${esc(p.country)}"
        >

        <label>Página web</label>
        <input
          id="editWebsite"
          value="${esc(p.website)}"
          placeholder="https://..."
        >

        <button
          class="blue"
          onclick="saveProfile()"
        >
          Guardar
        </button>

        <div id="profileMsg"></div>

      </div>
    </div>
  `;

  document.getElementById("avatarFile")
    .addEventListener("change",function(){

      const file=this.files[0];

      if(!file)return;

      document.getElementById("previewAvatar").src=
        URL.createObjectURL(file);
    });
}


/* =========================================================
   GUARDAR PERFIL + FOTO
   ========================================================= */

async function saveProfile(){

  const msg=document.getElementById("profileMsg");

  const username=
    document.getElementById("editUsername").value.trim();

  const bio=
    document.getElementById("editBio").value.trim();

  const age=
    document.getElementById("editAge").value;

  const country=
    document.getElementById("editCountry").value.trim();

  const website=
    document.getElementById("editWebsite").value.trim();

  const file=
    document.getElementById("avatarFile").files[0];

  if(!username){
    msg.innerHTML=message("Necesitas un nombre de usuario.");
    return;
  }

  let avatar_url=currentProfile.avatar_url || "";

  if(file){

    const extension=
      file.name.split(".").pop().toLowerCase();

    const path=
      `${currentUser.id}/${crypto.randomUUID()}.${extension}`;

    const {error:uploadError}=await sb.storage
      .from("avatars")
      .upload(path,file,{
        upsert:true,
        contentType:file.type
      });

    if(uploadError){
      msg.innerHTML=message(
        "No se pudo subir la foto: " +
        uploadError.message
      );
      return;
    }

    const {data:urlData}=sb.storage
      .from("avatars")
      .getPublicUrl(path);

    avatar_url=urlData.publicUrl;
  }

  const {data,error}=await sb
    .from("profiles")
    .update({
      username,
      bio,
      age:age ? Number(age) : null,
      country,
      website,
      avatar_url
    })
    .eq("id",currentUser.id)
    .select()
    .single();

  if(error){
    msg.innerHTML=message(error.message);
    return;
  }

  currentProfile=data;

  msg.innerHTML=message(
    "Perfil actualizado.",
    "success"
  );

  setTimeout(showProfile,700);
}


/* =========================================================
   USUARIOS
   ========================================================= */

async function showUsers(){

  currentView="users";
  setTitle("Usuarios");
  setBack(true);

  screen.innerHTML=
    `<div class="center">Cargando usuarios...</div>`;

  const {data,error}=await sb
    .from("profiles")
    .select("id,username,bio,avatar_url")
    .order("username");

  if(error){
    screen.innerHTML=message(error.message);
    return;
  }

  if(!data.length){
    screen.innerHTML=
      `<div class="center">Todavía no hay usuarios.</div>`;
    return;
  }

  screen.innerHTML=`

    <div class="list">

      ${data.map(user=>`

        <div class="row"
             onclick="viewUser('${user.id}')">

          <img
            class="avatar smallAvatar"
            src="${avatar(user.avatar_url)}"
          >

          <div>
            <b>${esc(user.username)}</b>
            <div class="small">
              ${esc(user.bio || "Sin descripción")}
            </div>
          </div>

          <div class="arrow">›</div>

        </div>

      `).join("")}

    </div>
  `;
}


async function viewUser(id){

  setTitle("Perfil");
  setBack(true);

  screen.innerHTML=
    `<div class="center">Cargando perfil...</div>`;

  const {data,error}=await sb
    .from("profiles")
    .select("*")
    .eq("id",id)
    .single();

  if(error){
    screen.innerHTML=message(error.message);
    return;
  }

  screen.innerHTML=`

    <div class="profile">

      <img
        class="avatar"
        src="${avatar(data.avatar_url)}"
      >

      <div class="username">
        ${esc(data.username)}
      </div>

      <div class="bio">
        ${esc(data.bio || "Sin descripción.")}
      </div>

    </div>

    <div class="card">

      <div class="cardhead">Información</div>

      <div class="cardbody">

        <b>País</b>
        <div>${esc(data.country || "No especificado")}</div>

        <br>

        <b>Edad</b>
        <div>${data.age || "No especificada"}</div>

        <br>

        ${
          data.website
          ? `<b>Web</b><br>
             <a href="${esc(data.website)}"
                target="_blank">
                ${esc(data.website)}
             </a>`
          : ""
        }

      </div>

    </div>

    ${
      currentUser && currentUser.id !== id
      ? `<div class="toolbar">
          <button class="blue"
                  onclick="startMessage('${id}')">
            💬 Enviar mensaje
          </button>
         </div>`
      : ""
    }
  `;
}


/* =========================================================
   FOROS
   ========================================================= */

async function showForums(){

  currentView="forums";
  setTitle("Foros");
  setBack(false);

  navAction.classList.remove("hidden");
  navAction.textContent="+";
  navAction.onclick=showCreateForum;

  screen.innerHTML=
    `<div class="center">Cargando foros...</div>`;

  const {data,error}=await sb
    .from("topics")
    .select(`
      id,
      category,
      title,
      body,
      user_id,
      created_at,
      profiles(
        username,
        avatar_url
      )
    `)
    .order("created_at",{ascending:false});

  if(error){
    screen.innerHTML=message(error.message);
    return;
  }

  if(!data.length){

    screen.innerHTML=`

      <div class="center">

        <div style="font-size:55px">🗂️</div>

        <h2>No hay foros todavía</h2>

        <p class="muted">
          Sé el primero en crear un foro.
        </p>

        ${
          currentUser
          ? `<button class="blue"
                    onclick="showCreateForum()">
               Crear foro
             </button>`
          : `<button class="blue"
                    onclick="showLogin()">
               Iniciar sesión
             </button>`
        }

      </div>
    `;

    return;
  }

  screen.innerHTML=`

    <div class="list">

      ${data.map(topic=>`

        <div class="row"
             onclick="openForum(${topic.id})">

          <img
            class="avatar smallAvatar"
            src="${avatar(topic.profiles?.avatar_url)}"
          >

          <div>

            <b>${esc(topic.title)}</b>

            <div class="small">
              ${esc(topic.category)}
              ·
              ${esc(topic.profiles?.username || "Usuario")}
            </div>

          </div>

          <div class="arrow">›</div>

        </div>

      `).join("")}

    </div>
  `;
}


/* =========================================================
   CREAR FORO
   ========================================================= */

function showCreateForum(){

  if(!currentUser){
    showLogin();
    return;
  }

  currentView="createForum";
  setTitle("Nuevo foro");
  setBack(true);

  navAction.classList.add("hidden");

  screen.innerHTML=`

    <div class="card">

      <div class="cardhead">
        Crear un foro
      </div>

      <div class="cardbody">

        <label>Categoría</label>

        <select id="forumCategory">

          <option>Música</option>
          <option>Juegos</option>
          <option>Apps</option>
          <option>Off-topic</option>

        </select>

        <label>Título</label>

        <input
          id="forumTitle"
          maxlength="120"
          placeholder="Título del foro"
        >

        <label>Contenido</label>

        <textarea
          id="forumBody"
          maxlength="10000"
          placeholder="Escribe algo..."
        ></textarea>

        <button
          class="blue"
          onclick="createForum()">
          Publicar foro
        </button>

        <div id="forumMsg"></div>

      </div>

    </div>
  `;
}


async function createForum(){

  const category=
    document.getElementById("forumCategory").value;

  const title=
    document.getElementById("forumTitle").value.trim();

  const body=
    document.getElementById("forumBody").value.trim();

  const msg=document.getElementById("forumMsg");

  if(!title || !body){
    msg.innerHTML=
      message("Escribe un título y contenido.");
    return;
  }

  const {data,error}=await sb
    .from("topics")
    .insert({
      category,
      title,
      body,
      user_id:currentUser.id
    })
    .select()
    .single();

  if(error){
    msg.innerHTML=message(error.message);
    return;
  }

  openForum(data.id);
}


/* =========================================================
   ABRIR FORO
   ========================================================= */

async function openForum(id){

  currentView="forum";
  setTitle("Foro");
  setBack(true);
  navAction.classList.add("hidden");

  screen.innerHTML=
    `<div class="center">Cargando...</div>`;

  const {data:topic,error:topicError}=await sb
    .from("topics")
    .select(`
      *,
      profiles(
        username,
        avatar_url
      )
    `)
    .eq("id",id)
    .single();

  if(topicError){
    screen.innerHTML=message(topicError.message);
    return;
  }

  const {data:replies,error:replyError}=await sb
    .from("replies")
    .select(`
      *,
      profiles(
        username,
        avatar_url
      )
    `)
    .eq("topic_id",id)
    .order("created_at");

  if(replyError){
    screen.innerHTML=message(replyError.message);
    return;
  }

  screen.innerHTML=`

    <div class="card">

      <div class="cardbody">

        <div class="topicTitle">
          ${esc(topic.title)}
        </div>

        <div class="small">
          ${esc(topic.category)}
        </div>

        <br>

        <div class="postUser">

          <img
            class="avatar smallAvatar"
            src="${avatar(topic.profiles?.avatar_url)}"
          >

          <b>
            ${esc(topic.profiles?.username || "Usuario")}
          </b>

        </div>

        <div style="white-space:pre-wrap">
          ${esc(topic.body)}
        </div>

      </div>

    </div>

    <div class="card">

      <div class="cardhead">
        Respuestas (${replies.length})
      </div>

      ${
        replies.length
        ? replies.map(reply=>`

          <div class="post">

            <div class="postUser">

              <img
                class="avatar smallAvatar"
                src="${avatar(reply.profiles?.avatar_url)}"
              >

              <b>
                ${esc(reply.profiles?.username || "Usuario")}
              </b>

            </div>

            <div style="white-space:pre-wrap">
              ${esc(reply.body)}
            </div>

          </div>

        `).join("")
        : `<div class="center muted">
             Todavía no hay respuestas.
           </div>`
      }

    </div>

    ${
      currentUser
      ? `
        <div class="card">

          <div class="cardhead">
            Responder
          </div>

          <div class="cardbody">

            <textarea
              id="replyBody"
              placeholder="Escribe tu respuesta..."
            ></textarea>

            <button
              class="blue"
              onclick="sendReply(${id})">
              Publicar respuesta
            </button>

            <div id="replyMsg"></div>

          </div>

        </div>
      `
      : `
        <div class="center">
          <button
            class="blue"
            onclick="showLogin()">
            Inicia sesión para responder
          </button>
        </div>
      `
    }
  `;
}


async function sendReply(topicId){

  const body=
    document.getElementById("replyBody").value.trim();

  const msg=document.getElementById("replyMsg");

  if(!body){
    msg.innerHTML=message("Escribe una respuesta.");
    return;
  }

  const {error}=await sb
    .from("replies")
    .insert({
      topic_id:topicId,
      body,
      user_id:currentUser.id
    });

  if(error){
    msg.innerHTML=message(error.message);
    return;
  }

  openForum(topicId);
}


/* =========================================================
   MENSAJES PRIVADOS
   ========================================================= */

async function showMessages(){

  if(!currentUser){
    showLogin();
    return;
  }

  currentView="messages";
  setTitle("Mensajes");
  setBack(false);

  navAction.classList.remove("hidden");
  navAction.textContent="+";
  navAction.onclick=showNewMessage;

  screen.innerHTML=
    `<div class="center">Cargando mensajes...</div>`;

  /*
    Esta consulta usa la tabla messages.
    Debes crearla en Supabase con el SQL indicado
    después del código.
  */

  const {data,error}=await sb
    .from("messages")
    .select(`
      id,
      sender_id,
      receiver_id,
      body,
      created_at,
      sender:profiles!messages_sender_id_fkey(
        username,
        avatar_url
      ),
      receiver:profiles!messages_receiver_id_fkey(
        username,
        avatar_url
      )
    `)
    .or(
      `sender_id.eq.${currentUser.id},receiver_id.eq.${currentUser.id}`
    )
    .order("created_at",{ascending:false});

  if(error){
    screen.innerHTML=message(
      "No se pudieron cargar los mensajes. " +
      error.message
    );
    return;
  }

  if(!data.length){

    screen.innerHTML=`

      <div class="center">

        <div style="font-size:55px">💬</div>

        <h2>No tienes mensajes</h2>

        <button
          class="blue"
          onclick="showNewMessage()">
          Nuevo mensaje
        </button>

      </div>

    `;

    return;
  }

  const users={};

  data.forEach(m=>{

    const other=
      m.sender_id===currentUser.id
      ? m.receiver
      : m.sender;

    const id=
      m.sender_id===currentUser.id
      ? m.receiver_id
      : m.sender_id;

    if(!users[id]){
      users[id]={
        id,
        username:other?.username || "Usuario",
        avatar_url:other?.avatar_url || "",
        body:m.body,
        date:m.created_at
      };
    }

  });

  screen.innerHTML=`

    <div class="list">

      ${Object.values(users).map(u=>`

        <div class="row"
             onclick="openConversation('${u.id}')">

          <img
            class="avatar smallAvatar"
            src="${avatar(u.avatar_url)}"
          >

          <div>

            <b>${esc(u.username)}</b>

            <div class="small">
              ${esc(u.body.slice(0,60))}
            </div>

          </div>

          <div class="arrow">›</div>

        </div>

      `).join("")}

    </div>
  `;
}


/* =========================================================
   NUEVO MENSAJE
   ========================================================= */

function showNewMessage(){

  if(!currentUser){
    showLogin();
    return;
  }

  currentView="newMessage";
  setTitle("Nuevo mensaje");
  setBack(true);

  screen.innerHTML=`

    <div class="card">

      <div class="cardhead">
        Enviar mensaje
      </div>

      <div class="cardbody">

        <label>Usuario</label>

        <input
          id="messageUser"
          placeholder="Nombre de usuario"
        >

        <label>Mensaje</label>

        <textarea
          id="messageBody"
          placeholder="Escribe tu mensaje..."
        ></textarea>

        <button
          class="blue"
          onclick="sendNewMessage()">
          Enviar
        </button>

        <div id="messageMsg"></div>

      </div>

    </div>
  `;
}


async function startMessage(userId){

  if(!currentUser){
    showLogin();
    return;
  }

  showNewMessage();

  const {data}=await sb
    .from("profiles")
    .select("username")
    .eq("id",userId)
    .single();

  if(data){
    document.getElementById("messageUser").value=
      data.username;
  }
}


async function sendNewMessage(){

  const username=
    document.getElementById("messageUser").value.trim();

  const body=
    document.getElementById("messageBody").value.trim();

  const msg=document.getElementById("messageMsg");

  if(!username || !body){
    msg.innerHTML=message("Completa todos los campos.");
    return;
  }

  const {data:user,error:userError}=await sb
    .from("profiles")
    .select("id")
    .eq("username",username)
    .single();

  if(userError || !user){
    msg.innerHTML=
      message("No existe ese usuario.");
    return;
  }

  if(user.id===currentUser.id){
    msg.innerHTML=
      message("No puedes enviarte un mensaje a ti mismo.");
    return;
  }

  const {error}=await sb
    .from("messages")
    .insert({
      sender_id:currentUser.id,
      receiver_id:user.id,
      body
    });

  if(error){
    msg.innerHTML=message(error.message);
    return;
  }

  openConversation(user.id);
}


/* =========================================================
   CONVERSACIÓN
   ========================================================= */

async function openConversation(userId){

  currentView="conversation";
  setTitle("Mensajes");
  setBack(true);

  const {data:user}=await sb
    .from("profiles")
    .select("*")
    .eq("id",userId)
    .single();

  const {data,error}=await sb
    .from("messages")
    .select("*")
    .or(
      `and(sender_id.eq.${currentUser.id},receiver_id.eq.${userId}),and(sender_id.eq.${userId},receiver_id.eq.${currentUser.id})`
    )
    .order("created_at");

  if(error){
    screen.innerHTML=message(error.message);
    return;
  }

  screen.innerHTML=`

    <div class="profile" style="padding:12px">

      <img
        class="avatar smallAvatar"
        src="${avatar(user?.avatar_url)}"
      >

      <div class="username" style="font-size:17px">
        ${esc(user?.username)}
      </div>

    </div>

    <div class="card">

      ${
        data.length
        ? data.map(m=>`

          <div class="message ${
            m.sender_id===currentUser.id
            ? "me"
            : ""
          }">

            <b>
              ${
                m.sender_id===currentUser.id
                ? "Tú"
                : esc(user?.username)
              }
            </b>

            <div style="white-space:pre-wrap">
              ${esc(m.body)}
            </div>

          </div>

        `).join("")
        : `<div class="center muted">
             No hay mensajes todavía.
           </div>`
      }

    </div>

    <div class="card">

      <div class="cardbody">

        <textarea
          id="conversationBody"
          placeholder="Escribe un mensaje..."
        ></textarea>

        <button
          class="blue"
          onclick="sendConversationMessage('${userId}')">
          Enviar
        </button>

      </div>

    </div>
  `;
}


async function sendConversationMessage(userId){

  const body=
    document.getElementById("conversationBody")
      .value.trim();

  if(!body)return;

  const {error}=await sb
    .from("messages")
    .insert({
      sender_id:currentUser.id,
      receiver_id:userId,
      body
    });

  if(error){
    alert(error.message);
    return;
  }

  openConversation(userId);
}


/* =========================================================
   NAVEGACIÓN
   ========================================================= */

function goBack(){

  if(currentView==="login" ||
     currentView==="register" ||
     currentView==="profile" ||
     currentView==="users"){
    showHome();
    return;
  }

  if(currentView==="createForum"){
    showForums();
    return;
  }

  if(currentView==="forum"){
    showForums();
    return;
  }

  if(currentView==="newMessage"){
    showMessages();
    return;
  }

  if(currentView==="conversation"){
    showMessages();
    return;
  }

  showHome();
}


/* =========================================================
   SESIÓN SUPABASE
   ========================================================= */

async function refreshSession(){

  const {data}=await sb.auth.getSession();

  currentUser=data.session?.user || null;

  if(currentUser){
    await ensureProfile();
  }else{
    currentProfile=null;
  }
}

sb.auth.onAuthStateChange(async(event,session)=>{

  currentUser=session?.user || null;

  if(currentUser){
    await ensureProfile();
  }else{
    currentProfile=null;
  }

});


/* =========================================================
   INICIO
   ========================================================= */

(async()=>{

  await refreshSession();

  showHome();

})();


/* =========================================================
   ACTUALIZACIÓN EN TIEMPO REAL
   ========================================================= */

sb.channel("forum-realtime")
  .on(
    "postgres_changes",
    {
      event:"*",
      schema:"public",
      table:"topics"
    },
    ()=>{
      if(currentView==="forums"){
        showForums();
      }
    }
  )
  .on(
    "postgres_changes",
    {
      event:"*",
      schema:"public",
      table:"replies"
    },
    ()=>{
      if(currentView==="forum"){
        /*
          La página se actualizará cuando vuelva
          a abrir el foro.
        */
      }
    }
  )
  .subscribe();

</script>

</body>
</html>
