<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>iPod Touch Forum</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    background: #c8cdd2;
    font-family: -apple-system, BlinkMacSystemFont, "Helvetica Neue", Arial, sans-serif;
    color: #111;
}

.app {
    max-width: 520px;
    min-height: 100vh;
    margin: auto;
    background: linear-gradient(#f8f8f8, #dfe3e7);
    box-shadow: 0 0 30px rgba(0,0,0,.35);
}

/* BARRA SUPERIOR */

.navbar {
    height: 52px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 9px;

    background:
        linear-gradient(
            #707b86,
            #252d34
        );

    border-bottom: 1px solid #111;
    color: white;

    position: sticky;
    top: 0;
    z-index: 10;
}

.navbar h1 {
    margin: 0;
    font-size: 20px;
    text-shadow: 0 -1px #000;
}

.button {
    border: 1px solid #111;
    border-radius: 7px;

    padding: 7px 11px;

    color: white;
    font-weight: bold;

    background:
        linear-gradient(
            #737f89,
            #303940
        );

    box-shadow:
        inset 0 1px rgba(255,255,255,.4),
        0 1px 2px rgba(0,0,0,.8);

    cursor: pointer;
}

.button:active {
    transform: scale(.97);
}

/* CONTENIDO */

.content {
    padding: 12px;
}

/* BUSCADOR */

.search {
    width: 100%;
    padding: 10px 12px;

    border-radius: 9px;
    border: 1px solid #999;

    font-size: 16px;

    background: white;

    box-shadow:
        inset 0 1px 3px rgba(0,0,0,.25);
}

/* SECCIONES */

.section-title {
    margin: 12px 5px 5px;

    font-size: 13px;
    font-weight: bold;

    color: #555;
    text-shadow: 0 1px white;
}

/* LISTAS */

.list {
    overflow: hidden;

    background: white;

    border: 1px solid #999;
    border-radius: 10px;

    box-shadow: 0 1px 4px rgba(0,0,0,.35);

    margin-bottom: 14px;
}

.row {
    display: flex;
    align-items: center;

    gap: 10px;

    padding: 11px;

    background:
        linear-gradient(
            #fff,
            #e9e9e9
        );

    border-bottom: 1px solid #ccc;

    cursor: pointer;
}

.row:last-child {
    border-bottom: none;
}

.row:active {
    background: #d5d5d5;
}

.icon {
    width: 40px;
    height: 40px;

    border-radius: 8px;

    display: flex;
    align-items: center;
    justify-content: center;

    font-size: 21px;
    color: white;

    background:
        linear-gradient(
            #74b8ed,
            #1764a5
        );

    border: 1px solid #15507e;

    box-shadow:
        inset 0 1px rgba(255,255,255,.7),
        0 1px 2px rgba(0,0,0,.4);

    text-shadow: 0 1px 2px #333;
}

.info {
    flex: 1;
}

.title {
    font-weight: bold;
    font-size: 16px;
}

.subtitle {
    color: #777;
    font-size: 12px;
    margin-top: 3px;
}

.arrow {
    color: #aaa;
    font-size: 25px;
}

/* TEMAS */

.topic {
    overflow: hidden;

    background: white;

    border: 1px solid #999;
    border-radius: 10px;

    box-shadow: 0 1px 4px rgba(0,0,0,.4);
}

.post {
    padding: 13px;
    border-bottom: 1px solid #ccc;
}

.post:last-child {
    border-bottom: none;
}

.user {
    display: flex;
    align-items: center;
    gap: 9px;
}

.avatar {
    width: 36px;
    height: 36px;

    border-radius: 50%;

    display: flex;
    align-items: center;
    justify-content: center;

    color: white;
    font-weight: bold;

    background:
        linear-gradient(
            #ddd,
            #888
        );

    border: 1px solid #777;
}

.username {
    font-weight: bold;
}

.date {
    font-size: 11px;
    color: #888;
}

.post h2 {
    font-size: 19px;
    margin: 12px 0 7px;
}

.post p {
    line-height: 1.45;
}

/* BOTONES DE POST */

.actions {
    display: flex;
    gap: 7px;
    margin-top: 10px;
}

.small-button {
    padding: 5px 9px;
    font-size: 12px;
}

/* CREAR TEMA */

.composer {
    display: none;

    padding: 10px;

    background: #eee;

    border: 1px solid #999;
    border-radius: 10px;

    box-shadow: 0 1px 3px #888;

    margin-top: 10px;
}

.composer input,
.composer textarea {
    width: 100%;

    padding: 9px;

    margin-bottom: 8px;

    border: 1px solid #aaa;
    border-radius: 7px;

    font-family: inherit;
    font-size: 15px;
}

.composer textarea {
    height: 110px;
    resize: none;
}

/* VACÍO */

.empty {
    padding: 25px;
    text-align: center;
    color: #777;
}

/* FOOTER */

.footer {
    padding: 20px;

    text-align: center;

    color: #777;
    font-size: 11px;
}
</style>
</head>


<body>

<div class="app">

<header class="navbar">

    <button
        class="button"
        id="backButton"
        style="display:none"
    >
        ‹ Foro
    </button>

    <h1 id="pageTitle">
        Foro
    </h1>

    <button
        class="button"
        id="newButton"
    >
        Nuevo
    </button>

</header>


<main class="content" id="content">
    <!-- BUSCADOR -->
    <input
        class="search"
        id="search"
        placeholder="Buscar en el foro…"
    >
    <!-- CATEGORÍAS -->
    <div class="section-title">
        CATEGORÍAS
    </div>
    <div class="list">
        <div
            class="row"
            data-category="Música"        >
           <div class="icon">
                ♫
            </div>
            <div class="info">
                <div class="title">
                    Música
                </div>
                <div class="subtitle">
                    Álbumes, artistas y producción
                </div>
            </div>
            <div class="arrow">
                ›
           </div>
        </div>
        <div
            class="row"
            data-category="Juegos"
        >
            <div class="icon">
                🎮
            </div>
            <div class="info">
                <div class="title">
                    Juegos
           </div>
                <div class="subtitle">
                    Consolas, juegos y comunidad
                </div>
            </div>
            <div class="arrow">
                ›
            </div>
        </div>
        <div
            class="row"
            data-category="Apps"
        >
            <div class="icon">
                ▦
            </div>
            <div class="info">
                <div class="title">
                    Apps
              </div>
                <div class="subtitle">
                    iOS, Android y software
               </div>
            </div>
            <div class="arrow">
                ›
            </div>
        </div>
        <div
            class="row"
            data-category="Off-topic"     
            <div class="icon">
                ☁
            </div>
            <div class="info">
                <div class="title">
                    Off-topic
                </div>
                <div class="subtitle">
                    Habla de cualquier cos
                </div>
            </div>
            <div class="arrow">
                ›
          </div>
       </div>
    </div>
    <!-- RECIENTES -->
    <div class="section-title">
        TEMAS RECIENTES
    </div>
    <div
        class="list"
        id="recentTopics"
    ></div>
    <!-- CREAR TEMA -->
    <div
        class="composer"
        id="composer"
    >
        <input
            id="topicTitle"
            placeholder="Título del tema"
        >
        <textarea
            id="topicBody"
            placeholder="Escribe tu publicación…"
        ></textarea>
        <button
            class="button"
            id="publishButton"
        >
            Publicar tema       </button>
    </div>
    <div class="footer">
        iPod Touch Forum · ✦
    </div>

</main>

</div>


<script>

/* =========================
   DATOS
========================= */

const defaultTopics = [

    {
        id: 1,
        category: "Música",
        title: "¿Qué álbum están escuchando últimamente?",
        body: "Estoy buscando música nueva. Dejen sus recomendaciones 👀",
        user: "Alex",
        date: "Hoy · 12:42",
        replies: 8
    },

    {
        id: 2,
        category: "Juegos",
        title: "Juegos que todavía valen la pena",
        body: "¿Qué juegos siguen siendo buenísimos aunque tengan algunos años?",
        user: "Nico",
        date: "Hoy · 11:18",
        replies: 14
    },

    {
        id: 3,
        category: "Apps",
        title: "Apps con estética retro",
        body: "¿Conocen aplicaciones que tengan ese estilo clásico de iOS?",
        user: "Milo",
        date: "Ayer · 20:07",
        replies: 5
    },

    {
        id: 4,
        category: "Off-topic",
        title: "¿Cuál fue su primer iPod?",
        body: "El mío era un iPod touch viejo y todavía extraño esa interfaz.",
        user: "Sam",
        date: "Ayer · 17:31",
        replies: 11
    }

];


/* =========================
   LOCAL STORAGE
========================= */

let topics =
    JSON.parse(
        localStorage.getItem("ipodForumTopics")
    ) || defaultTopics;


/* =========================
   ELEMENTOS
========================= */

const content =
    document.getElementById("content");

const pageTitle =
    document.getElementById("pageTitle");

const backButton =
    document.getElementById("backButton");

const newButton =
    document.getElementById("newButton");

const recentTopics =
    document.getElementById("recentTopics");

const search =
    document.getElementById("search");

const composer =
    document.getElementById("composer");


let currentCategory = null;
let currentTopic = null;


/* =========================
   GUARDAR
========================= */

function saveTopics() {

    localStorage.setItem(
        "ipodForumTopics",
        JSON.stringify(topics)
    );

}


/* =========================
   ESCAPAR HTML
========================= */

function escapeHTML(text) {

    return String(text)
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;")
        .replace(/'/g, "&#039;");

}


/* =========================
   CREAR FILA
========================= */

function createTopicRow(topic) {

    const row =
        document.createElement("div");

    row.className = "row";

    row.innerHTML = `

        <div class="icon">
            💬
        </div>

        <div class="info">

            <div class="title">
                ${escapeHTML(topic.title)}
            </div>

            <div class="subtitle">
                ${escapeHTML(topic.user)}
                · ${topic.replies} respuestas
                · ${escapeHTML(topic.category)}
            </div>

        </div>

        <div class="arrow">
            ›
        </div>

    `;

    row.onclick = () =>
        openTopic(topic.id);

    return row;

}


/* =========================
   TEMAS RECIENTES
========================= */

function renderRecent(filter = "") {

    recentTopics.innerHTML = "";

    const filtered =
        topics.filter(topic => {

            const text =
                (
                    topic.title +
                    " " +
                    topic.body +
                    " " +
                    topic.category
                ).toLowerCase();

            return text.includes(
                filter.toLowerCase()
            );

        });


    if (filtered.length === 0) {

        recentTopics.innerHTML =
            `<div class="empty">
                No encontramos temas.
            </div>`;

        return;
    }


    filtered
        .slice(0, 8)
        .forEach(topic => {

            recentTopics.appendChild(
                createTopicRow(topic)
            );

        });

}


/* =========================
   ABRIR CATEGORÍA
========================= */

function openCategory(category) {

    currentCategory = category;

    pageTitle.textContent =
        category;

    backButton.style.display =
        "block";

    newButton.style.display =
        "block";


    content.innerHTML = `

        <div class="section-title">
            TEMAS EN ${category.toUpperCase()}
        </div>

        <div
            class="list"
            id="categoryTopics"
        ></div>

        <div class="footer">
            Toca un tema para abrirlo ✦
        </div>

    `;


    const list =
        document.getElementById(
            "categoryTopics"
        );


    const categoryTopics =
        topics.filter(
            topic =>
                topic.category === category
        );


    if (categoryTopics.length === 0) {

        list.innerHTML =
            `<div class="empty">
                Todavía no hay temas aquí.
            </div>`;

        return;
    }


    categoryTopics.forEach(topic => {

        list.appendChild(
            createTopicRow(topic)
        );

    });

}


/* =========================
   ABRIR TEMA
========================= */

function openTopic(id) {

    currentTopic =
        topics.find(
            topic => topic.id === id
        );


    if (!currentTopic)
        return;


    pageTitle.textContent =
        "Tema";

    backButton.style.display =
        "block";

    newButton.style.display =
        "none";


    content.innerHTML = `

        <div class="topic">

            <div class="post">

                <div class="user">

                    <div class="avatar">
                        ${currentTopic.user[0]}
                    </div>

                    <div>

                        <div class="username">
                            ${escapeHTML(
                                currentTopic.user
                            )}
                        </div>

                        <div class="date">
                            ${currentTopic.date}
                        </div>

                    </div>

                </div>


                <h2>
                    ${escapeHTML(
                        currentTopic.title
                    )}
                </h2>


                <p>
                    ${escapeHTML(
                        currentTopic.body
                    )}
                </p>


                <div class="actions">

                    <button
                        class="button small-button"
                        onclick="likeTopic()"
                    >
                        ♥ Me gusta
                    </button>

                    <button
                        class="button small-button"
                        onclick="showReplyBox()"
                    >
                        ↩ Responder
                    </button>

                </div>

            </div>


            <div class="post">

                <div class="user">

                    <div class="avatar">
                        J
                    </div>

                    <div>

                        <div class="username">
                            Jordan
                        </div>

                        <div class="date">
                            Hoy · 13:02
                        </div>

                    </div>

                </div>


                <p>
                    Buen tema. Me sumo a la conversación 😎
                </p>

            </div>

        </div>


        <div id="replyBox"></div>

    `;

}


/* =========================
   LIKE
========================= */

function likeTopic() {

    alert("♥ ¡Me gusta!");

}


/* =========================
   RESPONDER
========================= */

function showReplyBox() {

    const box =
        document.getElementById(
            "replyBox"
        );


    box.innerHTML = `

        <div
            class="composer"
            style="display:block"
        >

            <textarea
                id="replyText"
                placeholder="Escribe una respuesta…"
            ></textarea>

            <button
                class="button"
                onclick="sendReply()"
            >
                Enviar
            </button>

        </div>

    `;

}


/* =========================
   ENVIAR RESPUESTA
========================= */

function sendReply() {

    const text =
        document
            .getElementById("replyText")
            .value
            .trim();


    if (!text)
        return;


    currentTopic.replies++;

    saveTopics();

    alert(
        "Respuesta publicada ✦"
    );

    openTopic(
        currentTopic.id
    );

}


/* =========================
   CATEGORÍAS
========================= */

document
    .querySelectorAll("[data-category]")
    .forEach(row => {

        row.onclick = () => {

            openCategory(
                row.dataset.category
            );

        };

    });


/* =========================
   BUSCAR
========================= */

search.oninput = event => {

    renderRecent(
        event.target.value
    );

};


/* =========================
   NUEVO TEMA
========================= */

newButton.onclick = () => {

    if (!document.getElementById("topicTitle")) {

        location.reload();

        return;
    }


    composer.style.display =
        composer.style.display === "block"
            ? "none"
            : "block";

};


/* =========================
   PUBLICAR
========================= */

document
    .getElementById("publishButton")
    .onclick = () => {

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


        if (!title || !body) {

            alert(
                "Escribe un título y un mensaje."
            );

            return;
        }


        topics.unshift({

            id: Date.now(),

            category:
                currentCategory ||
                "Off-topic",

            title: title,

            body: body,

            user: "Tú",

            date: "Ahora",

            replies: 0

        });


        saveTopics();


        document
            .getElementById("topicTitle")
            .value = "";

        document
            .getElementById("topicBody")
            .value = "";


        composer.style.display =
            "none";


        renderRecent();

    };


/* =========================
   VOLVER
========================= */

backButton.onclick = () => {

    location.reload();

};


/* =========================
   INICIAR
========================= */

renderRecent();

</script>

</body>
</html>
