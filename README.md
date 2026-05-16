<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Painel de Otimização</title>
    <style>
        /* Estilização Geral */
        body {
            margin: 0;
            padding: 0;
            background-color: #0d0d11;
            font-family: 'Segoe UI', Arial, sans-serif;
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        /* Container Principal do Painel */
        .panel-container {
            width: 340px;
            background: #16161a;
            border: 1px solid #333;
            border-radius: 14px;
            padding: 24px;
            box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.7);
        }

        h2 {
            margin: 0 0 5px 0;
            color: #00ff88;
            font-size: 20px;
            text-transform: uppercase;
            letter-spacing: 1px;
            text-align: center;
        }

        .subtitle {
            font-size: 12px;
            color: #777;
            text-align: center;
            margin-bottom: 25px;
            text-transform: uppercase;
        }

        /* Estrutura das Linhas de Função */
        .function-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #1f1f24;
            padding: 12px 16px;
            margin-bottom: 12px;
            border-radius: 8px;
            border: 1px solid #2a2a30;
        }

        .function-info {
            display: flex;
            flex-direction: column;
        }

        .function-name {
            font-size: 15px;
            font-weight: 600;
        }

        .function-desc {
            font-size: 11px;
            color: #aaa;
            margin-top: 2px;
        }

        /* Botão Estilo Toggle/Alternar */
        .btn-toggle {
            padding: 8px 16px;
            background: #2a2a30;
            border: 1px solid #444;
            color: #ccc;
            font-size: 12px;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.2s ease;
            min-width: 80px;
            text-transform: uppercase;
        }

        /* Estado quando a função está ligada */
        .btn-toggle.active {
            background: rgba(0, 255, 136, 0.15);
            border-color: #00ff88;
            color: #00ff88;
            box-shadow: 0 0 10px rgba(0, 255, 136, 0.2);
        }

        hr {
            border: 0;
            height: 1px;
            background: #2a2a30;
            margin: 20px 0;
        }

        /* Botão Injetar / Abrir */
        .btn-launch {
            width: 100%;
            padding: 14px;
            background: #00ff88;
            border: none;
            color: #0d0d11;
            font-size: 16px;
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: background 0.2s;
        }

        .btn-launch:hover {
            background: #00dd77;
        }
    </style>
</head>
<body>

    <div class="panel-container">
        <h2>Booster Panel</h2>
        <div class="subtitle">Módulos de Desempenho</div>
        
        <!-- Função 1: Otimizar FPS -->
        <div class="function-row">
            <div class="function-info">
                <span class="function-name">Otimizar Geral</span>
                <span class="function-desc">Reduz processos em segundo plano</span>
            </div>
            <button class="btn-toggle" id="opt-geral" onclick="toggleFunction('opt-geral')">OFF</button>
        </div>

        <!-- Função 2: Forçar 120 FPS -->
        <div class="function-row">
            <div class="function-info">
                <span class="function-name">Liberar 120 FPS</span>
                <span class="function-desc">Remove o limitador da engine</span>
            </div>
            <button class="btn-toggle" id="opt-fps" onclick="toggleFunction('opt-fps')">OFF</button>
        </div>

        <!-- Função 3: Limpar Memória RAM -->
        <div class="function-row">
            <div class="function-info">
                <span class="function-name">Limpar RAM</span>
                <span class="function-desc">Esvazia o cache do sistema</span>
            </div>
            <button class="btn-toggle" id="opt-ram" onclick="toggleFunction('opt-ram')">OFF</button>
        </div>

        <hr>

        <!-- Botão Executar -->
        <button class="btn-launch" onclick="executarEIniciar()">Injetar & Abrir FF</button>
    </div>

    <script>
        // Objeto para guardar quais funções estão ativadas
        const funcoesAtivas = {
            'opt-geral': false,
            'opt-fps': false,
            'opt-ram': false
        };

        // Função para ligar/desligar os botões individuais
        function toggleFunction(id) {
            const botao = document.getElementById(id);
            
            // Inverte o estado atual
            funcoesAtivas[id] = !funcoesAtivas[id];

            if (funcoesAtivas[id]) {
                botao.innerText = "ON";
                botao.classList.add('active');
            } else {
                botao.innerText = "OFF";
                botao.classList.remove('active');
            }
        }

        // Função do botão principal embaixo
        function executarEIniciar() {
            // Verifica o que o usuário ativou para exibir no aviso
            let modulosAtivados = [];
            if (funcoesAtivas['opt-geral']) modulosAtivados.push("Otimização Geral");
            if (funcoesAtivas['opt-fps']) modulosAtivados.push("120 FPS");
            if (funcoesAtivas['opt-ram']) modulosAtivados.push("Limpeza de RAM");

            if (modulosAtivados.length === 0) {
                alert("Nenhuma otimização selecionada. Abrindo o jogo padrão...");
            } else {
                alert("Aplicando: " + modulosAtivados.join(", ") + "\nIniciando o Free Fire!");
            }

            // Comando para tentar abrir o aplicativo através do navegador
            window.location.href = "freefire://";
        }
    </script>

</body>
</html>
