<!DOCTYPE html>
<html lang="pt">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tudo Acontece</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif; }

  :root {
    --bg: #0a0a0f;
    --card: #15151f;
    --card2: #1e1e2e;
    --border: #2a2a3e;
    --text: #fff;
    --text2: #a0a0b8;
    --accent: #ff2d55;
    --accent2: #ff6b9d;
    --grad: linear-gradient(135deg, #ff2d55, #ff6b9d, #a855f7);
  }

  body {
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    padding-bottom: 80px;
  }

  /* ===== HEADER ===== */
  header {
    background: rgba(10,10,15,0.95);
    backdrop-filter: blur(20px);
    padding: 12px 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid var(--border);
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .logo {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .logo-icone {
    width: 40px;
    height: 40px;
    background: var(--grad);
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    box-shadow: 0 0 20px rgba(255,45,85,0.5);
  }

  .logo-texto {
    font-size: 20px;
    font-weight: 800;
    background: var(--grad);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .header-acoes {
    display: flex;
    gap: 8px;
    align-items: center;
  }

  .btn-icone {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: var(--card2);
    border: 1px solid var(--border);
    color: var(--text);
    font-size: 18px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    transition: 0.2s;
  }

  .btn-icone:hover { background: var(--accent); border-color: var(--accent); }

  .notif-badge {
    position: absolute;
    top: -2px;
    right: -2px;
    background: var(--accent);
    color: white;
    font-size: 10px;
    padding: 2px 5px;
    border-radius: 10px;
    font-weight: bold;
  }

  /* ===== PESQUISA ===== */
  .pesquisa-box {
    padding: 12px 16px;
    background: var(--bg);
    border-bottom: 1px solid var(--border);
  }

  .pesquisa-box input {
    width: 100%;
    padding: 12px 16px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 25px;
    color: var(--text);
    font-size: 14px;
    outline: none;
    transition: 0.2s;
  }

  .pesquisa-box input:focus {
    border-color: var(--accent);
    box-shadow: 0 0 0 3px rgba(255,45,85,0.15);
  }

  /* ===== CONTEÚDO ===== */
  main {
    max-width: 600px;
    margin: 0 auto;
    padding: 16px;
  }

  /* ===== CRIAR POST ===== */
  .criar-post {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 16px;
    margin-bottom: 16px;
  }

  .criar-post-topo {
    display: flex;
    gap: 12px;
    align-items: flex-start;
    margin-bottom: 12px;
  }

  .avatar {
    width: 44px;
    height: 44px;
    border-radius: 50%;
    background: var(--grad);
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    font-size: 18px;
    flex-shrink: 0;
    color: white;
  }

  .criar-post textarea {
    flex: 1;
    background: var(--card2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 12px;
    color: var(--text);
    font-size: 15px;
    resize: none;
    min-height: 60px;
    outline: none;
    font-family: inherit;
  }

  .criar-post textarea:focus { border-color: var(--accent); }

  .criar-post-acoes {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .btn-publicar {
    padding: 10px 24px;
    background: var(--grad);
    color: white;
    border: none;
    border-radius: 25px;
    font-weight: bold;
    font-size: 14px;
    cursor: pointer;
    transition: 0.2s;
  }

  .btn-publicar:hover { transform: scale(1.05); box-shadow: 0 5px 20px rgba(255,45,85,0.4); }
  .btn-publicar:disabled { opacity: 0.4; cursor: not-allowed; }

  /* ===== ABAS ===== */
  .abas {
    display: flex;
    gap: 4px;
    background: var(--card);
    padding: 4px;
    border-radius: 12px;
    margin-bottom: 16px;
    border: 1px solid var(--border);
  }

  .aba {
    flex: 1;
    padding: 10px;
    background: transparent;
    border: none;
    color: var(--text2);
    font-weight: 600;
    font-size: 14px;
    border-radius: 8px;
    cursor: pointer;
    transition: 0.2s;
  }

  .aba.ativo { background: var(--accent); color: white; }

  /* ===== POST ===== */
  .post {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 16px;
    margin-bottom: 12px;
    animation: aparecer 0.4s ease;
  }

  @keyframes aparecer {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .post-topo {
    display: flex;
    gap: 12px;
    align-items: center;
    margin-bottom: 12px;
  }

  .post-info { flex: 1; }

  .post-nome {
    font-weight: bold;
    font-size: 15px;
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .verificado { color: var(--accent); font-size: 14px; }

  .post-tempo { color: var(--text2); font-size: 13px; }

  .post-texto {
    font-size: 15px;
    line-height: 1.5;
    margin-bottom: 12px;
    word-wrap: break-word;
  }

  .post-imagem {
    width: 100%;
    border-radius: 12px;
    margin-bottom: 12px;
    max-height: 400px;
    object-fit: cover;
  }

  .post-acoes {
    display: flex;
    gap: 20px;
    padding-top: 12px;
    border-top: 1px solid var(--border);
  }

  .acao-post {
    display: flex;
    align-items: center;
    gap: 6px;
    background: none;
    border: none;
    color: var(--text2);
    cursor: pointer;
    font-size: 14px;
    font-weight: 600;
    transition: 0.2s;
    padding: 4px 8px;
    border-radius: 8px;
  }

  .acao-post:hover { background: var(--card2); color: var(--text); }
  .acao-post.curtido { color: var(--accent); }
  .acao-post.guardado { color: #ffd700; }

  /* ===== COMENTÁRIOS ===== */
  .comentarios {
    margin-top: 12px;
    padding-top: 12px;
    border-top: 1px solid var(--border);
    display: none;
  }

  .comentarios.aberto { display: block; }

  .comentario {
    display: flex;
    gap: 8px;
    margin-bottom: 10px;
    font-size: 14px;
  }

  .comentario .avatar {
    width: 32px;
    height: 32px;
    font-size: 14px;
  }

  .comentario-texto b { color: var(--accent2); }

  .add-comentario {
    display: flex;
    gap: 8px;
    margin-top: 8px;
  }

  .add-comentario input {
    flex: 1;
    padding: 8px 12px;
    background: var(--card2);
    border: 1px solid var(--border);
    border-radius: 20px;
    color: var(--text);
    font-size: 14px;
    outline: none;
  }

  .add-comentario input:focus { border-color: var(--accent); }

  .add-comentario button {
    padding: 8px 16px;
    background: var(--accent);
    color: white;
    border: none;
    border-radius: 20px;
    font-weight: bold;
    cursor: pointer;
    font-size: 13px;
  }

  /* ===== BARRA INFERIOR ===== */
  .barra-inferior {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    background: rgba(10,10,15,0.95);
    backdrop-filter: blur(20px);
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 100;
  }

  .nav-btn {
    background: none;
    border: none;
    color: var(--text2);
    font-size: 24px;
    cursor: pointer;
    padding: 8px 20px;
    border-radius: 12px;
    transition: 0.2s;
    position: relative;
  }

  .nav-btn.ativo { color: var(--accent); }

  /* ===== MODAIS ===== */
  .modal {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.85);
    backdrop-filter: blur(10px);
    z-index: 200;
    justify-content: center;
    align-items: center;
    padding: 16px;
  }

  .modal.ativo { display: flex; }

  .modal-conteudo {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 24px;
    width: 100%;
    max-width: 400px;
    max-height: 90vh;
    overflow-y: auto;
    animation: aparecer 0.3s;
  }

  .modal-conteudo h2 {
    margin-bottom: 20px;
    background: var(--grad);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    font-size: 24px;
    text-align: center;
  }

  .campo {
    width: 100%;
    padding: 12px 16px;
    background: var(--card2);
    border: 1px solid var(--border);
    border-radius: 12px;
    color: var(--text);
    font-size: 15px;
    margin-bottom: 12px;
    outline: none;
    font-family: inherit;
  }

  .campo:focus { border-color: var(--accent); }

  .btn-principal {
    width: 100%;
    padding: 14px;
    background: var(--grad);
    color: white;
    border: none;
    border-radius: 12px;
    font-weight: bold;
    font-size: 15px;
    cursor: pointer;
    transition: 0.2s;
    margin-bottom: 8px;
  }

  .btn-principal:hover { transform: scale(1.02); }

  .btn-secundario {
    width: 100%;
    padding: 14px;
    background: var(--card2);
    color: var(--text);
    border: 1px solid var(--border);
    border-radius: 12px;
    font-weight: bold;
    font-size: 15px;
    cursor: pointer;
  }

  /* ===== PERFIL ===== */
  .perfil-capa {
    height: 120px;
    background: var(--grad);
    border-radius: 16px 16px 0 0;
  }

  .perfil-info {
    background: var(--card);
    border: 1px solid var(--border);
    border-top: none;
    border-radius: 0 0 16px 16px;
    padding: 16px;
    margin-bottom: 16px;
    position: relative;
  }

  .perfil-avatar {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background: var(--grad);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 32px;
    font-weight: bold;
    border: 4px solid var(--card);
    position: absolute;
    top: -40px;
    left: 20px;
  }

  .perfil-nome {
    margin-top: 40px;
    font-size: 20px;
    font-weight: bold;
  }

  .perfil-user { color: var(--text2); font-size: 14px; margin-bottom: 10px; }

  .perfil-bio { font-size: 14px; line-height: 1.5; margin-bottom: 12px; }

  .perfil-stats {
    display: flex;
    gap: 20px;
    font-size: 14px;
  }

  .perfil-stats b { color: var(--accent); }

  /* ===== VAZIO ===== */
  .vazio {
    text-align: center;
    padding: 60px 20px;
    color: var(--text2);
  }

  .vazio-emoji { font-size: 60px; margin-bottom: 16px; }

  /* ===== RESPONSIVO ===== */
  @media (min-width: 768px) {
    main { padding: 24px; }
  }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="logo">
    <div class="logo-icone">✨</div>
    <div class="logo-texto">Tudo Acontece</div>
  </div>
  <div class="header-acoes">
    <button class="btn-icone" onclick="abrirNotificacoes()">
      🔔
      <span class="notif-badge" id="notifBadge" style="display:none;">0</span>
    </button>
    <button class="btn-icone" onclick="abrirPerfil()">👤</button>
  </div>
</header>

<!-- PESQUISA -->
<div class="pesquisa-box">
  <input type="text" id="pesquisa" placeholder="🔍 Pesquisar posts, pessoas..." oninput="pesquisar()">
</div>

<!-- CONTEÚDO -->
<main>
  <!-- CRIAR POST -->
  <div class="criar-post" id="criarPostBox">
    <div class="criar-post-topo">
      <div class="avatar" id="avatarUser">?</div>
      <textarea id="textoPost" placeholder="O que está a acontecer?"></textarea>
    </div>
    <div class="criar-post-acoes">
      <span style="color:var(--text2);font-size:13px;" id="contador">0/280</span>
      <button class="btn-publicar" id="btnPublicar" onclick="publicar()" disabled>Publicar</button>
    </div>
  </div>

  <!-- ABAS -->
  <div class="abas">
    <button class="aba ativo" onclick="mudarAba('todos', this)">🌍 Todos</button>
    <button class="aba" onclick="mudarAba('seguindo', this)">👥 Seguindo</button>
    <button class="aba" onclick="mudarAba('guardados', this)">🔖 Guardados</button>
    <button class="aba" onclick="mudarAba('trending', this)">🔥 Trending</button>
  </div>

  <!-- FEED -->
  <div id="feed"></div>
</main>

<!-- BARRA INFERIOR -->
<div class="barra-inferior">
  <button class="nav-btn ativo" onclick="mudarAba('todos', this)">🏠</button>
  <button class="nav-btn" onclick="abrirExplorar()">🔍</button>
  <button class="nav-btn" onclick="abrirCriarPost()">➕</button>
  <button class="nav-btn" onclick="abrirNotificacoes()">🔔</button>
  <button class="nav-btn" onclick="abrirPerfil()">👤</button>
</div>

<!-- MODAL GENÉRICO -->
<div class="modal" id="modal">
  <div class="modal-conteudo" id="modalConteudo"></div>
</div>

<script>
/* ============================================
   BANCO DE DADOS
============================================ */
let posts = JSON.parse(localStorage.getItem('ta_posts')) || [
  { id: 1, autor: 'Stock do Cuito', user: '@stockcuito', texto: '🔥 Promoção: Telemóvel Samsung a 45.000 Kz! Aproveita agora. #promoção #cuito', tempo: Date.now() - 3600000, likes: 24, curtido: false, guardado: false, comentarios: [
    { autor: 'Ana', texto: 'Quero um!' },
    { autor: 'Carlos', texto: 'Bom preço!' }
  ]},
  { id: 2, autor: 'Maria Silva', user: '@mariia', texto: 'Hoje o dia está lindo no Cuito! ☀️ Alguém quer passear?', tempo: Date.now() - 7200000, likes: 12, curtido: false, guardado: false, comentarios: [] },
  { id: 3, autor: 'Tech Angola', user: '@techangola', texto: 'Novo curso de programação GRÁTIS no YouTube! Link na bio. 🚀 #programação', tempo: Date.now() - 10800000, likes: 45, curtido: false, guardado: false, comentarios: [
    { autor: 'João', texto: 'Já me inscrevi!' }
  ]}
];

let usuario = JSON.parse(localStorage.getItem('ta_user')) || {
  nome: 'Visitante',
  user: '@visitante',
  bio: 'Bem-vindo ao Tudo Acontece!',
  seguidores: 0,
  seguindo: 0
};

let abaAtual = 'todos';
let notificacoes = JSON.parse(localStorage.getItem('ta_notif')) || [];

/* ============================================
   RENDERIZAR FEED
============================================ */
function renderizarFeed(lista = null) {
  const feed = document.getElementById('feed');
  let listaFiltrada = lista || posts;

  if (abaAtual === 'guardados') {
    listaFiltrada = posts.filter(p => p.guardado);
  } else if (abaAtual === 'trending') {
    listaFiltrada = [...posts].sort((a, b) => b.likes - a.likes);
  }

  if (listaFiltrada.length === 0) {
    feed.innerHTML = `
      <div class="vazio">
        <div class="vazio-emoji">📭</div>
        <p>Nada por aqui ainda.</p>
        <p style="font-size:13px;margin-top:8px;">Sê o primeiro a publicar!</p>
      </div>`;
    return;
  }

  feed.innerHTML = listaFiltrada.map(p => `
    <div class="post">
      <div class="post-topo">
        <div class="avatar">${p.autor[0].toUpperCase()}</div>
        <div class="post-info">
          <div class="post-nome">${p.autor} ${p.autor === 'Stock do Cuito' ? '<span class="verificado">✓</span>' : ''}</div>
          <div class="post-tempo">${p.user} · ${tempoAtras(p.tempo)}</div>
        </div>
      </div>
      <div class="post-texto">${destacar(p.texto)}</div>
      <div class="post-acoes">
        <button class="acao-post ${p.curtido ? 'curtido' : ''}" onclick="curtir(${p.id})">
          ${p.curtido ? '❤️' : '🤍'} ${p.likes}
        </button>
        <button class="acao-post" onclick="toggleComentarios(${p.id})">
          💬 ${p.comentarios.length}
        </button>
        <button class="acao-post ${p.guardado ? 'guardado' : ''}" onclick="guardar(${p.id})">
          ${p.guardado ? '🔖' : '📑'}
        </button>
        <button class="acao-post" onclick="partilhar(${p.id})">📤</button>
      </div>
      <div class="comentarios" id="com-${p.id}">
        ${p.comentarios.map(c => `
          <div class="comentario">
            <div class="avatar">${c.autor[0].toUpperCase()}</div>
            <div class="comentario-texto"><b>${c.autor}</b> ${c.texto}</div>
          </div>
        `).join('')}
        <div class="add-comentario">
          <input placeholder="Escreve um comentário..." onkeypress="if(event.key==='Enter') comentar(${p.id}, this)">
          <button onclick="comentar(${p.id}, this.previousElementSibling)">Enviar</button>
        </div>
      </div>
    </div>
  `).join('');
}

/* ============================================
   AÇÕES
============================================ */
function publicar() {
  const texto = document.getElementById('textoPost').value.trim();
  if (!texto) return;

  const novo = {
    id: Date.now(),
    autor: usuario.nome,
    user: usuario.user,
    texto,
    tempo: Date.now(),
    likes: 0,
    curtido: false,
    guardado: false,
    comentarios: []
  };

  posts.unshift(novo);
  salvar();
  document.getElementById('textoPost').value = '';
  document.getElementById('contador').textContent = '0/280';
  document.getElementById('btnPublicar').disabled = true;
  renderizarFeed();
  adicionarNotificacao('Publicaste um novo post! ✨');
}

function curtir(id) {
  const p = posts.find(x => x.id === id);
  if (!p) return;
  p.curtido = !p.curtido;
  p.likes += p.curtido ? 1 : -1;
  salvar();
  renderizarFeed();
}

function guardar(id) {
  const p = posts.find(x => x.id === id);
  if (!p) return;
  p.guardado = !p.guardado;
  salvar();
  renderizarFeed();
  adicionarNotificacao(p.guardado ? 'Post guardado! 🔖' : 'Post removido dos guardados.');
}

function toggleComentarios(id) {
  const el = document.getElementById('com-' + id);
  el.classList.toggle('aberto');
}

function comentar(id, input) {
  const texto = input.value.trim();
  if (!texto) return;
  const p = posts.find(x => x.id === id);
  p.comentarios.push({ autor: usuario.nome, texto });
  salvar();
  renderizarFeed();
  adicionarNotificacao('Comentaste num post! 💬');
}

function partilhar(id) {
  const p = posts.find(x => x.id === id);
  const texto = `"${p.texto}" — ${p.autor} no Tudo Acontece`;
  if (navigator.share) {
    navigator.share({ title: 'Tudo Acontece', text: texto });
  } else {
    navigator.clipboard.writeText(texto);
    alert('✅ Texto copiado! Cola onde quiseres partilhar.');
  }
}

/* ============================================
   PESQUISA
============================================ */
function pesquisar() {
  const termo = document.getElementById('pesquisa').value.toLowerCase();
  if (!termo) { renderizarFeed(); return; }
  const resultado = posts.filter(p =>
    p.texto.toLowerCase().includes(termo) ||
    p.autor.toLowerCase().includes(termo) ||
    p.user.toLowerCase().includes(termo)
  );
  renderizarFeed(resultado);
}

/* ============================================
   ABAS
============================================ */
function mudarAba(aba, btn) {
  abaAtual = aba;
  document.querySelectorAll('.aba').forEach(b => b.classList.remove('ativo'));
  if (btn && btn.classList.contains('aba')) btn.classList.add('ativo');
  renderizarFeed();
}

/* ============================================
   PERFIL
============================================ */
function abrirPerfil() {
  const modal = document.getElementById('modal');
  document.getElementById('modalConteudo').innerHTML = `
    <div class="perfil-capa"></div>
    <div class="perfil-info">
      <div class="perfil-avatar">${usuario.nome[0].toUpperCase()}</div>
      <div class="perfil-nome">${usuario.nome}</div>
      <div class="perfil-user">${usuario.user}</div>
      <div class="perfil-bio">${usuario.bio}</div>
      <div class="perfil-stats">
        <div><b>${posts.filter(p => p.autor === usuario.nome).length}</b> posts</div>
        <div><b>${usuario.seguidores}</b> seguidores</div>
        <div><b>${usuario.seguindo}</b> seguindo</div>
      </div>
    </div>
    <input class="campo" id="editNome" placeholder="Teu nome" value="${usuario.nome}">
    <input class="campo" id="editUser" placeholder="@username# Tudo-acontece-aqui-na-banda
