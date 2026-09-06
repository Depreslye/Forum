
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport"
      content="width=device-width, initial-scale=1.0,
               maximum-scale=1.0,user-scalable=no">

<title>iPod Forum</title>

<style>

/* =====================================================
   IPOD TOUCH / IOS 6 STYLE
===================================================== */

*{
    box-sizing:border-box;
    -webkit-tap-highlight-color:transparent;
}

html,
body{
    margin:0;
    padding:0;

    min-height:100%;

    font-family:
        -apple-system,
        BlinkMacSystemFont,
        "Helvetica Neue",
        Arial,
        sans-serif;

    background:
        linear-gradient(
            135deg,
            #d9d9d9 0%,
            #bcbcbc 50%,
            #d5d5d5 100%
        );

    color:#222;
}


/* =====================================================
   IPOD BODY
===================================================== */

#app{

    width:100%;
    max-width:520px;

    min-height:100vh;

    margin:auto;

    background:
        linear-gradient(
            #eeeeee,
            #d1d1d1
        );

    box-shadow:
        0 0 25px rgba(0,0,0,.45);

    position:relative;

}


/* =====================================================
   TOP BAR
===================================================== */

.navbar{

    height:52px;

    display:flex;

    align-items:center;

    justify-content:space-between;

    padding:0 7px;

    color:white;

    background:
        linear-gradient(
            #7d7d7d 0%,
            #555 45%,
            #363636 50%,
            #626262 100%
        );

    border-bottom:1px solid #222;

    box-shadow:
        inset 0 1px rgba(255,255,255,.35),
        0 1px 3px rgba(0,0,0,.5);

}


.navbar h1{

    margin:0;

    font-size:20px;

    font-weight:bold;

    text-shadow:
        0 -1px 1px #000;

}


.navbutton{

    min-width:65px;

    padding:7px 10px;

    color:white;

    font-size:13px;

    font-weight:bold;

    border-radius:6px;

    border:1px solid #222;

    background:
        linear-gradient(
            #777,
            #333
        );

    box-shadow:
        inset 0 1px rgba(255,255,255,.35),
        0 1px 1px rgba(0,0,0,.5);

}


.navbutton:active{

    background:
        linear-gradient(
            #333,
            #777
        );

}


/* =====================================================
   CONTENT
===================================================== */

.screen{

    padding:12px;

}


.hidden{

    display:none!important;

}


/* =====================================================
   SEARCH
===================================================== */

.search{

    width:100%;

    height:38px;

    padding:0 12px;

    border-radius:8px;

    border:1px solid #999;

    background:
        linear-gradient(
            #fff,
            #e5e5e5
        );

    box-shadow:
        inset 0 1px 3px rgba(0,0,0,.2);

    font-size:16px;

    outline:none;

    margin-bottom:14px;

}


.search:focus{

    border-color:#4c9bea;

}


/* =====================================================
   SECTIONS
===================================================== */

.section{

    margin-bottom:20px;

}


.section-title{

    color:#555;

    font-size:13px;

    font-weight:bold;

    text-shadow:
        0 1px white;

    margin:

        7px 10px;

}


/* =====================================================
   IOS LIST
===================================================== */

.list{

    background:#fff;

    border:1px solid #999;

    border-radius:9px;

    overflow:hidden;

    box-shadow:
        0 1px 2px rgba(0,0,0,.25);

}


.item{

    min-height:52px;

    padding:10px 38px 10px 14px;

    position:relative;

    background:
        linear-gradient(
            #fff,
            #eeeeee
        );

    border-bottom:1px solid #ccc;

    cursor:pointer;

}


.item:last-child{

    border-bottom:none;

}


.item:after{

    content:"›";

    position:absolute;

    right:14px;

    top:50%;

    transform:
        translateY(-50%);

    color:#999;

    font-size:27px;

    font-weight:normal;

}


.item:active{

    color:white;

    background:
        linear-gradient(
            #70b5f5,
            #277dcc
        );

}


.item:active .item-info{

    color:#e6f2ff;

}


.item-title{

    font-size:16px;

    font-weight:bold;

}


.item-info{

    color:#777;

    font-size:12px;

    margin-top:4px;

}


