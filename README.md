<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">

<title>iPod Community</title>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
/* =========================================================
   iOS 6 / iPod touch inspired UI
   ========================================================= */

*{
  box-sizing:border-box;
  -webkit-tap-highlight-color:transparent;
}

html,body{
  margin:0;
  min-height:100%;
  font-family:
    "Helvetica Neue",
    Helvetica,
    Arial,
    sans-serif;
  color:#222;
}

body{
  background:
    repeating-linear-gradient(
      0deg,
      #d9d9d9 0px,
      #d9d9d9 1px,
      #d2d2d2 1px,
      #d2d2d2 2px
    );
}

/* DEVICE */

#device{
  width:100%;
  max-width:430px;
  min-height:100vh;
  margin:auto;
  background:#cfd2d5;
  position:relative;
  overflow:hidden;
  box-shadow:
    0 0 35px rgba(0,0,0,.45),
    inset 0 0 20px rgba(255,255,255,.5);
}

/* STATUS BAR */

.statusbar{
  height:20px;
  background:
    linear-gradient(
      #4b4b4b,
      #111
    );
  color:white;
  font-size:11px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:0 7px;
  text-shadow:0 -1px #000;
}

.status-left{
  font-weight:bold;
}

.status-right{
  display:flex;
  gap:7px;
}

/* NAVIGATION BAR */

.navbar{
  height:45px;
  position:relative;
  z-index:20;

  background:
    linear-gradient(
      #f8f8f8 0%,
      #e9e9e9 48%,
      #c8c8c8 52%,
      #dedede 100%
    );

  border-top:1px solid #fff;
  border-bottom:1px solid #777;

  box-shadow:
    inset 0 1px rgba(255,255,255,.9),
    0 1px 2px rgba(0,0,0,.35);

  display:flex;
  align-items:center;
  justify-content:center;
}

.nav-title{
  font-size:20px;
  font-weight:bold;
  color:#222;
  text-shadow:
    0 1px #fff,
    0 -1px rgba(0,0,0,.15);
}

.nav-button{
  position:absolute;
  top:7px;
  height:31px;
  padding:0 10px;

  color:#fff;
  font-size:13px;
  font-weight:bold;

  border:1px solid #333;
  border-radius:5px;

  background:
    linear-gradient(
      #777,
      #444 48%,
      #222 52%,
      #555
    );

  box-shadow:
    inset 0 1px rgba(255,255,255,.4),
    0 1px 1px rgba(0,0,0,.5);

  text-shadow:0 -1px #000;
}

.nav-button:active{
  background:linear-gradient(#222,#555);
}

.nav-left{
  left:6px;
}

.nav-right{
  right:6px;
}

/* CONTENT */

#screen{
  min-height:calc(100vh - 116px);
  padding-bottom:65px;

  background:
    linear-gradient(
      rgba(255,255,255,.45),
      rgba(255,255,255,.45)
    ),
    repeating-linear-gradient(
      45deg,
      #d8d8d8 0px,
      #d8d8d8 2px,
      #d2d2d2 2px,
      #d2d2d2 4px
    );
}

/* HOME HEADER */

.home-header{
  text-align:center;
  padding:25px 15px 20px;

  background:
    linear-gradient(
      #eeeeee,
      #d0d0d0
    );

  border-bottom:1px solid #999;

  box-shadow:
    inset 0 1px white;
}

.ipod-icon{
  width:86px;
  height:86px;
  margin:auto;

  border-radius:18px;

  background:
    linear-gradient(
      145deg,
      #f8f8f8,
      #aaa
    );

  border:2px solid #777;

  box-shadow:
    inset 0 2px white,
    0 2px 5px rgba(0,0,0,.5);

  display:flex;
  align-items:center;
  justify-content:center;

  font-size:43px;
}

.home-title{
  font-size:25px;
  font-weight:bold;
  margin-top:12px;
  text-shadow:0 1px white;
}

.home-subtitle{
  color:#555;
  font-size:13px;
  margin-top:4px;
}

/* LISTS */

.list{
  background:#fff;
  border-top:1px solid #aaa;
  border-bottom:1px solid #888;

  box-shadow:
    0 1px 2px rgba(0,0,0,.2);
}

.list-title{
  padding:6px 12px;

  font-size:12px;
  font-weight:bold;
  color:#555;
  text-shadow:0 1px white;

  background:
    linear-gradient(
      #eeeeee,
      #c7c7c7
    );

  border-top:1px solid white;
  border-bottom:1px solid #999;
}

.row{
  min-height:57px;
  display:flex;
  align-items:center;
  gap:11px;

  padding:7px 12px;

  background:
    linear-gradient(
      #fff,
      #f2f2f2
    );

  border-bottom:1px solid #c8c8c8;

  position:relative;
}

.row:last-child{
  border-bottom:0;
}

.row:active{
  background:#d9d9d9;
}

.row-icon{
  width:40px;
  height:40px;

  flex:none;

  border-radius:9px;

  display:flex;
  align-items:center;
  justify-content:center;

  font-size:23px;

  background:
    linear-gradient(
      #fafafa,
      #aaa
    );

  border:1px solid #777;

  box-shadow:
    inset 0 1px white,
    0 1px 2px rgba(0,0,0,.4);
}

.row-content{
  min-width:0;
  flex:1;
}

.row-title{
  font-size:16px;
  font-weight:bold;
  color:#222;
}

.row-subtitle{
  margin-top:2px;
  font-size:12px;
  color:#777;
  white-space:nowrap;
  overflow:hidden;
  text-overflow:ellipsis;
}

.chevron{
  color:#999;
  font-size:27px;
  font-weight:normal;
}

/* BUTTON */

.ios-button{
  height:36px;
  padding:0 14px;

  border-radius:6px;

  border:1px solid #315d8b;

  background:
    linear-gradient(
      #75b9ed,
      #3c82bd 48%,
      #21659c 52%,
      #4b91c8
    );

  color:white;

  font-size:14px;
  font-weight:bold;

  text-shadow:
    0 -1px #24557c;

  box-shadow:
    inset 0 1px rgba(255,255,255,.7),
    0 1px 2px rgba(0,0,0,.45);
}

