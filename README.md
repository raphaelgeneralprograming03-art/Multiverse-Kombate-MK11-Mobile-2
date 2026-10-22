
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multiverse Kombat 11 Mobile - Módulo 2</title>
    <style>
        :root {
            --gold: #d4af37;
            --dark-bg: #0a0a0d;
            --panel-bg: #14141a;
            --card-border: #2e2e38;
            --red-glow: #ef4444;
            --blue-glow: #3b82f6;
            --diamond-glow: #a855f7;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            user-select: none;
        }

        body {
            background-color: var(--dark-bg);
            color: #f3f4f6;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            padding: 10px;
        }

        header {
            width: 100%;
            max-width: 1050px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(90deg, #181820, #09090d);
            border: 2px solid var(--gold);
            padding: 10px 20px;
            border-radius: 6px;
            margin-bottom: 12px;
            box-shadow: 0 0 15px rgba(212, 175, 55, 0.2);
        }

        h1 {
            color: var(--gold);
            font-size: 1.3rem;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .currencies {
            display: flex;
            gap: 12px;
            font-size: 0.85rem;
            font-weight: bold;
        }

        .curr-item {
            display: flex;
            align-items: center;
            gap: 5px;
            background: #22222b;
            padding: 5px 12px;
            border-radius: 4px;
            border: 1px solid #383846;
        }

        /* NAVEGAÇÃO PRINCIPAL MK11 MOBILE */
        nav.menu-bar {
            width: 100%;
            max-width: 1050px;
            display: flex;
            gap: 8px;
            margin-bottom: 12px;
        }

        .nav-btn {
            flex: 1;
            background: #181820;
            border: 1px solid #383846;
            color: #a1a1aa;
            padding: 10px;
            font-weight: bold;
            font-size: 0.85rem;
            text-transform: uppercase;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.2s;
            text-align: center;
        }

        .nav-btn.active, .nav-btn:hover {
            background: var(--gold);
            color: #000;
            border-color: var(--gold);
            box-shadow: 0 0 10px rgba(212, 175, 55, 0.4);
        }

        .app-container {
            width: 100%;
            max-width: 1050px;
            background: var(--panel-bg);
            border: 2px solid var(--card-border);
            border-radius: 8px;
            padding: 15px;
            min-height: 550px;
        }

        .tab-content {
            display: none;
            flex-direction: column;
            gap: 15px;
        }

        .tab-content.active {
            display: flex;
        }

        .section-title {
            color: var(--gold);
            font-size: 1.1rem;
            text-transform: uppercase;
            border-bottom: 1px solid var(--gold);
            padding-bottom: 5px;
            display: flex;
            justify-content: space-between;
        }

        /* LOJA DE PACOTES (PACK STORE) */
        .store-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 15px;
        }

        .pack-card {
            background: linear-gradient(145deg, #1e1e28, #111118);
            border: 2px solid var(--gold);
            border-radius: 8px;
            padding: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            gap: 10px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.5);
            position: relative;
            overflow: hidden;
        }

        .pack-card.diamond {
            border-color: var(--diamond-glow);
            box-shadow: 0 0 15px rgba(168, 85, 247, 0.3);
        }

        .pack-title {
            font-size: 1.1rem;
            font-weight: bold;
            color: #fff;
        }

        .pack-price {
            font-size: 1rem;
            font-weight: bold;
            color: var(--gold);
            background: #272736;
            padding: 6px 15px;
            border-radius: 20px;
            border: 1px solid var(--gold);
        }

        .btn-buy {
            width: 100%;
            background: linear-gradient(135deg, #22c55e, #15803d);
            border: none;
            color: #fff;
            padding: 10px;
            font-weight: bold;
            font-size: 0.95rem;
            border-radius: 4px;
            cursor: pointer;
            text-transform: uppercase;
            transition: 0.2s;
        }

        .btn-buy:hover {
            background: linear-gradient(135deg, #4ade80, #16a34a);
            box-shadow: 0 0 12px rgba(34, 197, 94, 0.5);
        }

        /* COLEÇÃO E FUSÃO DE CARTAS */
        .collection-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 12px;
        }

        .card-item {
            background: #1e1e2a;
            border: 2px solid #383848;
            border-radius: 6px;
            padding: 10px;
            display: flex;
            flex-direction: column;
            align-items: center;
            position: relative;
        }

        .card-item.gold-tier { border-color: var(--gold); }
        .card-item.diamond-tier { border-color: var(--diamond-glow); box-shadow: 0 0 8px rgba(168, 85, 247, 0.4); }

        .card-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: bold;
            color: #fff;
            margin-bottom: 8px;
            border: 2px solid #fff;
        }

        .fusion-badge {
            position: absolute;
            top: 6px;
            right: 6px;
            background: var(--gold);
            color: #000;
            font-weight: bold;
            font-size: 0.7rem;
            padding: 2px 6px;
            border-radius: 3px;
        }

        .card-stats {
            width: 100%;
            font-size: 0.75rem;
            color: #a1a1aa;
            margin-top: 6px;
            display: flex;
            justify-content: space-between;
        }

        /* TORRES DE DESAFIO (CAMPANHA) */
        .towers-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 15px;
        }

        .tower-card {
            background: #181822;
            border: 2px solid #383848;
            border-radius: 6px;
            padding: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
            text-align: center;
        }

        .tower-card.active {
            border-color: var(--red-glow);
            box-shadow: 0 0 12px rgba(239, 68, 68, 0.3);
        }

        /* RESULTADO DA ABERTURA DE PACOTE (POPUP) */
        .modal-overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.85);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 100;
        }

        .modal-card-reveal {
            background: #1e1e2a;
            border: 3px solid var(--gold);
            border-radius: 8px;
            padding: 25px;
            width: 300px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 12px;
            box-shadow: 0 0 30px var(--gold);
            text-align: center;
            animation: popIn 0.3s ease-out;
        }

        @keyframes popIn {
            0% { transform: scale(0.5); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }
    </style>
</head>
<body>

    <header>
        <h1>Multiverse Kombat 11</h1>
        <div class="currencies">
            <div class="curr-item">🪙 <span id="coins-display">250,000</span></div>
            <div class="curr-item">💎 <span id="souls-display">1,500</span></div>
        </div>
    </header>

    <!-- MENU DE NAVEGAÇÃO ENTRE MÓDULOS -->
    <nav class="menu-bar">
        <div class="nav-btn active" onclick="switchTab('team')">1. Equipe & Luta</div>
        <div class="nav-btn" onclick="switchTab('collection')">2. Minha Coleção</div>
        <div class="nav-btn" onclick="switchTab('store')">3. Loja de Pacotes</div>
        <div class="nav-btn" onclick="switchTab('towers')">4. Torres de Desafio</div>
    </nav>

    <div class="app-container">
        
        <!-- MÓDULO 1: SELEÇÃO DE TIME E ADVERSÁRIO -->
        <div id="tab-team" class="tab-content active">
            <div class="section-title">
                <span>Seleção de Equipe & Oponente</span>
                <span style="font-size: 0.8rem; color: #a1a1aa;">Módulo 1 + 2</span>
            </div>
            <p style="font-size: 0.85rem; color: #a1a1aa;">Monte seu time com as cartas adquiridas na sua Coleção e escolha o adversário para combater!</p>

            <div style="display: flex; gap: 15px; flex-wrap: wrap;">
                <div style="flex: 1; background: #191922; padding: 10px; border-radius: 6px;">
                    <div style="font-size: 0.85rem; font-weight: bold; color: #22c55e;">SUA EQUIPE (3 SLOTS)</div>
                    <div style="display: flex; gap: 10px; margin-top: 10px;" id="team-slots-box"></div>
                </div>
                <div style="flex: 0.4; background: #191922; padding: 10px; border-radius: 6px;">
                    <div style="font-size: 0.85rem; font-weight: bold; color: var(--red-glow);">OPONENTE</div>
                    <div style="margin-top: 10px;" id="enemy-slot-box"></div>
                </div>
            </div>

            <button style="background: linear-gradient(135deg, #b91c1c, #7f1d1d); border: 2px solid #ef4444; color: #fff; padding: 12px; font-weight: bold; border-radius: 6px; cursor: pointer; text-transform: uppercase; font-size: 1rem; margin-top: 15px;" onclick="alert('Iniciando arena de combate do Módulo 1!')">
                Ir Para a Arena de Combate ⚔️
            </button>
        </div>

        <!-- MÓDULO 2: COLEÇÃO E FUSÃO DE CARTAS -->
        <div id="tab-collection" class="tab-content">
            <div class="section-title">
                <span>Coleção de Cartas & Fusão (Evolução)</span>
                <span style="font-size: 0.8rem; color: var(--gold);" id="owned-count">0 Cartas</span>
            </div>
            <div class="collection-grid" id="collectionGrid"></div>
        </div>

        <!-- MÓDULO 2: LOJA DE PACOTES (PACK STORE) -->
        <div id="tab-store" class="tab-content">
            <div class="section-title">Loja de Pacotes do Multiverso</div>
            <div class="store-grid">
                <!-- PACOTE OURO -->
                <div class="pack-card">
                    <div class="pack-title">Pacote Ouro do Multiverso</div>
                    <p style="font-size: 0.8rem; color: #a1a1aa;">Contém 1 Carta Ouro garantida (Mortal Kombat, Marvel, DC ou X-Men).</p>
                    <div class="pack-price">🪙 50,000 Moedas</div>
                    <button class="btn-buy" onclick="buyPack('gold')">Abrir Pacote</button>
                </div>

                <!-- PACOTE DIAMANTE -->
                <div class="pack-card diamond">
                    <div class="pack-title" style="color: var(--diamond-glow);">Pacote Diamante Celestial</div>
                    <p style="font-size: 0.8rem; color: #a1a1aa;">Alta chance de invocar lutadores supremos de Raridade Diamante!</p>
                    <div class="pack-price" style="border-color: var(--diamond-glow); color: var(--diamond-glow);">💎 400 Gemas</div>
                    <button class="btn-buy" style="background: linear-gradient(135deg, #a855f7, #6b21a8);" onclick="buyPack('diamond')">Abrir Pacote</button>
                </div>
            </div>
        </div>

        <!-- MÓDULO 2: TORRES DE DESAFIO -->
        <div id="tab-towers" class="tab-content">
            <div class="section-title">Torres de Desafio Klassic</div>
            <div class="towers-container">
                <div class="tower-card active">
                    <div style="font-weight: bold; color: var(--gold);">Torre 1: Arena do Hellspawn</div>
                    <p style="font-size: 0.75rem; color: #aaa;">5 Partidas • Chefe: Spawn</p>
                    <div style="font-size: 0.8rem; color: #22c55e;">Recompensa: 🪙 20,000</div>
                    <button class="btn-buy" onclick="alert('Iniciando Desafio da Torre 1!')">Desafiar</button>
                </div>
                <div class="tower-card">
                    <div style="font-weight: bold; color: var(--gold);">Torre 2: Crise nos Multiversos</div>
                    <p style="font-size: 0.75rem; color: #aaa;">7 Partidas • Chefe: Superman</p>
                    <div style="font-size: 0.8rem; color: #22c55e;">Recompensa: 💎 150 Gemas</div>
                    <button class="btn-buy" style="opacity: 0.5;" disabled>Bloqueado</button>
                </div>
            </div>
        </div>

    </div>

    <!-- MODAL DE REVELAÇÃO DA CARTA COMPRADA -->
    <div class="modal-overlay" id="revealModal">
        <div class="modal-card-reveal" id="modalContent"></div>
    </div>

    <script>
        let coins = 250000;
        let souls = 1500;

        // BANCO DE DADOS DE CARTAS E FUSÕES
        const allCards = [
            { id: 'spawn', name: 'Spawn', universe: 'Image Comics', tier: 'Diamante', atk: 1200, hp: 1400, color: '#00ff66', fusion: 0, owned: true },
            { id: 'scorpion', name: 'Scorpion', universe: 'Mortal Kombat', tier: 'Ouro', atk: 950, hp: 900, color: '#f59e0b', fusion: 0, owned: true },
            { id: 'subzero', name: 'Sub-Zero', universe: 'Mortal Kombat', tier: 'Ouro', atk: 900, hp: 950, color: '#38bdf8', fusion: 0, owned: true },
            { id: 'wolverine', name: 'Wolverine', universe: 'X-Men / Marvel', tier: 'Ouro', atk: 1050, hp: 1100, color: '#eab308', fusion: 0, owned: true },
            { id: 'batman', name: 'Batman', universe: 'DC Comics', tier: 'Ouro', atk: 880, hp: 1000, color: '#64748b', fusion: 0, owned: false },
            { id: 'ironman', name: 'Homem de Ferro', universe: 'Marvel Comics', tier: 'Ouro', atk: 920, hp: 890, color: '#ef4444', fusion: 0, owned: false },
            { id: 'superman', name: 'Superman', universe: 'DC Comics', tier: 'Diamante', atk: 1300, hp: 1500, color: '#2563eb', fusion: 0, owned: false },
            { id: 'phoenix', name: 'Jean Grey (Fênix)', universe: 'X-Men / Marvel', tier: 'Diamante', atk: 1350, hp: 1200, color: '#f97316', fusion: 0, owned: false }
        ];

        function switchTab(tabId) {
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            document.querySelectorAll('.tab-content').forEach(tab => tab.classList.remove('active'));

            event.target.classList.add('active');
            document.getElementById(`tab-${tabId}`).classList.add('active');

            if (tabId === 'collection') renderCollection();
        }

        function renderCollection() {
            const grid = document.getElementById('collectionGrid');
            grid.innerHTML = '';
            let ownedTotal = 0;

            allCards.forEach(card => {
                if (!card.owned) return;
                ownedTotal++;
                
                const cardEl = document.createElement('div');
                cardEl.className = `card-item ${card.tier === 'Diamante' ? 'diamond-tier' : 'gold-tier'}`;
                
                // Cálculo com multiplicador de Fusão (FX)
                let currentAtk = Math.floor(card.atk * (1 + card.fusion * 0.15));
                let currentHp = Math.floor(card.hp * (1 + card.fusion * 0.15));

                cardEl.innerHTML = `
                    <div class="fusion-badge">F${card.fusion}</div>
                    <div class="card-avatar" style="background: ${card.color}">${card.name[0]}</div>
                    <div style="font-size: 0.85rem; font-weight: bold; text-align: center;">${card.name}</div>
                    <div style="font-size: 0.65rem; color: var(--gold);">${card.universe}</div>
                    <div class="card-stats">
                        <span>⚔️ ${currentAtk}</span>
                        <span>❤️ ${currentHp}</span>
                    </div>
                `;
                grid.appendChild(cardEl);
            });

            document.getElementById('owned-count').innerText = `${ownedTotal} / ${allCards.length} Cartas`;
        }

        function buyPack(type) {
            if (type === 'gold' && coins < 50000) {
                alert("Moedas insuficientes!"); return;
            }
            if (type === 'diamond' && souls < 400) {
                alert("Gemas de Alma insuficientes!"); return;
            }

            if (type === 'gold') coins -= 50000;
            if (type === 'diamond') souls -= 400;
            updateCurrencies();

            // Sorteio de Carta
            let pool = type === 'diamond' ? allCards : allCards.filter(c => c.tier === 'Ouro');
            let drawn = pool[Math.floor(Math.random() * pool.length)];

            if (!drawn.owned) {
                drawn.owned = true;
            } else {
                if (drawn.fusion < 10) drawn.fusion++; // Subir fusão até F10
            }

            showModalReveal(drawn);
        }

        function showModalReveal(card) {
            const modal = document.getElementById('revealModal');
            const content = document.getElementById('modalContent');

            content.innerHTML = `
                <div style="font-size: 0.8rem; color: var(--gold); text-transform: uppercase;">Nova Carta Obtida!</div>
                <div class="card-avatar" style="background: ${card.color}; width: 80px; height: 80px; font-size: 2rem;">${card.name[0]}</div>
                <div style="font-size: 1.2rem; font-weight: bold;">${card.name}</div>
                <div style="font-size: 0.8rem; color: #a1a1aa;">${card.universe} • ${card.tier}</div>
                <div style="font-size: 0.9rem; font-weight: bold; color: #22c55e;">Nível de Fusão: F${card.fusion}</div>
                <button class="btn-buy" onclick="closeModal()">Coletar</button>
            `;

            modal.style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('revealModal').style.display = 'none';
        }

        function updateCurrencies() {
            document.getElementById('coins-display').innerText = coins.toLocaleString();
            document.getElementById('souls-display').innerText = souls.toLocaleString();
        }

        renderCollection();
    </script>
</body>
</html>