/* =====================================================
   IPOD BUTTON
===================================================== */

.bigbutton{

    width:100%;

    min-height:42px;

    padding:10px;

    border-radius:8px;

    border:1px solid #777;

    color:#111;

    font-size:16px;

    font-weight:bold;

    background:
        linear-gradient(
            #fff,
            #c7c7c7
        );

    box-shadow:
        inset 0 1px white,
        0 1px 2px rgba(0,0,0,.3);

}


.bigbutton:active{

    background:
        linear-gradient(
            #aaa,
            #eee
        );

}


/* =====================================================
   FORM
===================================================== */

input,
textarea,
select{

    width:100%;

    padding:10px;

    border:1px solid #999;

    border-radius:7px;

    background:white;

    box-shadow:
        inset 0 1px 2px rgba(0,0,0,.15);

    font-family:inherit;

    font-size:16px;

    margin-top:5px;

    margin-bottom:13px;

}


textarea{

    min-height:120px;

    resize:vertical;

}


label{

    display:block;

    color:#555;

    font-size:13px;

    font-weight:bold;

    text-shadow:0 1px white;

    margin-top:5px;

}


/* =====================================================
   CARD
===================================================== */

.card{

    padding:14px;

    margin-bottom:12px;

    background:
        linear-gradient(
            #fafafa,
            #e3e3e3
        );

    border:1px solid #999;

    border-radius:9px;

    box-shadow:
        0 1px 2px rgba(0,0,0,.25);

}


/* =====================================================
   PROFILE
===================================================== */

.profile-header,
.profile-top{

    display:flex;

    align-items:center;

    gap:15px;

    margin-bottom:18px;

}


.large-avatar{

    width:90px;
    height:90px;

    flex-shrink:0;

    display:flex;

    justify-content:center;
    align-items:center;

    overflow:hidden;

    border-radius:18px;

    border:1px solid #777;

    background:
        linear-gradient(
            #f7f7f7,
            #aaa
        );

    box-shadow:
        inset 0 1px white,
        0 2px 3px rgba(0,0,0,.3);

    font-size:40px;

}


.avatar-image{

    width:100%;
    height:100%;

    object-fit:cover;

}


.profile-main h2{

    margin:0 0 5px;

    font-size:22px;

}


.profile-country{

    color:#777;

    font-size:13px;

}


.profile-description{

    background:white;

    border:1px solid #aaa;

    border-radius:8px;

    padding:12px;

    margin-bottom:12px;

    line-height:1.4;

}


.profile-details{

    background:white;

    border:1px solid #aaa;

    border-radius:8px;

    padding:8px;

    margin-bottom:15px;

}


.profile-details div{

    padding:8px 4px;

    border-bottom:1px solid #ddd;

}


.profile-details div:last-child{

    border-bottom:none;

}


/* =====================================================
   REPLIES
===================================================== */

.reply{

    background:white;

    border:1px solid #aaa;

    border-radius:8px;

    padding:12px;

    margin-bottom:9px;

    box-shadow:
        0 1px 2px rgba(0,0,0,.2);

}


.reply-user{

    font-weight:bold;

    color:#333;

}


.reply-date{

    color:#888;

    font-size:11px;

    margin-top:3px;

}


.reply-body,
.topic-body{

    margin-top:10px;

    white-space:pre-wrap;

    word-break:break-word;

    line-height:1.45;

}


/* =====================================================
   EMPTY
===================================================== */

.empty{

    padding:28px 15px;

    text-align:center;

    color:#777;

    font-size:14px;

    background:white;

}


/* =====================================================
   MESSAGE
===================================================== */

.message{

    padding:10px;

    margin-bottom:10px;

    border-radius:7px;

    color:#174b7c;

    background:
        linear-gradient(
            #eaf5ff,
            #d4e9fb
        );

    border:1px solid #91b7d8;

    font-size:14px;

}


/* =====================================================
   TOPIC HEADER
===================================================== */

.topic-category{

    color:#777;

    font-size:12px;

    font-weight:bold;

    text-transform:uppercase;

}


.topic-author{

    color:#777;

    font-size:12px;

}


.topic-title{

    margin:7px 0;

    font-size:22px;

    line-height:1.2;

}