.ios-button:active{
  background:
    linear-gradient(
      #21659c,
      #75b9ed
    );
}

.gray-button{
  border-color:#777;
  color:#222;
  text-shadow:0 1px white;

  background:
    linear-gradient(
      #fff,
      #d2d2d2
    );
}

/* PANELS */

.panel{
  margin:12px;

  background:#fff;

  border:1px solid #999;
  border-radius:7px;

  box-shadow:
    0 1px 3px rgba(0,0,0,.35);

  overflow:hidden;
}

.panel-title{
  padding:9px 11px;

  font-size:15px;
  font-weight:bold;

  background:
    linear-gradient(
      #f9f9f9,
      #d0d0d0
    );

  border-bottom:1px solid #aaa;

  text-shadow:0 1px white;
}

.panel-body{
  padding:12px;
}

/* FORUM */

.forum-post{
  background:white;
  border-bottom:1px solid #bbb;
  padding:12px;
}

.forum-user{
  display:flex;
  align-items:center;
  gap:9px;
  margin-bottom:9px;
}

.forum-user-name{
  font-weight:bold;
  color:#222;
}

.forum-body{
  font-size:15px;
  line-height:1.45;
  white-space:pre-wrap;
  word-break:break-word;
}

.forum-meta{
  font-size:11px;
  color:#888;
  margin-top:5px;
}

/* AVATAR */

.avatar{
  width:82px;
  height:82px;

  border-radius:17px;

  object-fit:cover;

  background:#aaa;

  border:2px solid white;

  box-shadow:
    0 1px 4px rgba(0,0,0,.5);
}

.avatar-small{
  width:43px;
  height:43px;
  border-radius:9px;
}

/* PROFILE */

.profile-header{
  text-align:center;
  padding:22px 15px;

  background:
    linear-gradient(
      #f4f4f4,
      #cfcfcf
    );

  border-bottom:1px solid #999;

  box-shadow:
    inset 0 1px white;
}

.profile-name{
  margin-top:9px;
  font-size:22px;
  font-weight:bold;
  text-shadow:0 1px white;
}

.profile-bio{
  margin:5px auto 0;
  max-width:340px;
  font-size:13px;
  color:#555;
  white-space:pre-wrap;
}

/* FORMS */

.form{
  padding:12px;
}

label{
  display:block;
  margin:7px 2px 4px;

  font-size:13px;
  font-weight:bold;
  color:#444;

  text-shadow:0 1px white;
}

input,
textarea,
select{
  width:100%;

  border:1px solid #888;
  border-radius:5px;

  background:#fff;

  padding:9px;

  font-family:inherit;
  font-size:15px;

  box-shadow:
    inset 0 1px 3px rgba(0,0,0,.15);
}

textarea{
  min-height:110px;
  resize:vertical;
}

.form-buttons{
  display:flex;
  gap:8px;
  margin-top:12px;
}

.form-buttons button{
  flex:1;
}

/* MESSAGE */

.message{
  padding:10px 12px;
  border-bottom:1px solid #ccc;
  background:#fff;
}

.message.me{
  background:#e5f1fc;
}

.message-name{
  font-size:13px;
  font-weight:bold;
}

.message-body{
  margin-top:3px;
  font-size:14px;
  white-space:pre-wrap;
  word-break:break-word;
}

/* EMPTY */

.empty{
  text-align:center;
  padding:45px 20px;
  color:#666;
}

.empty-icon{
  font-size:55px;
  margin-bottom:8px;
}

.empty-title{
  font-size:19px;
  font-weight:bold;
  color:#444;
}

/* ALERTS */

.alert{
  margin:10px;
  padding:10px;

  border-radius:6px;

  border:1px solid #999;

  background:#eee;

  font-size:13px;
}

.alert.error{
  background:#ffe0e0;
  border-color:#cc8888;
  color:#8b0000;
}

.alert.success{
  background:#e2f6e2;
  border-color:#8ab58a;
  color:#275d27;
}

/* BOTTOM TAB BAR */

.tabbar{
  position:fixed;
  bottom:0;

  width:100%;
  max-width:430px;

  height:51px;

  z-index:50;

  display:flex;

  background:
    linear-gradient(
      #505050,
      #252525
    );

  border-top:1px solid #111;

  box-shadow:
    0 -1px 4px rgba(0,0,0,.5);
}

.tab{
  flex:1;

  color:#ddd;

  border:0;
  border-radius:0;

  background:transparent;

  font-size:10px;
  font-weight:bold;

  text-shadow:0 -1px black;
}

.tab-icon{
  font-size:21px;
  display:block;
  line-height:22px;
}

.tab.active{
  color:#fff;
}

.hidden{
  display:none!important;
}

.center{
  text-align:center;
}

.spacer{
  height:10px;
}

.small-text{
  font-size:12px;
  color:#777;
}

hr{
  border:0;
  border-top:1px solid #ccc;
}

/* IOS STYLE SECTION HEADER */

.section-header{
  padding:5px 12px;

  font-size:12px;
  font-weight:bold;

  color:#555;

  background:
    linear-gradient(
      #e9e9e9,
      #c8c8c8
    );

  border-top:1px solid white;
  border-bottom:1px solid #999;

  text-shadow:0 1px white;
}
</style>
</head>

<body>

<div id="device">

  <div class="statusbar">
    <div class="status-left">iPod</div>
    <div class="status-right">
      <span>Wi-Fi</span>
      <span>▰</span>
      <span>100%</span>
    </div>
  </div>

  <div class="navbar">

    <button
      id="backButton"
      class="nav-button nav-left hidden"
      onclick="goBack()">
      ‹ Atrás
    </button>

    <div
      id="navTitle"
      class="nav-title">
      iPod Community
    </div>

    <button
      id="navAction"
      class="nav-button nav-right hidden">
    </button>

  </div>

  <main id="screen"></main>

  <div class="tabbar">

    <button
      id="tabHome"
      class="tab active"
      onclick="showHome()">
      <span class="tab-icon">⌂</span>
      Inicio
    </button>

    <button
      id="tabForums"
      class="tab"
      onclick="showForums()">
      <span class="tab-icon">▤</span>
      Foros
    </button>

    <button
      id="tabMessages"
      class="tab"
      onclick="showMessages()">
      <span class="tab-icon">●</span>
      Mensajes
    </button>

    <button
      id="tabProfile"
      class="tab"
      onclick="showProfile()">
      <span class="tab-icon">●</span>
      Perfil
    </button>

  </div>

</div>


<script>
/* =========================================================
   SUPABASE
   ========================================================= */

const SUPABASE_URL =
  "TU_SUPABASE_URL";

const SUPABASE_KEY =
  "TU_SUPABASE_PUBLISHABLE_KEY";

const db =
  window.supabase.createClient(
    SUPABASE_URL,
    SUPABASE_KEY
  );


/* =========================================================
   STATE
   ========================================================= */

let currentUser = null;
let currentProfile = null;
let currentPage = "home";
let previousPage = "home";

const screen =
  document.getElementById("screen");

const navTitle =
  document.getElementById("navTitle");

const backButton =
  document.getElementById("backButton");

const navAction =
  document.getElementById("navAction");


/* =========================================================
   HELPERS
   ========================================================= */

function esc(value){

  if(value === null || value === undefined)
    return "";

  return String(value)
    .replaceAll("&","&amp;")
    .replaceAll("<","&lt;")
    .replaceAll(">","&gt;")
    .replaceAll('"',"&quot;")
    .replaceAll("'","&#039;");
}


function defaultAvatar(){

  return "data:image/svg+xml," +
    encodeURIComponent(`
      <svg xmlns="http://www.w3.org/2000/svg"
           width="200"
           height="200"
           viewBox="0 0 200 200">

        <defs>
          <linearGradient id="g"
                          x1="0"
                          y1="0"
                          x2="0"
                          y2="1">
            <stop offset="0"
                  stop-color="#eee"/>
            <stop offset="1"
                  stop-color="#aaa"/>
          </linearGradient>
        </defs>

        <rect width="200"
              height="200"
              rx="35"
              fill="url(#g)"/>

        <circle
          cx="100"
          cy="72"
          r="38"
          fill="#777"/>

        <path
          d="M35 190
             C40 140 65 120 100 120
             C135 120 160 140 165 190Z"
          fill="#777"/>

      </svg>
    `);
}


function getAvatar(url){
  return url || defaultAvatar();
}


function setTitle(title){
  navTitle.textContent = title;
}


function setBack(value){

  backButton.classList.toggle(
    "hidden",
    !value
  );
}


function setAction(text,fn){

  if(!text){

    navAction.classList.add("hidden");
    return;
  }

  navAction.classList.remove("hidden");
  navAction.textContent=text;
  navAction.onclick=fn;
}


function alertBox(text,type="error"){

  return `
    <div class="alert ${type}">
      ${esc(text)}
    </div>
  `;
}


function setTab(active){

  document.querySelectorAll(".tab")
    .forEach(t=>t.classList.remove("active"));

  const el =
    document.getElementById("tab"+active);

  if(el) el.classList.add("active");
}


/* =========================================================
   SESSION
   ========================================================= */

async function loadSession(){

  const {data,error} =
    await db.auth.getSession();

  if(error){
    console.error(error);
    return;
  }

  currentUser =
    data.session?.user || null;

  if(currentUser){

    await ensureProfile();

  }else{

    currentProfile=null;
  }
}