/* =====================================================
   IPOD BLUE LINKS
===================================================== */

.blue{

    color:#1674c7;

}


/* =====================================================
   FILE INPUT
===================================================== */

input[type="file"]{

    padding:7px;

    background:
        linear-gradient(
            #fff,
            #ddd
        );

}


/* =====================================================
   SMALL IOS STYLE HEADER
===================================================== */

.ios-header{

    text-align:center;

    padding:5px;

    color:#555;

    font-size:13px;

    font-weight:bold;

}


/* =====================================================
   RESPONSIVE
===================================================== */

@media(max-width:520px){

    body{

        background:#d1d1d1;

    }

    #app{

        min-height:100vh;

        box-shadow:none;

    }

}

</style>
</head>


<body>

<div id="app">


<!-- =================================================
     NAVBAR
================================================= -->

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


<!-- =================================================
     HOME
================================================= -->

<div id="home">


<input
    id="search"
    class="search"
    placeholder="Buscar en el foro..."
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

            <div class="item-title">
                🎵 Música
            </div>

            <div class="item-info">
                Música, artistas, álbumes y producción
            </div>

        </div>


        <div
            class="item"
            onclick="openCategory('Juegos')">

            <div class="item-title">
                🎮 Juegos
            </div>

            <div class="item-info">
                Videojuegos, consolas y emulación
            </div>

        </div>


        <div
            class="item"
            onclick="openCategory('Apps')">

            <div class="item-title">
                📱 Apps
            </div>

            <div class="item-info">
                Aplicaciones, Android, iOS y tecnología
            </div>

        </div>


        <div
            class="item"
            onclick="openCategory('Off-topic')">

            <div class="item-title">
                💬 Off-topic
            </div>

            <div class="item-info">
                Conversaciones generales
            </div>

        </div>


    </div>

</div>



<div class="section">


    <div style="
        display:flex;
        align-items:center;
        justify-content:space-between;
    ">

        <div class="section-title">
            Hilos recientes
        </div>


        <button
            class="navbutton"
            onclick="showCreateTopic()">

            + Nuevo

        </button>

    </div>


    <div
        id="topics"
        class="list">

    </div>

</div>


</div>


<!-- =================================================
     PROFILE
================================================= -->

<div
    id="profilePage"
    class="hidden">


    <button
        class="navbutton back"
        onclick="goHome()">

        ← Volver

    </button>


    <div id="profileBox"></div>


</div>



<!-- =================================================
     CREATE TOPIC
================================================= -->

<div
    id="createTopicPage"
    class="hidden">


    <button
        class="navbutton back"
        onclick="goHome()">

        ← Volver

    </button>


    <div class="card">


        <div class="ios-header">
            NUEVO HILO
        </div>


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
            placeholder="Título"
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



<!-- =================================================
     CATEGORY
================================================= -->

<div
    id="categoryPage"
    class="hidden">


    <button
        class="navbutton back"
        onclick="goHome()">

        ← Volver

    </button>


    <div class="ios-header"
         id="categoryTitle">

    </div>


    <div
        id="categoryTopics"
        class="list">

    </div>


</div>



<!-- =================================================
     TOPIC
================================================= -->

<div
    id="topicPage"
    class="hidden">


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


        <div class="ios-header">
            RESPONDER
        </div>


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

/* =====================================================
   STORAGE
===================================================== */

let profile =
    JSON.parse(
        localStorage.getItem(
            "ipod_forum_profile"
        ) || "null"
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


let currentTopic = null;


let currentUser =
    profile
        ? profile.username
        : localStorage.getItem(
            "ipod_forum_username"
        );


/* =====================================================
   SAVE
===================================================== */

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


/* =====================================================
   ESCAPE
===================================================== */

function escapeHTML(text){

    const div =
        document.createElement("div");

    div.textContent =
        text || "";

    return div.innerHTML;

}


/* =====================================================
   MESSAGE
===================================================== */

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

        box.innerHTML = "";

    },3000);

}


/* =====================================================
   HIDE ALL
===================================================== */

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


/* =====================================================
   HOME
===================================================== */

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


/* =====================================================
   RENDER TOPICS
===================================================== */