async function ensureProfile(){

  if(!currentUser)
    return null;

  const {data,error} =
    await db
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
   * Crea el perfil automáticamente
   * después de iniciar sesión.
   */

  const username =
    currentUser.user_metadata?.username ||
    "Usuario" +
    currentUser.id.slice(0,6);


  const {data:newProfile,error:createError} =
    await db
      .from("profiles")
      .insert({

        id:currentUser.id,

        username,

        bio:"",

        age:null,

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


db.auth.onAuthStateChange(
  async(event,session)=>{

    currentUser =
      session?.user || null;

    if(currentUser){

      setTimeout(
        ()=>ensureProfile(),
        0
      );

    }else{

      currentProfile=null;
    }
  }
);


/* =========================================================
   HOME
   ========================================================= */

async function showHome(){

  previousPage=currentPage;
  currentPage="home";

  setTitle("iPod Community");
  setBack(false);
  setAction(null);
  setTab("Home");

  const account =
    currentUser
      ? `
        <b>
          ${esc(
            currentProfile?.username ||
            "Usuario"
          )}
        </b>

        <div class="small-text">
          Sesión iniciada
        </div>
      `
      : `
        <b>Visitante</b>

        <div class="small-text">
          No has iniciado sesión
        </div>
      `;


  screen.innerHTML=`

    <div class="home-header">

      <div class="ipod-icon">
        ♪
      </div>

      <div class="home-title">
        iPod Community
      </div>

      <div class="home-subtitle">
        Tu comunidad con estilo clásico.
      </div>

    </div>


    <div class="section-header">
      CUENTA
    </div>

    <div class="list">

      <div class="row"
           onclick="${
             currentUser
               ? "showProfile()"
               : "showLogin()"
           }">

        <div class="row-icon">
          ${
            currentUser
              ? "👤"
              : "🔐"
          }
        </div>

        <div class="row-content">

          <div class="row-title">
            ${currentUser
              ? "Mi perfil"
              : "Iniciar sesión"}
          </div>

          <div class="row-subtitle">
            ${account}
          </div>

        </div>

        <div class="chevron">›</div>

      </div>

    </div>


    <div class="section-header">
      COMUNIDAD
    </div>

    <div class="list">

      <div class="row"
           onclick="showForums()">

        <div class="row-icon">
          🗂
        </div>

        <div class="row-content">

          <div class="row-title">
            Foros
          </div>

          <div class="row-subtitle">
            Crea y participa en conversaciones
          </div>

        </div>

        <div class="chevron">›</div>

      </div>


      <div class="row"
           onclick="showMessages()">

        <div class="row-icon">
          💬
        </div>

        <div class="row-content">

          <div class="row-title">
            Mensajes
          </div>

          <div class="row-subtitle">
            Envía mensajes privados
          </div>

        </div>

        <div class="chevron">›</div>

      </div>


      <div class="row"
           onclick="showUsers()">

        <div class="row-icon">
          👥
        </div>

        <div class="row-content">

          <div class="row-title">
            Usuarios
          </div>

          <div class="row-subtitle">
            Conoce a otros miembros
          </div>

        </div>

        <div class="chevron">›</div>

      </div>

    </div>

  `;
}


/* =========================================================
   LOGIN
   ========================================================= */

function showLogin(){

  previousPage=currentPage;
  currentPage="login";

  setTitle("Iniciar sesión");
  setBack(true);
  setAction(null);

  screen.innerHTML=`

    <div class="panel">

      <div class="panel-title">
        Iniciar sesión
      </div>

      <div class="form">

        <label>Email</label>

        <input
          id="loginEmail"
          type="email"
          autocomplete="email"
          placeholder="correo@ejemplo.com">


        <label>Contraseña</label>

        <input
          id="loginPassword"
          type="password"
          autocomplete="current-password"
          placeholder="Contraseña">


        <div class="form-buttons">

          <button
            class="ios-button"
            onclick="login()">
            Entrar
          </button>

          <button
            class="ios-button gray-button"
            onclick="showRegister()">
            Crear cuenta
          </button>

        </div>

        <div id="loginMessage"></div>

      </div>

    </div>

  `;
}


async function login(){

  const email =
    document.getElementById(
      "loginEmail"
    ).value.trim();

  const password =
    document.getElementById(
      "loginPassword"
    ).value;

  const output =
    document.getElementById(
      "loginMessage"
    );


  if(!email || !password){

    output.innerHTML =
      alertBox(
        "Completa todos los campos."
      );

    return;
  }


  const {error} =
    await db.auth.signInWithPassword({
      email,
      password
    });


  if(error){

    output.innerHTML =
      alertBox(error.message);

    return;
  }


  await loadSession();

  showHome();
}


/* =========================================================
   REGISTER
   ========================================================= */

function showRegister(){

  previousPage=currentPage;
  currentPage="register";

  setTitle("Crear cuenta");
  setBack(true);
  setAction(null);

  screen.innerHTML=`

    <div class="panel">

      <div class="panel-title">
        Crear una cuenta
      </div>

      <div class="form">

        <label>
          Nombre de usuario
        </label>

        <input
          id="registerUsername"
          maxlength="30"
          placeholder="Tu nombre">


        <label>Email</label>

        <input
          id="registerEmail"
          type="email"
          autocomplete="email"
          placeholder="correo@ejemplo.com">


        <label>Contraseña</label>

        <input
          id="registerPassword"
          type="password"
          autocomplete="new-password"
          placeholder="Mínimo 6 caracteres">


        <div class="form-buttons">

          <button
            class="ios-button"
            onclick="register()">
            Registrarme
          </button>

          <button
            class="ios-button gray-button"
            onclick="showLogin()">
            Ya tengo cuenta
          </button>

        </div>

        <div id="registerMessage"></div>

      </div>

    </div>

  `;
}


async function register(){

  const username =
    document.getElementById(
      "registerUsername"
    ).value.trim();

  const email =
    document.getElementById(
      "registerEmail"
    ).value.trim();

  const password =
    document.getElementById(
      "registerPassword"
    ).value;

  const output =
    document.getElementById(
      "registerMessage"
    );


  if(username.length < 3){

    output.innerHTML =
      alertBox(
        "El nombre debe tener al menos 3 caracteres."
      );

    return;
  }


  if(password.length < 6){

    output.innerHTML =
      alertBox(
        "La contraseña debe tener al menos 6 caracteres."
      );

    return;
  }


  const {data,error} =
    await db.auth.signUp({

      email,

      password,

      options:{
        data:{
          username
        },

        emailRedirectTo:
          window.location.href
      }

    });


  if(error){

    output.innerHTML =
      alertBox(error.message);

    return;
  }


  /*
   * Si Supabase no exige confirmación
   * del email, tendremos sesión inmediatamente.
   */

  if(data.session){

    currentUser=data.user;

    await ensureProfile();

    output.innerHTML =
      alertBox(
        "Cuenta creada correctamente.",
        "success"
      );

    setTimeout(
      showHome,
      800
    );

  }else{

    output.innerHTML =
      alertBox(
        "Cuenta creada. Revisa tu correo para confirmar la cuenta.",
        "success"
      );
  }
}


/* =========================================================
   LOGOUT
   ========================================================= */

async function logout(){

  await db.auth.signOut();

  currentUser=null;
  currentProfile=null;

  showHome();
}


/* =========================================================
   PROFILE
   ========================================================= */

async function showProfile(){

  if(!currentUser){

    showLogin();
    return;
  }

  await ensureProfile();

  previousPage=currentPage;
  currentPage="profile";

  setTitle("Mi perfil");
  setBack(false);
  setTab("Profile");

  setAction(
    "Editar",
    editProfile
  );


  const p=currentProfile;


  screen.innerHTML=`

    <div class="profile-header">

      <img
        class="avatar"
        src="${getAvatar(p?.avatar_url)}">

      <div class="profile-name">
        ${esc(p?.username)}
      </div>

      <div class="profile-bio">
        ${
          esc(
            p?.bio ||
            "Sin descripción."
          )
        }
      </div>

    </div>


    <div class="section-header">
      INFORMACIÓN
    </div>

    <div class="list">

      <div class="row">

        <div class="row-content">

          <div class="row-title">
            País
          </div>

          <div class="row-subtitle">
            ${esc(
              p?.country ||
              "No especificado"
            )}
          </div>

        </div>

      </div>


      <div class="row">

        <div class="row-content">

          <div class="row-title">
            Edad
          </div>

          <div class="row-subtitle">
            ${
              p?.age ||
              "No especificada"
            }
          </div>

        </div>

      </div>


      <div class="row">

        <div class="row-content">

          <div class="row-title">
            Página web
          </div>

          <div class="row-subtitle">
            ${
              esc(
                p?.website ||
                "No especificada"
              )
            }
          </div>

        </div>

      </div>

    </div>


    <div class="panel">

      <div class="panel-body center">

        <button
          class="ios-button"
          onclick="logout()">
          Cerrar sesión
        </button>

      </div>

    </div>

  `;
}


/* =========================================================
   EDIT PROFILE
   ========================================================= */

function editProfile(){

  if(!currentUser){

    showLogin();
    return;
  }

  currentPage="editProfile";

  setTitle("Editar perfil");
  setBack(true);
  setAction(null);


  const p=currentProfile;


  screen.innerHTML=`

    <div class="panel">

      <div class="panel-title">
        Información personal
      </div>

      <div class="form">

        <label>
          Foto de perfil
        </label>

        <div class="center">

          <img
            id="avatarPreview"
            class="avatar"
            src="${getAvatar(p?.avatar_url)}">

        </div>

        <input
          id="avatarFile"
          type="file"
          accept="image/*">


        <label>
          Nombre de usuario
        </label>

        <input
          id="editUsername"
          maxlength="30"
          value="${esc(p?.username || "")}">


        <label>
          Descripción
        </label>

        <textarea
          id="editBio"
          maxlength="1000">${esc(p?.bio || "")}</textarea>


        <label>
          Edad
        </label>

        <input
          id="editAge"
          type="number"
          min="1"
          max="120"
          value="${p?.age || ""}">


        <label>
          País
        </label>

        <input
          id="editCountry"
          value="${esc(p?.country || "")}">


        <label>
          Página web
        </label>

        <input
          id="editWebsite"
          value="${esc(p?.website || "")}"
          placeholder="https://ejemplo.com">


        <div class="form-buttons">

          <button
            class="ios-button"
            onclick="saveProfile()">
            Guardar
          </button>

          <button
            class="ios-button gray-button"
            onclick="showProfile()">
            Cancelar
          </button>

        </div>

        <div id="profileMessage"></div>

      </div>

    </div>

  `;


  document
    .getElementById("avatarFile")
    .addEventListener(
      "change",
      function(){

        const file=this.files[0];

        if(!file)
          return;

        document
          .getElementById(
            "avatarPreview"
          )
          .src=
          URL.createObjectURL(file);
      }
    );
}


/* =========================================================
   SAVE PROFILE
   ========================================================= */

async function saveProfile(){

  const output =
    document.getElementById(
      "profileMessage"
    );


  const username =
    document.getElementById(
      "editUsername"
    ).value.trim();


  const bio =
    document.getElementById(
      "editBio"
    ).value.trim();


  const age =
    document.getElementById(
      "editAge"
    ).value;


  const country =
    document.getElementById(
      "editCountry"
    ).value.trim();


  const website =
    document.getElementById(
      "editWebsite"
    ).value.trim();


  const file =
    document.getElementById(
      "avatarFile"
    ).files[0];


  if(username.length < 3){

    output.innerHTML =
      alertBox(
        "El nombre debe tener al menos 3 caracteres."
      );

    return;
  }


  let avatarUrl =
    currentProfile?.avatar_url || "";


  /* SUBIR FOTO */

  if(file){

    if(file.size > 5 * 1024 * 1024){

      output.innerHTML =
        alertBox(
          "La foto debe pesar menos de 5 MB."
        );

      return;
    }


    const extension =
      file.name
        .split(".")
        .pop()
        .toLowerCase();


    const path =
      currentUser.id +
      "/" +
      crypto.randomUUID() +
      "." +
      extension;


    const {error:uploadError} =
      await db.storage
        .from("avatars")
        .upload(
          path,
          file,
          {
            contentType:file.type,
            upsert:false
          }
        );


    if(uploadError){

      output.innerHTML =
        alertBox(
          "No se pudo subir la foto: " +
          uploadError.message
        );

      return;
    }


    const {data:urlData} =
      db.storage
        .from("avatars")
        .getPublicUrl(path);


    avatarUrl =
      urlData.publicUrl;
  }


  const {data,error} =
    await db
      .from("profiles")
      .update({

        username,

        bio,

        age:
          age
            ? Number(age)
            : null,

        country,

        website,

        avatar_url:
          avatarUrl

      })
      .eq(
        "id",
        currentUser.id
      )
      .select()
      .single();


  if(error){

    output.innerHTML =
      alertBox(error.message);

    return;
  }


  currentProfile=data;


  output.innerHTML =
    alertBox(
      "Perfil actualizado.",
      "success"
    );


  setTimeout(
    showProfile,
    700
  );
}


/* =========================================================
   USERS
   ========================================================= */

async function showUsers(){

  previousPage=currentPage;
  currentPage="users";

  setTitle("Usuarios");
  setBack(true);
  setAction(null);


  screen.innerHTML=
    `<div class="empty">
       Cargando usuarios...
     </div>`;


  const {data,error} =
    await db
      .from("profiles")
      .select(
        "id,username,bio,avatar_url"
      )
      .order(
        "username",
        {ascending:true}
      );


  if(error){

    screen.innerHTML =
      alertBox(error.message);

    return;
  }


  if(!data.length){

    screen.innerHTML=`

      <div class="empty">

        <div class="empty-icon">
          👥
        </div>

        <div class="empty-title">
          No hay usuarios
        </div>

      </div>

    `;

    return;
  }


  screen.innerHTML=`

    <div class="section-header">
      MIEMBROS
    </div>

    <div class="list">

      ${
        data.map(user=>`

          <div
            class="row"
            onclick="viewUser('${user.id}')">

            <img
              class="avatar avatar-small"
              src="${getAvatar(user.avatar_url)}">

            <div class="row-content">

              <div class="row-title">
                ${esc(user.username)}
              </div>

              <div class="row-subtitle">
                ${
                  esc(
                    user.bio ||
                    "Sin descripción"
                  )
                }
              </div>

            </div>

            <div class="chevron">
              ›
            </div>

          </div>

        `).join("")
      }

    </div>

  `;
}


/* =========================================================
   VIEW USER
   ========================================================= */

async function viewUser(id){

  previousPage=currentPage;
  currentPage="user";

  setTitle("Perfil");
  setBack(true);
  setAction(null);


  screen.innerHTML =
    `<div class="empty">
       Cargando perfil...
     </div>`;


  const {data,error} =
    await db
      .from("profiles")
      .select("*")
      .eq("id",id)
      .single();


  if(error){

    screen.innerHTML =
      alertBox(error.message);

    return;
  }


  screen.innerHTML=`

    <div class="profile-header">

      <img
        class="avatar"
        src="${getAvatar(data.avatar_url)}">

      <div class="profile-name">
        ${esc(data.username)}
      </div>

      <div class="profile-bio">
        ${
          esc(
            data.bio ||
            "Sin descripción."
          )
        }
      </div>

    </div>


    <div class="section-header">
      INFORMACIÓN
    </div>

    <div class="list">

      <div class="row">

        <div class="row-content">

          <div class="row-title">
            País
          </div>

          <div class="row-subtitle">
            ${
              esc(
                data.country ||
                "No especificado"
              )
            }
          </div>

        </div>

      </div>


      <div class="row">

        <div class="row-content">

          <div class="row-title">
            Edad
          </div>

          <div class="row-subtitle">
            ${
              data.age ||
              "No especificada"
            }
          </div>

        </div>

      </div>

    </div>


    ${
      currentUser &&
      currentUser.id !== id
      ?
      `
        <div class="panel">

          <div class="panel-body center">

            <button
              class="ios-button"
              onclick="startMessage('${id}')">
              💬 Enviar mensaje
            </button>

          </div>

        </div>
      `
      :
      ""
    }

  `;
}


/* =========================================================
   FORUM LIST
   ========================================================= */

async function showForums(){

  previousPage=currentPage;
  currentPage="forums";

  setTitle("Foros");
  setBack(false);

  setTab("Forums");

  setAction(
    "+",
    showCreateForum
  );


  screen.innerHTML =
    `<div class="empty">
       Cargando foros...
     </div>`;


  const {data,error} =
    await db
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
      .order(
        "created_at",
        {ascending:false}
      );


  if(error){

    screen.innerHTML =
      alertBox(error.message);

    return;
  }


  if(!data.length){

    screen.innerHTML=`

      <div class="empty">

        <div class="empty-icon">
          🗂
        </div>

        <div class="empty-title">
          No hay foros
        </div>

        <p>
          Todavía nadie ha creado un foro.
        </p>

        ${
          currentUser
          ?
          `
            <button
              class="ios-button"
              onclick="showCreateForum()">
              Crear primer foro
            </button>
          `
          :
          `
            <button
              class="ios-button"
              onclick="showLogin()">
              Iniciar sesión
            </button>
          `
        }

      </div>

    `;

    return;
  }


  screen.innerHTML=`

    <div class="section-header">
      CONVERSACIONES
    </div>

    <div class="list">

      ${
        data.map(topic=>`

          <div
            class="row"
            onclick="openForum(${topic.id})">

            <img
              class="avatar avatar-small"
              src="${getAvatar(
                topic.profiles?.avatar_url
              )}">

            <div class="row-content">

              <div class="row-title">
                ${esc(topic.title)}
              </div>

              <div class="row-subtitle">
                ${esc(topic.category)}
                ·
                ${esc(
                  topic.profiles?.username ||
                  "Usuario"
                )}
              </div>

            </div>

            <div class="chevron">
              ›
            </div>

          </div>

        `).join("")
      }

    </div>

  `;
}


/* =========================================================
   CREATE FORUM
   ========================================================= */

function showCreateForum(){

  if(!currentUser){

    showLogin();
    return;
  }


  previousPage=currentPage;
  currentPage="createForum";

  setTitle("Nuevo foro");
  setBack(true);
  setAction(null);


  screen.innerHTML=`

    <div class="panel">

      <div class="panel-title">
        Nuevo foro
      </div>

      <div class="form">

        <label>
          Categoría
        </label>

        <select id="forumCategory">

          <option value="Música">
            Música
          </option>

          <option value="Juegos">
            Juegos
          </option>

          <option value="Apps">
            Apps
          </option>

          <option value="Off-topic">
            Off-topic
          </option>

        </select>


        <label>
          Título
        </label>

        <input
          id="forumTitle"
          maxlength="120"
          placeholder="Título del foro">


        <label>
          Contenido
        </label>

        <textarea
          id="forumBody"
          maxlength="10000"
          placeholder="Escribe el contenido..."></textarea>


        <div class="form-buttons">

          <button
            class="ios-button"
            onclick="createForum()">
            Publicar
          </button>

          <button
            class="ios-button gray-button"
            onclick="showForums()">
            Cancelar
          </button>

        </div>

        <div id="forumMessage"></div>

      </div>

    </div>

  `;
}


async function createForum(){

  const category =
    document.getElementById(
      "forumCategory"
    ).value;

  const title =
    document.getElementById(
      "forumTitle"
    ).value.trim();

  const body =
    document.getElementById(
      "forumBody"
    ).value.trim();

  const output =
    document.getElementById(
      "forumMessage"
    );


  if(!title || !body){

    output.innerHTML =
      alertBox(
        "Escribe un título y contenido."
      );

    return;
  }


  const {data,error} =
    await db
      .from("topics")
      .insert({

        category,

        title,

        body,

        user_id:
          currentUser.id

      })
      .select()
      .single();


  if(error){

    output.innerHTML =
      alertBox(error.message);

    return;
  }


  openForum(data.id);
}


/* =========================================================
   OPEN FORUM
   ========================================================= */

async function openForum(id){

  previousPage=currentPage;
  currentPage="forum";

  setTitle("Foro");
  setBack(true);
  setAction(null);


  screen.innerHTML =
    `<div class="empty">
       Cargando...
     </div>`;


  const {data:topic,error:topicError} =
    await db
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

    screen.innerHTML =
      alertBox(topicError.message);

    return;
  }


  const {data:replies,error:replyError} =
    await db
      .from("replies")
      .select(`
        *,
        profiles(
          username,
          avatar_url
        )
      `)
      .eq(
        "topic_id",
        id
      )
      .order(
        "created_at",
        {ascending:true}
      );


  if(replyError){

    screen.innerHTML =
      alertBox(replyError.message);

    return;
  }


  screen.innerHTML=`

    <div class="panel">

      <div class="panel-title">

        ${esc(topic.title)}

        <div class="small-text">
          ${esc(topic.category)}
        </div>

      </div>


      <div class="forum-post">

        <div class="forum-user">

          <img
            class="avatar avatar-small"
            src="${getAvatar(
              topic.profiles?.avatar_url
            )}">

          <div>

            <div class="forum-user-name">
              ${esc(
                topic.profiles?.username ||
                "Usuario"
              )}
            </div>

            <div class="forum-meta">
              Autor
            </div>

          </div>

        </div>


        <div class="forum-body">
          ${esc(topic.body)}
        </div>

      </div>

    </div>


    <div class="section-header">
      RESPUESTAS (${replies.length})
    </div>


    <div class="list">

      ${
        replies.length
        ?
        replies.map(reply=>`

          <div class="forum-post">

            <div class="forum-user">

              <img
                class="avatar avatar-small"
                src="${getAvatar(
                  reply.profiles?.avatar_url
                )}">

              <div>

                <div class="forum-user-name">
                  ${esc(
                    reply.profiles?.username ||
                    "Usuario"
                  )}
                </div>

                <div class="forum-meta">
                  Miembro
                </div>

              </div>

            </div>


            <div class="forum-body">
              ${esc(reply.body)}
            </div>

          </div>

        `).join("")
        :
        `
          <div class="empty">
            Todavía no hay respuestas.
          </div>
        `
      }

    </div>


    ${
      currentUser
      ?
      `
        <div class="panel">

          <div class="panel-title">
            Responder
          </div>

          <div class="form">

            <textarea
              id="replyBody"
              maxlength="10000"
              placeholder="Escribe una respuesta..."></textarea>

            <button
              class="ios-button"
              onclick="sendReply(${id})">
              Publicar respuesta
            </button>

            <div id="replyMessage"></div>

          </div>

        </div>
      `
      :
      `
        <div class="empty">

          <button
            class="ios-button"
            onclick="showLogin()">
            Inicia sesión para responder
          </button>

        </div>
      `
    }

  `;
}


/* =========================================================
   REPLY
   ========================================================= */

async function sendReply(topicId){

  const body =
    document.getElementById(
      "replyBody"
    ).value.trim();

  const output =
    document.getElementById(
      "replyMessage"
    );


  if(!body){

    output.innerHTML =
      alertBox(
        "Escribe una respuesta."
      );

    return;
  }


  const {error} =
    await db
      .from("replies")
      .insert({

        topic_id:topicId,

        body,

        user_id:
          currentUser.id

      });


  if(error){

    output.innerHTML =
      alertBox(error.message);

    return;
  }


  openForum(topicId);
}


/* =========================================================
   MESSAGES
   ========================================================= */

async function showMessages(){

  if(!currentUser){

    showLogin();
    return;
  }


  previousPage=currentPage;
  currentPage="messages";

  setTitle("Mensajes");
  setBack(false);
  setTab("Messages");

  setAction(
    "+",
    showNewMessage
  );


  screen.innerHTML =
    `<div class="empty">
       Cargando mensajes...
     </div>`;


  const {data,error} =
    await db
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
      .order(
        "created_at",
        {ascending:false}
      );


  if(error){

    screen.innerHTML =
      alertBox(
        "No se pudieron cargar los mensajes: " +
        error.message
      );

    return;
  }


  if(!data.length){

    screen.innerHTML=`

      <div class="empty">

        <div class="empty-icon">
          💬
        </div>

        <div class="empty-title">
          No tienes mensajes
        </div>

        <p>
          Puedes iniciar una conversación
          con otro usuario.
        </p>

        <button
          class="ios-button"
          onclick="showNewMessage()">
          Nuevo mensaje
        </button>

      </div>

    `;

    return;
  }


  const conversations={};


  data.forEach(m=>{

    const otherId =
      m.sender_id === currentUser.id
      ? m.receiver_id
      : m.sender_id;


    const other =
      m.sender_id === currentUser.id
      ? m.receiver
      : m.sender;


    if(!conversations[otherId]){

      conversations[otherId]={
        id:otherId,
        username:
          other?.username ||
          "Usuario",
        avatar_url:
          other?.avatar_url ||
          "",
        body:m.body
      };
    }

  });


  screen.innerHTML=`

    <div class="section-header">
      CONVERSACIONES
    </div>

    <div class="list">

      ${
        Object.values(conversations)
          .map(c=>`

            <div
              class="row"
              onclick="openConversation('${c.id}')">

              <img
                class="avatar avatar-small"
                src="${getAvatar(c.avatar_url)}">

              <div class="row-content">

                <div class="row-title">
                  ${esc(c.username)}
                </div>

                <div class="row-subtitle">
                  ${esc(
                    c.body.slice(0,70)
                  )}
                </div>

              </div>

              <div class="chevron">
                ›
              </div>

            </div>

          `).join("")
      }

    </div>

  `;
}