function renderTopics(){

    const container =
        document.getElementById(
            "topics"
        );


    const search =
        (
            document.getElementById(
                "search"
            ).value || ""
        )
        .toLowerCase();


    const filtered =
        topics.filter(topic=>{

            return (

                topic.title
                    .toLowerCase()
                    .includes(search)

                ||

                topic.body
                    .toLowerCase()
                    .includes(search)

                ||

                topic.username
                    .toLowerCase()
                    .includes(search)

            );

        });


    if(filtered.length === 0){

        container.innerHTML = `

            <div class="empty">

                Todavía no hay hilos.

                <br><br>

                Sé el primero en crear uno.

            </div>

        `;

        return;

    }


    container.innerHTML =

        filtered.map(topic=>`

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


/* =====================================================
   PROFILE
===================================================== */

function showProfile(){

    hideAll();


    document
        .getElementById(
            "profilePage"
        )
        .classList
        .remove("hidden");


    document
        .getElementById(
            "pageTitle"
        )
        .textContent =
        "Perfil";


    renderProfile();

}


function renderProfile(){

    const box =
        document.getElementById(
            "profileBox"
        );


    /* ----------------------------------------------
       NO PROFILE
    ---------------------------------------------- */

    if(!profile){

        box.innerHTML = `

            <div class="card">


                <div class="profile-header">

                    <div
                        class="large-avatar"
                        id="avatarPreview">

                        👤

                    </div>


                    <div>

                        <h2 style="margin:0">

                            Crear perfil

                        </h2>


                        <div
                            style="color:#777">

                            Personaliza tu identidad
                            en el foro.

                        </div>

                    </div>

                </div>


                <label>
                    Foto de perfil
                </label>


                <input
                    type="file"
                    id="profilePhoto"
                    accept="image/*"
                    onchange="previewProfilePhoto(event)"
                >


                <label>
                    Nombre de usuario
                </label>


                <input
                    id="profileUsername"
                    maxlength="25"
                    placeholder="Tu nombre"
                >


                <label>
                    Descripción
                </label>


                <textarea
                    id="profileBio"
                    maxlength="160"
                    placeholder="Cuéntanos algo sobre ti..."
                ></textarea>


                <label>
                    Edad
                </label>


                <input
                    id="profileAge"
                    type="number"
                    min="1"
                    max="120"
                    placeholder="Opcional"
                >


                <label>
                    País
                </label>


                <input
                    id="profileCountry"
                    maxlength="40"
                    placeholder="Ej: Brasil"
                >


                <label>
                    Sitio web
                </label>


                <input
                    id="profileWebsite"
                    maxlength="100"
                    placeholder="Opcional"
                >


                <button
                    class="bigbutton"
                    onclick="createFullProfile()">

                    Crear perfil

                </button>


            </div>

        `;

        return;

    }


    /* ----------------------------------------------
       EXISTING PROFILE
    ---------------------------------------------- */

    let avatar = "👤";


    if(profile.photo){

        avatar = `

            <img
                src="${profile.photo}"
                class="avatar-image">

        `;

    }


    box.innerHTML = `

        <div class="card profile-card">


            <div class="profile-top">


                <div class="large-avatar">

                    ${avatar}

                </div>


                <div class="profile-main">

                    <h2>

                        ${escapeHTML(
                            profile.username
                        )}

                    </h2>


                    ${
                        profile.country
                        ?
                        `
                        <div
                            class="profile-country">

                            🌎
                            ${escapeHTML(
                                profile.country
                            )}

                        </div>
                        `
                        :
                        ""
                    }

                </div>


            </div>


            ${
                profile.bio
                ?
                `
                <div
                    class="profile-description">

                    ${escapeHTML(
                        profile.bio
                    )}

                </div>
                `
                :
                ""
            }


            <div class="profile-details">


                ${
                    profile.age
                    ?
                    `
                    <div>

                        🎂
                        ${escapeHTML(
                            profile.age
                        )}
                        años

                    </div>
                    `
                    :
                    ""
                }


                ${
                    profile.website
                    ?
                    `
                    <div>

                        🔗
                        ${escapeHTML(
                            profile.website
                        )}

                    </div>
                    `
                    :
                    ""
                }


                <div>

                    🗓️ Miembro desde

                    ${new Date(
                        profile.createdAt
                    ).toLocaleDateString()}

                </div>


            </div>


            <button
                class="bigbutton"
                onclick="editProfile()">

                ✏️ Editar perfil

            </button>


            <br><br>


            <button
                class="bigbutton"
                onclick="deleteProfile()">

                Cambiar / eliminar perfil

            </button>


        </div>

    `;

}


/* =====================================================
   PROFILE PHOTO PREVIEW
===================================================== */

function previewProfilePhoto(event){

    const file =
        event.target.files[0];


    if(!file) return;


    const reader =
        new FileReader();


    reader.onload = function(e){

        const preview =
            document.getElementById(
                "avatarPreview"
            );


        preview.innerHTML = `

            <img
                src="${e.target.result}"
                class="avatar-image">

        `;

    };


    reader.readAsDataURL(file);

}


/* =====================================================
   CREATE PROFILE
===================================================== */

function createFullProfile(){

    const username =
        document
            .getElementById(
                "profileUsername"
            )
            .value
            .trim();


    const bio =
        document
            .getElementById(
                "profileBio"
            )
            .value
            .trim();


    const age =
        document
            .getElementById(
                "profileAge"
            )
            .value
            .trim();


    const country =
        document
            .getElementById(
                "profileCountry"
            )
            .value
            .trim();


    const website =
        document
            .getElementById(
                "profileWebsite"
            )
            .value
            .trim();


    if(username.length < 3){

        showMessage(
            "El nombre debe tener al menos 3 caracteres."
        );

        return;

    }


    const file =
        document
            .getElementById(
                "profilePhoto"
            )
            .files[0];


    if(file){

        const reader =
            new FileReader();


        reader.onload = function(e){

            saveProfile(
                username,
                bio,
                age,
                country,
                website,
                e.target.result
            );

        };


        reader.readAsDataURL(file);

    }

    else{

        saveProfile(
            username,
            bio,
            age,
            country,
            website,
            ""
        );

    }

}


/* =====================================================
   SAVE PROFILE
===================================================== */

function saveProfile(
    username,
    bio,
    age,
    country,
    website,
    photo
){

    profile = {

        username,
        bio,
        age,
        country,
        website,
        photo,

        createdAt:
            new Date().toISOString()

    };


    currentUser =
        username;


    localStorage.setItem(
        "ipod_forum_profile",
        JSON.stringify(profile)
    );


    localStorage.setItem(
        "ipod_forum_username",
        username
    );


    showMessage(
        "Perfil creado correctamente."
    );


    renderProfile();

}


/* =====================================================
   EDIT PROFILE
===================================================== */

function editProfile(){

    const box =
        document.getElementById(
            "profileBox"
        );


    box.innerHTML = `

        <div class="card">


            <div class="ios-header">

                EDITAR PERFIL

            </div>


            <div
                class="large-avatar"
                id="avatarPreview">


                ${
                    profile.photo
                    ?
                    `
                    <img
                        src="${profile.photo}"
                        class="avatar-image">
                    `
                    :
                    "👤"
                }


            </div>


            <label>
                Cambiar foto
            </label>


            <input
                type="file"
                id="profilePhoto"
                accept="image/*"
                onchange="previewProfilePhoto(event)"
            >


            <label>
                Nombre
            </label>


            <input
                id="profileUsername"
                maxlength="25"
                value="${escapeHTML(
                    profile.username
                )}"
            >


            <label>
                Descripción
            </label>


            <textarea
                id="profileBio"
                maxlength="160"
            >${escapeHTML(
                profile.bio || ""
            )}</textarea>


            <label>
                Edad
            </label>


            <input
                id="profileAge"
                type="number"
                value="${escapeHTML(
                    profile.age || ""
                )}"
            >


            <label>
                País
            </label>


            <input
                id="profileCountry"
                maxlength="40"
                value="${escapeHTML(
                    profile.country || ""
                )}"
            >


            <label>
                Sitio web
            </label>


            <input
                id="profileWebsite"
                maxlength="100"
                value="${escapeHTML(
                    profile.website || ""
                )}"
            >


            <button
                class="bigbutton"
                onclick="updateProfile()">

                Guardar cambios

            </button>


        </div>

    `;

}


/* =====================================================
   UPDATE PROFILE
===================================================== */

function updateProfile(){

    const username =
        document
            .getElementById(
                "profileUsername"
            )
            .value
            .trim();


    const bio =
        document
            .getElementById(
                "profileBio"
            )
            .value
            .trim();


    const age =
        document
            .getElementById(
                "profileAge"
            )
            .value
            .trim();


    const country =
        document
            .getElementById(
                "profileCountry"
            )
            .value
            .trim();


    const website =
        document
            .getElementById(
                "profileWebsite"
            )
            .value
            .trim();


    if(username.length < 3){

        showMessage(
            "El nombre debe tener al menos 3 caracteres."
        );

        return;

    }


    const file =
        document
            .getElementById(
                "profilePhoto"
            )
            .files[0];


    if(file){

        const reader =
            new FileReader();


        reader.onload = function(e){

            finishUpdate(
                username,
                bio,
                age,
                country,
                website,
                e.target.result
            );

        };


        reader.readAsDataURL(file);

    }

    else{

        finishUpdate(
            username,
            bio,
            age,
            country,
            website,
            profile.photo
        );

    }

}


/* =====================================================
   FINISH UPDATE
===================================================== */

function finishUpdate(
    username,
    bio,
    age,
    country,
    website,
    photo
){

    profile = {

        ...profile,

        username,
        bio,
        age,
        country,
        website,
        photo

    };


    currentUser =
        username;


    localStorage.setItem(
        "ipod_forum_profile",
        JSON.stringify(profile)
    );


    localStorage.setItem(
        "ipod_forum_username",
        username
    );


    showMessage(
        "Perfil actualizado."
    );


    renderProfile();

}


/* =====================================================
   DELETE PROFILE
===================================================== */

function deleteProfile(){

    if(!confirm(
        "¿Eliminar tu perfil de este dispositivo?"
    )) return;


    profile = null;

    currentUser = null;


    localStorage.removeItem(
        "ipod_forum_profile"
    );


    localStorage.removeItem(
        "ipod_forum_username"
    );


    showMessage(
        "Perfil eliminado."
    );


    renderProfile();

}


/* =====================================================
   CREATE TOPIC PAGE
===================================================== */

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


/* =====================================================
   CREATE TOPIC
===================================================== */

function createTopic(){

    if(!currentUser){

        showMessage(
            "Primero crea un perfil."
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


    topics.unshift(topic);


    saveData();


    document
        .getElementById(
            "topicTitle"
        )
        .value = "";


    document
        .getElementById(
            "topicBody"
        )
        .value = "";


    showMessage(
        "Hilo publicado."
    );


    setTimeout(
        goHome,
        500
    );

}


/* =====================================================
   CATEGORY
===================================================== */

function openCategory(category){

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


    if(filtered.length === 0){

        container.innerHTML = `

            <div class="empty">

                No hay hilos en esta categoría.

                <br><br>

                Puedes crear el primero.

            </div>

        `;

        return;

    }


    container.innerHTML =

        filtered.map(topic=>`

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


/* =====================================================
   OPEN TOPIC
===================================================== */

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


                <div class="topic-category">

                    ${escapeHTML(
                        topic.category
                    )}

                </div>


                <div class="topic-title">

                    ${escapeHTML(
                        topic.title
                    )}

                </div>


                <div class="topic-author">

                    Por
                    <span class="blue">

                        ${escapeHTML(
                            topic.username
                        )}

                    </span>

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


/* =====================================================
   REPLIES
===================================================== */

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


    if(topicReplies.length === 0){

        container.innerHTML = `

            <div class="empty">

                Todavía no hay respuestas.

            </div>

        `;

        return;

    }


    container.innerHTML =

        topicReplies.map(reply=>`

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


/* =====================================================
   SEND REPLY
===================================================== */

function sendReply(){

    if(!currentUser){

        showMessage(
            "Primero crea un perfil."
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


    replies.push({

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

    });


    saveData();


    textarea.value = "";


    renderReplies();

}


/* =====================================================
   START
===================================================== */

goHome();

</script>

</body>
</html>