/* =========================================================
   NEW MESSAGE
   ========================================================= */

function showNewMessage(){

  if(!currentUser){

    showLogin();
    return;
  }


  previousPage=currentPage;
  currentPage="newMessage";

  setTitle("Nuevo mensaje");
  setBack(true);
  setAction(null);


  screen.innerHTML=`

    <div class="panel">

      <div class="panel-title">
        Nuevo mensaje
      </div>

      <div class="form">

        <label>
          Usuario
        </label>

        <input
          id="messageUsername"
          placeholder="Nombre de usuario">


        <label>
          Mensaje
        </label>

        <textarea
          id="messageBody"
          placeholder="Escribe tu mensaje..."></textarea>


        <button
          class="ios-button"
          onclick="sendNewMessage()">
          Enviar
        </button>


        <div id="messageOutput"></div>

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


  const {data} =
    await db
      .from("profiles")
      .select("username")
      .eq("id",userId)
      .single();


  if(data){

    document
      .getElementById(
        "messageUsername"
      )
      .value=
      data.username;
  }
}


async function sendNewMessage(){

  const username =
    document
      .getElementById(
        "messageUsername"
      )
      .value.trim();


  const body =
    document
      .getElementById(
        "messageBody"
      )
      .value.trim();


  const output =
    document
      .getElementById(
        "messageOutput"
      );


  if(!username || !body){

    output.innerHTML =
      alertBox(
        "Completa todos los campos."
      );

    return;
  }


  const {data:user,error:userError} =
    await db
      .from("profiles")
      .select("id")
      .eq(
        "username",
        username
      )
      .single();


  if(userError || !user){

    output.innerHTML =
      alertBox(
        "No existe ese usuario."
      );

    return;
  }


  if(user.id === currentUser.id){

    output.innerHTML =
      alertBox(
        "No puedes enviarte un mensaje a ti mismo."
      );

    return;
  }


  const {error} =
    await db
      .from("messages")
      .insert({

        sender_id:
          currentUser.id,

        receiver_id:
          user.id,

        body

      });


  if(error){

    output.innerHTML =
      alertBox(error.message);

    return;
  }


  openConversation(user.id);
}


/* =========================================================
   CONVERSATION
   ========================================================= */

async function openConversation(userId){

  previousPage=currentPage;
  currentPage="conversation";

  setTitle("Mensajes");
  setBack(true);
  setAction(null);


  const {data:user,error:userError} =
    await db
      .from("profiles")
      .select("*")
      .eq("id",userId)
      .single();


  if(userError){

    screen.innerHTML =
      alertBox(userError.message);

    return;
  }


  const {data,error} =
    await db
      .from("messages")
      .select("*")
      .or(
        `and(sender_id.eq.${currentUser.id},receiver_id.eq.${userId}),and(sender_id.eq.${userId},receiver_id.eq.${currentUser.id})`
      )
      .order(
        "created_at",
        {ascending:true}
      );


  if(error){

    screen.innerHTML =
      alertBox(error.message);

    return;
  }


  screen.innerHTML=`

    <div class="profile-header"
         style="padding:12px">

      <img
        class="avatar avatar-small"
        src="${getAvatar(user.avatar_url)}">

      <div
        class="profile-name"
        style="font-size:17px">

        ${esc(user.username)}

      </div>

    </div>


    <div class="list">

      ${
        data.length
        ?
        data.map(m=>`

          <div
            class="message ${
              m.sender_id === currentUser.id
                ? "me"
                : ""
            }">

            <div class="message-name">

              ${
                m.sender_id === currentUser.id
                ? "Tú"
                : esc(user.username)
              }

            </div>

            <div class="message-body">
              ${esc(m.body)}
            </div>

          </div>

        `).join("")
        :
        `
          <div class="empty">
            No hay mensajes todavía.
          </div>
        `
      }

    </div>


    <div class="panel">

      <div class="form">

        <textarea
          id="conversationText"
          placeholder="Escribe un mensaje..."></textarea>

        <button
          class="ios-button"
          onclick="sendConversationMessage('${userId}')">
          Enviar
        </button>

      </div>

    </div>

  `;
}


async function sendConversationMessage(userId){

  const input =
    document.getElementById(
      "conversationText"
    );


  const body =
    input.value.trim();


  if(!body)
    return;


  const {error} =
    await db
      .from("messages")
      .insert({

        sender_id:
          currentUser.id,

        receiver_id:
          userId,

        body

      });


  if(error){

    alert(error.message);
    return;
  }


  openConversation(userId);
}


/* =========================================================
   NAVIGATION
   ========================================================= */

function goBack(){

  switch(currentPage){

    case "login":
    case "register":
    case "users":
      showHome();
      break;

    case "profile":
      showHome();
      break;

    case "editProfile":
      showProfile();
      break;

    case "createForum":
      showForums();
      break;

    case "forum":
      showForums();
      break;

    case "newMessage":
      showMessages();
      break;

    case "conversation":
      showMessages();
      break;

    case "user":
      showUsers();
      break;

    default:
      showHome();
  }
}


/* =========================================================
   REALTIME
   ========================================================= */

db.channel("community-live")

  .on(
    "postgres_changes",
    {
      event:"*",
      schema:"public",
      table:"topics"
    },
    ()=>{
      if(currentPage==="forums"){
        showForums();
      }
    }
  )

  .on(
    "postgres_changes",
    {
      event:"*",
      schema:"public",
      table:"messages"
    },
    ()=>{
      if(currentPage==="messages"){
        showMessages();
      }
    }
  )

  .subscribe();


/* =========================================================
   START
   ========================================================= */

(async()=>{

  await loadSession();

  showHome();

})();
</script>

</body>
</html>
