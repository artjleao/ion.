<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🏢 Mestre da Estratégia - Prosperidade</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background: linear-gradient(135deg, #0a2f44, #1b4a6b);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 10px;
            overflow: hidden;
            position: relative;
        }

        /* Efeito de dinheiro caindo no fundo */
        body::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" opacity="0.1"><text x="10" y="20" font-size="20">💰</text><text x="40" y="60" font-size="25">💵</text><text x="70" y="30" font-size="18">💎</text><text x="20" y="80" font-size="22">🪙</text><text x="60" y="90" font-size="24">💶</text><text x="80" y="50" font-size="20">💷</text><text x="30" y="40" font-size="28">💴</text><text x="50" y="15" font-size="22">💎</text><text x="85" y="75" font-size="18">💰</text></svg>');
            background-size: 200px 200px;
            animation: dinheiroCaindo 20s linear infinite;
            pointer-events: none;
            z-index: 0;
        }

        @keyframes dinheiroCaindo {
            0% { background-position: 0 0; }
            100% { background-position: 0 400px; }
        }

        /* Efeito de brilho dourado */
        body::after {
            content: "";
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,215,0,0.1) 0%, transparent 70%);
            animation: brilho 15s ease-in-out infinite;
            pointer-events: none;
            z-index: 0;
        }

        @keyframes brilho {
            0% { transform: rotate(0deg) scale(1); opacity: 0.3; }
            50% { transform: rotate(5deg) scale(1.1); opacity: 0.5; }
            100% { transform: rotate(0deg) scale(1); opacity: 0.3; }
        }

        /* LAYOUT PRINCIPAL - DOIS PAINÉIS */
        .dashboard {
            max-width: 1400px;
            width: 100%;
            height: 96vh;
            display: flex;
            gap: 15px;
            position: relative;
            z-index: 1;
        }

        /* PAINEL ESQUERDO - VISOR E STATUS */
        .painel-esquerdo {
            flex: 1;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(5px);
            border-radius: 40px;
            padding: 20px;
            box-shadow: 0 30px 60px rgba(0,0,0,0.6), 0 0 0 3px gold, 0 0 30px rgba(255,215,0,0.5);
            display: flex;
            flex-direction: column;
            overflow-y: auto;
            position: relative;
            border: none;
        }

        /* PAINEL DIREITO - PERGUNTA E JOGO */
        .painel-direito {
            flex: 1.2;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(5px);
            border-radius: 40px;
            padding: 20px;
            box-shadow: 0 30px 60px rgba(0,0,0,0.6), 0 0 0 3px gold, 0 0 30px rgba(255,215,0,0.5);
            display: flex;
            flex-direction: column;
            overflow-y: auto;
            position: relative;
            border: none;
        }

        /* Scroll personalizado para os painéis */
        .painel-esquerdo::-webkit-scrollbar,
        .painel-direito::-webkit-scrollbar {
            width: 8px;
        }
        
        .painel-esquerdo::-webkit-scrollbar-track,
        .painel-direito::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 10px;
        }
        
        .painel-esquerdo::-webkit-scrollbar-thumb,
        .painel-direito::-webkit-scrollbar-thumb {
            background: gold;
            border-radius: 10px;
            box-shadow: 0 0 10px gold;
        }

        /* Efeito de brilho nos painéis */
        .painel-esquerdo::before,
        .painel-direito::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            border-radius: 40px;
            background: linear-gradient(135deg, rgba(255,215,0,0.2) 0%, transparent 50%, rgba(255,215,0,0.1) 100%);
            pointer-events: none;
        }

        /* TÍTULO PRINCIPAL */
        h1 {
            text-align: center;
            color: #0a2f44;
            font-size: 28px;
            margin-bottom: 15px;
            text-transform: uppercase;
            text-shadow: 2px 2px 0 gold, 0 0 20px rgba(255,215,0,0.5);
            animation: tituloBrilho 2s ease-in-out infinite;
        }

        @keyframes tituloBrilho {
            0% { text-shadow: 2px 2px 0 gold, 0 0 20px rgba(255,215,0,0.5); }
            50% { text-shadow: 2px 2px 0 #f39c12, 0 0 40px rgba(255,215,0,0.8); }
            100% { text-shadow: 2px 2px 0 gold, 0 0 20px rgba(255,215,0,0.5); }
        }

        .subtitulo {
            text-align: center;
            color: #2c3e50;
            margin-bottom: 15px;
            font-style: italic;
            font-size: 14px;
            font-weight: bold;
        }

        /* INDICADOR DE NÍVEL */
        .nivel-indicador {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(135deg, #2c3e50, #34495e);
            padding: 12px 20px;
            border-radius: 40px;
            margin-bottom: 20px;
            color: white;
            font-size: 16px;
            border: 1px solid gold;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        .nivel-badge {
            background: gold;
            color: #2c3e50;
            padding: 8px 25px;
            border-radius: 30px;
            font-weight: bold;
            font-size: 18px;
            animation: badgePulse 2s infinite;
        }

        @keyframes badgePulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); box-shadow: 0 0 20px gold; }
            100% { transform: scale(1); }
        }

        /* COFRE */
        .cofre-container {
            background: linear-gradient(135deg, #2c3e50, #34495e);
            border-radius: 30px;
            padding: 20px;
            margin-bottom: 20px;
            border: 2px solid gold;
            box-shadow: 0 10px 30px rgba(255,215,0,0.3), inset 0 0 20px rgba(255,215,0,0.2);
            position: relative;
            overflow: hidden;
        }

        .cofre-container::before {
            content: "💰💵💎🪙💰💵💎🪙";
            position: absolute;
            top: -20px;
            left: 0;
            width: 100%;
            height: 100%;
            font-size: 40px;
            opacity: 0.1;
            animation: dinheiroGirando 15s linear infinite;
            white-space: nowrap;
            pointer-events: none;
        }

        @keyframes dinheiroGirando {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        .cofre-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            color: white;
            margin-bottom: 15px;
            position: relative;
            z-index: 1;
        }

        .cofre-titulo {
            font-size: 20px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .cofre-valor {
            background: gold;
            color: #2c3e50;
            padding: 8px 25px;
            border-radius: 40px;
            font-size: 28px;
            font-weight: bold;
            box-shadow: 0 0 30px gold;
            animation: valorBrilho 1.5s infinite;
            transition: all 0.3s;
        }

        @keyframes valorBrilho {
            0% { box-shadow: 0 0 20px gold; }
            50% { box-shadow: 0 0 50px gold, 0 0 70px #f39c12; }
            100% { box-shadow: 0 0 20px gold; }
        }

        .cofre-barras {
            display: flex;
            gap: 6px;
            height: 70px;
            align-items: flex-end;
            position: relative;
            z-index: 1;
        }

        .barra-dinheiro {
            flex: 1;
            background: linear-gradient(0deg, #f1c40f, #f39c12, #e67e22);
            border-radius: 12px 12px 0 0;
            transition: height 0.5s;
            min-height: 5px;
            box-shadow: 0 -5px 15px rgba(255,215,0,0.3);
            animation: barraBrilho 2s infinite;
        }

        @keyframes barraBrilho {
            0% { filter: brightness(1); }
            50% { filter: brightness(1.3); }
            100% { filter: brightness(1); }
        }

        /* ALERTAS */
        .alerta-falencia {
            background: linear-gradient(135deg, #e74c3c, #c0392b);
            color: white;
            padding: 12px;
            border-radius: 15px;
            text-align: center;
            font-weight: bold;
            margin-bottom: 20px;
            font-size: 14px;
            display: none;
            border: 2px solid gold;
            box-shadow: 0 0 30px #e74c3c;
            animation: alertaPulse 1s infinite;
        }

        @keyframes alertaPulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.02); box-shadow: 0 0 50px #e74c3c; }
            100% { transform: scale(1); }
        }

        .bonus-ativo {
            background: linear-gradient(135deg, #f39c12, #e67e22, #d35400);
            color: white;
            padding: 8px 25px;
            border-radius: 40px;
            font-weight: bold;
            display: inline-block;
            margin-bottom: 15px;
            font-size: 14px;
            border: 1px solid gold;
            animation: bonusGlow 1s infinite;
        }

        @keyframes bonusGlow {
            0% { box-shadow: 0 0 10px #f39c12; }
            50% { box-shadow: 0 0 40px #f39c12, 0 0 60px gold; }
            100% { box-shadow: 0 0 10px #f39c12; }
        }

        /* STATS */
        .empresa-card {
            background: linear-gradient(135deg, rgba(236, 240, 241, 0.9), rgba(189, 195, 199, 0.9));
            backdrop-filter: blur(5px);
            border-radius: 25px;
            padding: 20px;
            margin-bottom: 20px;
            border: 2px solid gold;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            position: relative;
            overflow: hidden;
        }

        .empresa-card::after {
            content: "💎";
            position: absolute;
            bottom: -10px;
            right: -10px;
            font-size: 60px;
            opacity: 0.1;
            transform: rotate(15deg);
        }

        .empresa-stats {
            display: flex;
            justify-content: space-around;
            margin: 10px 0;
            gap: 10px;
        }

        .stat {
            text-align: center;
            flex: 1;
            background: rgba(255,255,255,0.5);
            padding: 10px;
            border-radius: 20px;
            backdrop-filter: blur(3px);
        }

        .stat-valor {
            font-size: 28px;
            font-weight: bold;
            color: #27ae60;
            text-shadow: 0 0 10px rgba(39, 174, 96, 0.5);
        }

        .stat-label {
            font-size: 12px;
            color: #2c3e50;
            font-weight: bold;
        }

        .sequencia-container {
            background: linear-gradient(135deg, #0a2f44, #1b4a6b);
            color: white;
            padding: 12px;
            border-radius: 20px;
            text-align: center;
            margin: 15px 0;
            font-size: 14px;
            border: 1px solid gold;
            box-shadow: inset 0 0 20px rgba(255,215,0,0.3);
        }

        .barra-progresso {
            height: 15px;
            background: #95a5a6;
            border-radius: 10px;
            overflow: hidden;
            margin: 10px 0;
            border: 1px solid gold;
        }

        .barra-preenchimento {
            height: 100%;
            background: linear-gradient(90deg, #27ae60, #2ecc71, #f1c40f);
            width: 0%;
            transition: width 0.5s;
            box-shadow: 0 0 20px #2ecc71;
        }

        /* PERGUNTAS */
        .pergunta-container {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(5px);
            border-radius: 30px;
            padding: 25px;
            margin-bottom: 20px;
            border: 2px solid gold;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2), inset 0 0 30px rgba(255,215,0,0.2);
            position: relative;
            overflow: hidden;
        }

        .pergunta-container::before {
            content: "❓";
            position: absolute;
            bottom: -30px;
            left: -30px;
            font-size: 150px;
            opacity: 0.05;
            transform: rotate(10deg);
        }

        .dificuldade-tag {
            position: absolute;
            top: -10px;
            right: 20px;
            padding: 5px 20px;
            border-radius: 25px;
            font-weight: bold;
            font-size: 14px;
            border: 2px solid gold;
            box-shadow: 0 5px 10px rgba(0,0,0,0.2);
            z-index: 2;
        }

        .pergunta-numero {
            background: linear-gradient(135deg, #0a2f44, #1b4a6b);
            color: white;
            padding: 8px 25px;
            border-radius: 40px;
            display: inline-block;
            margin-bottom: 15px;
            font-size: 14px;
            border: 1px solid gold;
            box-shadow: 0 5px 10px rgba(0,0,0,0.2);
        }

        .pergunta-texto {
            font-size: 18px;
            color: #2c3e50;
            margin-bottom: 20px;
            font-weight: 600;
            padding-right: 120px;
            text-shadow: 1px 1px 0 rgba(255,215,0,0.3);
        }

        .opcoes {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .opcao {
            background: white;
            border: 2px solid #bdc3c7;
            border-radius: 20px;
            padding: 15px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 15px;
            font-size: 15px;
            box-shadow: 0 5px 10px rgba(0,0,0,0.1);
            position: relative;
            overflow: hidden;
        }

        .opcao::before {
            content: "💰";
            position: absolute;
            right: -20px;
            bottom: -20px;
            font-size: 50px;
            opacity: 0;
            transition: opacity 0.3s;
            transform: rotate(15deg);
        }

        .opcao:hover:not(.disabled) {
            border-color: gold;
            transform: translateX(10px) scale(1.02);
            box-shadow: 0 15px 30px rgba(255,215,0,0.4);
            background: linear-gradient(135deg, white, #fff9e6);
        }

        .opcao:hover:not(.disabled)::before {
            opacity: 0.1;
        }

        .opcao.correta {
            background: linear-gradient(135deg, #d4edda, #c3e6cb);
            border-color: #27ae60;
            box-shadow: 0 0 30px #27ae60;
        }

        .opcao.incorreta {
            background: linear-gradient(135deg, #f8d7da, #f5c6cb);
            border-color: #e74c3c;
        }

        .letra {
            background: linear-gradient(135deg, #0a2f44, #1b4a6b);
            color: white;
            width: 35px;
            height: 35px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 16px;
            box-shadow: 0 3px 8px rgba(0,0,0,0.3);
            border: 1px solid gold;
        }

        /* FEEDBACK */
        .feedback {
            margin-top: 20px;
            padding: 15px;
            border-radius: 20px;
            display: none;
            font-size: 14px;
            font-weight: bold;
            border: 2px solid gold;
            animation: feedbackEntrada 0.3s;
        }

        @keyframes feedbackEntrada {
            0% { transform: scale(0.8); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .feedback.sucesso {
            background: linear-gradient(135deg, #d4edda, #c3e6cb);
            color: #155724;
            display: block;
            border-left: 10px solid #27ae60;
        }

        .feedback.erro {
            background: linear-gradient(135deg, #f8d7da, #f5c6cb);
            color: #721c24;
            display: block;
            border-left: 10px solid #e74c3c;
        }

        .feedback.bonus {
            background: linear-gradient(135deg, #fff3cd, #ffe69c);
            color: #856404;
            display: block;
            border-left: 10px solid #f39c12;
            animation: bonusFeedback 1s infinite;
        }

        @keyframes bonusFeedback {
            0% { box-shadow: 0 0 10px #f39c12; }
            50% { box-shadow: 0 0 40px #f39c12; }
            100% { box-shadow: 0 0 10px #f39c12; }
        }

        /* BOTÕES */
        .botoes {
            display: flex;
            gap: 15px;
            margin: 20px 0;
        }

        .btn {
            flex: 1;
            background: linear-gradient(135deg, #0a2f44, #1b4a6b);
            color: white;
            border: none;
            border-radius: 20px;
            padding: 15px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            border: 2px solid gold;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: "💰";
            position: absolute;
            left: -30px;
            top: -10px;
            font-size: 35px;
            opacity: 0;
            transition: 0.3s;
        }

        .btn:hover:not(:disabled) {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px gold;
            background: linear-gradient(135deg, #1b4a6b, #2c3e50);
        }

        .btn:hover:not(:disabled)::before {
            left: 15px;
            opacity: 0.3;
        }

        .btn:active:not(:disabled) {
            transform: translateY(0);
        }

        .btn-reiniciar {
            background: linear-gradient(135deg, #e67e22, #d35400, #e67e22);
            background-size: 200% 200%;
            animation: gradientMove 3s ease infinite;
        }

        @keyframes gradientMove {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* RANKING */
        .ranking {
            background: rgba(236, 240, 241, 0.8);
            backdrop-filter: blur(5px);
            border-radius: 25px;
            padding: 15px;
            margin-top: 10px;
            border: 2px solid gold;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        .ranking-grid {
            display: grid;
            grid-template-columns: repeat(10, 1fr);
            gap: 6px;
        }

        .ranking-item {
            background: white;
            border: 2px solid #bdc3c7;
            border-radius: 10px;
            padding: 5px;
            text-align: center;
            font-size: 11px;
            transition: 0.3s;
            font-weight: bold;
        }

        .ranking-item.acertou {
            background: linear-gradient(135deg, #d4edda, #c3e6cb);
            border-color: #27ae60;
            box-shadow: 0 0 15px #27ae60;
            animation: acertoPulse 2s infinite;
        }

        .ranking-item.errou {
            background: linear-gradient(135deg, #f8d7da, #f5c6cb);
            border-color: #e74c3c;
        }

        @keyframes acertoPulse {
            0% { box-shadow: 0 0 5px #27ae60; }
            50% { box-shadow: 0 0 20px #27ae60; }
            100% { box-shadow: 0 0 5px #27ae60; }
        }

        /* MODAL FALÊNCIA */
        .modal-falencia {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.9);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            backdrop-filter: blur(5px);
        }

        .modal-conteudo {
            background: linear-gradient(135deg, #2c3e50, #34495e);
            padding: 40px;
            border-radius: 50px;
            text-align: center;
            max-width: 400px;
            border: 4px solid #e74c3c;
            box-shadow: 0 0 100px #e74c3c;
            animation: modalEntrada 0.5s;
        }

        @keyframes modalEntrada {
            0% { transform: scale(0.5) rotate(-10deg); opacity: 0; }
            100% { transform: scale(1) rotate(0); opacity: 1; }
        }

        .modal-conteudo h2 {
            color: #e74c3c;
            font-size: 36px;
            margin-bottom: 20px;
            text-shadow: 0 0 30px #e74c3c;
        }

        .modal-conteudo p {
            color: white;
            margin-bottom: 25px;
            font-size: 16px;
        }

        .modal-btn {
            background: linear-gradient(135deg, #e74c3c, #c0392b);
            color: white;
            border: none;
            padding: 15px 50px;
            border-radius: 40px;
            font-size: 18px;
            cursor: pointer;
            margin-top: 15px;
            border: 2px solid gold;
            box-shadow: 0 0 30px #e74c3c;
            transition: 0.3s;
        }

        .modal-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 0 50px #e74c3c;
        }

        /* RESULTADO FINAL */
        .resultado-final {
            text-align: center;
            padding: 25px;
            background: linear-gradient(135deg, gold, #f39c12, #e67e22);
            border-radius: 40px;
            color: #0a2f44;
            margin-top: 15px;
            display: none;
            border: 3px solid white;
            box-shadow: 0 0 60px gold;
            animation: resultadoEntrada 1s;
        }

        @keyframes resultadoEntrada {
            0% { transform: scale(0.8) translateY(50px); opacity: 0; }
            100% { transform: scale(1) translateY(0); opacity: 1; }
        }

        .resultado-final h2 {
            font-size: 28px;
            margin-bottom: 15px;
            color: #0a2f44;
            text-shadow: 2px 2px 0 white;
        }

        #resultado-mensagem {
            font-size: 18px;
            margin-top: 15px;
            font-weight: bold;
            background: rgba(255,255,255,0.5);
            padding: 15px;
            border-radius: 30px;
        }

        /* TÍTULO DO PAINEL */
        .painel-titulo {
            font-size: 18px;
            color: #0a2f44;
            margin-bottom: 15px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
            border-bottom: 2px solid gold;
            padding-bottom: 10px;
        }

        .painel-titulo span {
            background: gold;
            padding: 5px 15px;
            border-radius: 30px;
            font-size: 14px;
        }

        /* AJUSTES RESPONSIVOS */
        @media (max-width: 900px) {
            .dashboard {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="modal-falencia" id="modal-falencia">
        <div class="modal-conteudo">
            <h2>💀 FALÊNCIA 💀</h2>
            <p>Você errou 2 perguntas seguidas!<br>Sua empresa faliu e o cofre zerou!</p>
            <button class="modal-btn" onclick="fecharModalFalencia()">Recomeçar</button>
        </div>
    </div>

    <div class="dashboard">
        <!-- PAINEL ESQUERDO - VISOR E STATUS -->
        <div class="painel-esquerdo">
            <div class="painel-titulo">
                📊 VISOR DA EMPRESA
                <span>STATUS</span>
            </div>

            <!-- INDICADOR DE NÍVEL -->
            <div class="nivel-indicador">
                <span>📊 NÍVEL ATUAL</span>
                <span class="nivel-badge" id="nivel-atual">FÁCIL</span>
                <span id="pontos-nivel">0/10</span>
            </div>

            <!-- ALERTAS -->
            <div class="alerta-falencia" id="alerta-falencia">
                ⚠️ CUIDADO! Você está a 1 erro da FALÊNCIA! ⚠️
            </div>

            <!-- COFRE -->
            <div class="cofre-container">
                <div class="cofre-header">
                    <div class="cofre-titulo">
                        <span>💰</span>
                        <span>CAPITAL DA EMPRESA</span>
                    </div>
                    <div class="cofre-valor" id="cofre-valor">R$ 0</div>
                </div>
                <div class="cofre-barras" id="cofre-barras"></div>
            </div>

            <!-- BÔNUS -->
            <div class="bonus-ativo" id="bonus-ativo" style="display: none;">
                ⚡ BÔNUS ATIVO! +15% em cada acerto! ⚡
            </div>

            <!-- STATS -->
            <div class="empresa-card">
                <div class="empresa-stats">
                    <div class="stat">
                        <div class="stat-valor" id="pontuacao">0</div>
                        <div class="stat-label">Pontos</div>
                    </div>
                    <div class="stat">
                        <div class="stat-valor" id="acertos">0/20</div>
                        <div class="stat-label">Acertos</div>
                    </div>
                    <div class="stat">
                        <div class="stat-valor" id="erros-consecutivos">0</div>
                        <div class="stat-label">Erros consec.</div>
                    </div>
                </div>

                <div class="sequencia-container" id="sequencia-texto">
                    🎯 Acertos seguidos: 0
                </div>

                <div class="barra-progresso">
                    <div class="barra-preenchimento" id="barra-progresso"></div>
                </div>
            </div>

            <!-- RANKING -->
            <div class="ranking">
                <div class="painel-titulo" style="margin-top: 0; margin-bottom: 15px;">
                    🏆 RANKING DE PERGUNTAS
                </div>
                <div class="ranking-grid" id="ranking-grid"></div>
            </div>
        </div>

        <!-- PAINEL DIREITO - PERGUNTA E JOGO -->
        <div class="painel-direito">
            <div class="painel-titulo">
                🎯 ÁREA DE DESAFIOS
                <span>PERGUNTA ATUAL</span>
            </div>

            <!-- PERGUNTA ATUAL -->
            <div class="pergunta-container">
                <div class="dificuldade-tag" id="dificuldade-tag" style="background: #27ae60; color: white;">FÁCIL</div>
                <div class="pergunta-numero" id="pergunta-numero">Pergunta 1/20</div>
                <div class="pergunta-texto" id="pergunta-texto">Carregando...</div>
                <div class="opcoes" id="opcoes"></div>
                <div class="feedback" id="feedback"></div>
            </div>

            <!-- BOTÕES -->
            <div class="botoes">
                <button class="btn" id="proxima-btn" onclick="proximaPergunta()" disabled>➡️ PRÓXIMA</button>
                <button class="btn btn-reiniciar" onclick="reiniciar()">🔄 REINICIAR</button>
            </div>

            <!-- RESULTADO FINAL -->
            <div class="resultado-final" id="resultado-final">
                <h2>🏁 RESULTADO FINAL</h2>
                <div class="cofre-valor" id="resultado-cofre" style="margin: 15px auto;">R$ 0</div>
                <div id="resultado-mensagem"></div>
            </div>
        </div>
    </div>

    <script>
        // (todo o JavaScript permanece exatamente igual ao original)
        // ========== PERGUNTAS POR NÍVEL ==========
        const perguntas = [
            // NÍVEL FÁCIL (Perguntas 1-10)
            {
                pergunta: "O que é vantagem competitiva?",
                opcoes: ["A) Ter mais funcionários", "B) Capacidade de superar concorrentes oferecendo mais valor", "C) Ter o maior escritório", "D) Gastar mais em marketing"],
                correta: 1,
                valor: 100,
                nivel: "Fácil"
            },
          {
    pergunta: "O que é análise de mercado?",
    opcoes: [
        "A) Estudo do setor, concorrentes e consumidores para tomada de decisão",
        "B) Cálculo do faturamento mensal",
        "C) Número de funcionários da empresa",
        "D) Valor do aluguel do escritório"
    ],
    correta: 0,
    valor: 100,
    nivel: "Fácil"
},
            {
                pergunta: "O que é missão de uma empresa?",
                opcoes: ["A) O lucro que ela quer alcançar", "B) Sua razão de existir e propósito principal", "C) O número de funcionários", "D) Seu faturamento anual"],
                correta: 1,
                valor: 100,
                nivel: "Fácil"
            },
            {
                pergunta: "O que caracteriza uma estratégia empresarial eficaz?",
                opcoes: ["A) Focar apenas nas operações diárias", "B) Definir objetivos claros e vantagem competitiva", "C) Reduzir funcionários", "D) Copiar concorrentes"],
                correta: 1,
                valor: 100,
                nivel: "Fácil"
            },
            {
                pergunta: "O posicionamento estratégico está relacionado a:",
                opcoes: ["A) Como organizar funcionários", "B) Como a empresa compete no mercado", "C) Como pagar impostos", "D) Como contratar pessoas"],
                correta: 1,
                valor: 100,
                nivel: "Fácil"
            },
            {
                pergunta: "Quando uma empresa oferece produtos únicos, ela adota:",
                opcoes: ["A) Liderança em custos", "B) Diferenciação", "C) Diversificação", "D) Redução de mercado"],
                correta: 1,
                valor: 100,
                nivel: "Fácil"
            },
            {
                pergunta: "A estratégia de liderança em custos busca:",
                opcoes: ["A) Oferecer o menor preço", "B) Produzir menos", "C) Ter mais funcionários", "D) Aumentar burocracia"],
                correta: 0,
                valor: 100,
                nivel: "Fácil"
            },
            {
                pergunta: "Trade-offs estratégicos ocorrem quando:",
                opcoes: ["A) A empresa faz tudo ao mesmo tempo", "B) Precisa escolher entre alternativas", "C) Não existem limitações", "D) O mercado não muda"],
                correta: 1,
                valor: 100,
                nivel: "Fácil"
            },
            {
                pergunta: "Estratégia deliberada é aquela que:",
                opcoes: ["A) Surge por acaso", "B) É planejada antecipadamente", "C) Não tem objetivos", "D) Surge do mercado"],
                correta: 1,
                valor: 100,
                nivel: "Fácil"
            },
            {
                pergunta: "Estratégia emergente ocorre quando:",
                opcoes: ["A) A empresa adapta ações conforme oportunidades", "B) Tudo segue o plano inicial", "C) Não existe planejamento", "D) Ignora mudanças"],
                correta: 0,
                valor: 100,
                nivel: "Fácil"
            },
            
            // NÍVEL MÉDIO (Perguntas 11-15)
            {
                pergunta: "A estratégia baseada em recursos afirma que vantagem competitiva vem de:",
                opcoes: ["A) Recursos internos valiosos e difíceis de imitar", "B) Apenas preços baixos", "C) Grandes escritórios", "D) Muitas filiais"],
                correta: 0,
                valor: 200,
                nivel: "Médio"
            },
            {
                pergunta: "Qual exemplo representa um recurso estratégico intangível?",
                opcoes: ["A) Máquinas", "B) Equipamentos", "C) Marca reconhecida", "D) Estoque"],
                correta: 2,
                valor: 200,
                nivel: "Médio"
            },
            {
                pergunta: "A globalização aumenta principalmente:",
                opcoes: ["A) Isolamento das empresas", "B) Concorrência entre países", "C) Redução do comércio", "D) Produção local"],
                correta: 1,
                valor: 200,
                nivel: "Médio"
            },
            {
                pergunta: "O que é 'core business'?",
                opcoes: ["A) O negócio principal da empresa", "B) O departamento de TI", "C) A sede da empresa", "D) O conselho administrativo"],
                correta: 0,
                valor: 200,
                nivel: "Médio"
            },
            {
                pergunta: "O que significa 'benchmarking'?",
                opcoes: ["A) Copiar concorrentes", "B) Comparar práticas com empresas de referência", "C) Demitir funcionários", "D) Aumentar preços"],
                correta: 1,
                valor: 200,
                nivel: "Médio"
            },
            
            // NÍVEL DIFÍCIL (Perguntas 16-20)
            {
                pergunta: "Sobre vantagem competitiva sustentável, é correto afirmar que:",
                opcoes: [
                    "A) Surge exclusivamente da redução contínua de custos operacionais",
                    "B) Está associada à posse de recursos e capacidades difíceis de imitar e substituir",
                    "C) Depende apenas do aumento da participação de mercado",
                    "D) É garantida quando a empresa atua em mercados internacionais"
                ],
                correta: 1,
                valor: 300,
                nivel: "Difícil"
            },
            {
                pergunta: "No contexto de estratégia deliberada e emergente, pode-se afirmar que:",
                opcoes: [
                    "A) Estratégias emergentes são sempre resultado de falhas no planejamento formal",
                    "B) Estratégias deliberadas eliminam completamente a necessidade de adaptação",
                    "C) Estratégias emergentes podem surgir a partir de padrões de ação não intencionalmente planejados",
                    "D) Estratégias emergentes só ocorrem em empresas de pequeno porte"
                ],
                correta: 2,
                valor: 300,
                nivel: "Difícil"
            },
            {
                pergunta: "Sobre trade-offs estratégicos, assinale a alternativa correta:",
                opcoes: [
                    "A) São falhas gerenciais que devem ser evitadas a qualquer custo",
                    "B) Ocorrem apenas quando há escassez financeira",
                    "C) São escolhas que reforçam o posicionamento estratégico ao exigir renúncias",
                    "D) Indicam ausência de planejamento organizacional"
                ],
                correta: 2,
                valor: 300,
                nivel: "Difícil"
            },
            {
                pergunta: "Em relação ao posicionamento estratégico, é correto afirmar que:",
                opcoes: [
                    "A) Empresas podem sustentar simultaneamente liderança absoluta em custos e diferenciação máxima sem conflitos",
                    "B) O posicionamento é definido exclusivamente pela área de marketing",
                    "C) O posicionamento estratégico busca ocupar um espaço único na percepção do cliente",
                    "D) Toda empresa deve competir apenas por preço para garantir sobrevivência"
                ],
                correta: 2,
                valor: 300,
                nivel: "Difícil"
            },
            {
                pergunta: "Considerando a estratégia baseada em recursos, é correto afirmar que:",
                opcoes: [
                    "A) A vantagem competitiva depende prioritariamente da estrutura do setor",
                    "B) Recursos tangíveis são sempre mais importantes que os intangíveis",
                    "C) Recursos estratégicos precisam ser valiosos, raros, difíceis de imitar e organizados adequadamente",
                    "D) Tecnologia adquirida no mercado garante vantagem sustentável automática"
                ],
                correta: 2,
                valor: 300,
                nivel: "Difícil"
            }
        ];

        // ========== VARIÁVEIS ==========
        let perguntaAtual = 0;
        let acertos = 0;
        let pontuacao = 0;
        let dinheiroCofre = 0;
        let errosConsecutivos = 0;
        let acertosConsecutivos = 0;
        let bonusAtivo = false;
        let respondidas = new Array(20).fill(null);
        let quizFinalizado = false;

        // ========== ELEMENTOS ==========
        const perguntaNumero = document.getElementById('pergunta-numero');
        const perguntaTexto = document.getElementById('pergunta-texto');
        const opcoesDiv = document.getElementById('opcoes');
        const feedbackDiv = document.getElementById('feedback');
        const proximaBtn = document.getElementById('proxima-btn');
        const pontuacaoEl = document.getElementById('pontuacao');
        const acertosEl = document.getElementById('acertos');
        const errosConsecutivosEl = document.getElementById('erros-consecutivos');
        const sequenciaTexto = document.getElementById('sequencia-texto');
        const barraProgresso = document.getElementById('barra-progresso');
        const rankingGrid = document.getElementById('ranking-grid');
        const resultadoFinal = document.getElementById('resultado-final');
        const cofreValor = document.getElementById('cofre-valor');
        const cofreBarras = document.getElementById('cofre-barras');
        const resultadoCofre = document.getElementById('resultado-cofre');
        const alertaFalencia = document.getElementById('alerta-falencia');
        const bonusAtivoDiv = document.getElementById('bonus-ativo');
        const modalFalencia = document.getElementById('modal-falencia');
        const nivelAtual = document.getElementById('nivel-atual');
        const pontosNivel = document.getElementById('pontos-nivel');
        const dificuldadeTag = document.getElementById('dificuldade-tag');

        // ========== FUNÇÕES ==========
        function atualizarNivel() {
            if (perguntaAtual < 10) {
                nivelAtual.innerHTML = 'FÁCIL';
                nivelAtual.style.background = 'gold';
                nivelAtual.style.color = '#2c3e50';
            } else if (perguntaAtual < 15) {
                nivelAtual.innerHTML = 'MÉDIO';
                nivelAtual.style.background = '#f39c12';
                nivelAtual.style.color = 'white';
            } else {
                nivelAtual.innerHTML = 'DIFÍCIL';
                nivelAtual.style.background = '#e74c3c';
                nivelAtual.style.color = 'white';
            }
            pontosNivel.innerHTML = `${perguntaAtual}/20`;
        }

        function atualizarCofre() {
            cofreValor.innerHTML = `R$ ${dinheiroCofre}`;
            
            let numeroBarras = Math.min(10, Math.floor(dinheiroCofre / 200) + 1);
            let html = '';
            
            for (let i = 0; i < 10; i++) {
                let altura = i < numeroBarras ? 20 + (i * 15) : 5;
                html += `<div class="barra-dinheiro" style="height: ${altura}px;"></div>`;
            }
            
            cofreBarras.innerHTML = html;
        }

        function verificarBonus() {
            if (acertosConsecutivos >= 3 && !bonusAtivo) {
                bonusAtivo = true;
                bonusAtivoDiv.style.display = 'inline-block';
                feedbackDiv.className = 'feedback bonus';
                feedbackDiv.innerHTML = '⚡ BÔNUS ATIVADO! +15% em cada acerto por 3 acertos seguidos! ⚡';
            }
        }

        function verificarFalencia() {
            if (errosConsecutivos >= 2) {
                modalFalencia.style.display = 'flex';
                dinheiroCofre = 0;
                pontuacao = 0;
                errosConsecutivos = 0;
                atualizarCofre();
                pontuacaoEl.innerHTML = pontuacao;
                errosConsecutivosEl.innerHTML = errosConsecutivos;
                quizFinalizado = true;
                proximaBtn.disabled = true;
                return true;
            }
            
            alertaFalencia.style.display = errosConsecutivos === 1 ? 'block' : 'none';
            return false;
        }

        function fecharModalFalencia() {
            modalFalencia.style.display = 'none';
            reiniciar();
        }

        function carregarPergunta() {
            if (perguntaAtual >= perguntas.length) {
                mostrarResultadoFinal();
                return;
            }

            const p = perguntas[perguntaAtual];
            perguntaNumero.innerHTML = `Pergunta ${perguntaAtual + 1}/20`;
            perguntaTexto.innerHTML = p.pergunta;
            
            // Atualiza tag de dificuldade
            dificuldadeTag.innerHTML = p.nivel;
            if (p.nivel === 'Fácil') dificuldadeTag.style.background = '#27ae60';
            else if (p.nivel === 'Médio') dificuldadeTag.style.background = '#f39c12';
            else dificuldadeTag.style.background = '#e74c3c';

            let html = '';
            p.opcoes.forEach((opcao, i) => {
                let classe = 'opcao';
                if (respondidas[perguntaAtual] !== null) {
                    if (i === p.correta) classe += ' correta';
                    else if (i === respondidas[perguntaAtual]) classe += ' incorreta';
                    classe += ' disabled';
                }
                html += `
                    <div class="${classe}" onclick="responder(${i})">
                        <span class="letra">${opcao[0]}</span>
                        <span>${opcao.substring(3)}</span>
                    </div>
                `;
            });
            opcoesDiv.innerHTML = html;
            
            proximaBtn.disabled = respondidas[perguntaAtual] === null;
            atualizarNivel();
        }

        function responder(opcao) {
            if (respondidas[perguntaAtual] !== null || quizFinalizado) return;

            const p = perguntas[perguntaAtual];
            const acertou = (opcao === p.correta);

            respondidas[perguntaAtual] = opcao;

            if (acertou) {
                let valorGanho = p.valor;
                if (bonusAtivo) {
                    valorGanho = Math.floor(valorGanho * 1.15);
                }
                
                acertos++;
                acertosConsecutivos++;
                errosConsecutivos = 0;
                pontuacao += valorGanho;
                dinheiroCofre += valorGanho;
                
                feedbackDiv.className = 'feedback sucesso';
                feedbackDiv.innerHTML = `✅ CORRETO! +R$ ${valorGanho} ${bonusAtivo ? '(com bônus de 15%)' : ''}`;
                
                verificarBonus();
                
                cofreValor.style.transform = 'scale(1.2)';
                setTimeout(() => cofreValor.style.transform = 'scale(1)', 200);
            } else {
                acertosConsecutivos = 0;
                errosConsecutivos++;
                bonusAtivo = false;
                bonusAtivoDiv.style.display = 'none';
                
                feedbackDiv.className = 'feedback erro';
                feedbackDiv.innerHTML = `❌ ERRADO! A resposta correta é: ${p.opcoes[p.correta]}`;
                
                if (verificarFalencia()) return;
            }

            pontuacaoEl.innerHTML = pontuacao;
            acertosEl.innerHTML = acertos + '/20';
            errosConsecutivosEl.innerHTML = errosConsecutivos;
            sequenciaTexto.innerHTML = `🎯 Acertos seguidos: ${acertosConsecutivos}`;
            barraProgresso.style.width = (acertos / 20 * 100) + '%';
            
            atualizarCofre();
            carregarPergunta();
            atualizarRanking();
        }

        function proximaPergunta() {
            if (perguntaAtual < perguntas.length - 1) {
                perguntaAtual++;
                feedbackDiv.className = 'feedback';
                feedbackDiv.innerHTML = '';
                carregarPergunta();
            } else {
                mostrarResultadoFinal();
            }
        }

        function atualizarRanking() {
            let html = '';
            for (let i = 0; i < 20; i++) {
                let classe = 'ranking-item';
                if (respondidas[i] !== null) {
                    classe += respondidas[i] === perguntas[i].correta ? ' acertou' : ' errou';
                }
                let nivel = '';
                if (i < 10) nivel = 'F';
                else if (i < 15) nivel = 'M';
                else nivel = 'D';
                
                html += `<div class="${classe}">P${i+1}<br><span class="dificuldade-indicador">${nivel}</span></div>`;
            }
            rankingGrid.innerHTML = html;
        }

        function mostrarResultadoFinal() {
            quizFinalizado = true;
            proximaBtn.disabled = true;
            resultadoFinal.style.display = 'block';
            resultadoCofre.innerHTML = `R$ ${dinheiroCofre}`;
            
            let mensagem = '';
            if (acertos === 20) mensagem = '🌟 PERFEITO! Você é um expert em estratégia empresarial! 🌟';
            else if (acertos >= 17) mensagem = '🏆 EXCELENTE! Conhecimento sólido em todos os níveis!';
            else if (acertos >= 14) mensagem = '👍 MUITO BOM! Domina bem os conceitos!';
            else if (acertos >= 10) mensagem = '📚 BOM! Continue estudando os níveis mais avançados!';
            else mensagem = '💪 NÃO DESISTA! Pratique mais e volte mais forte!';
            
            document.getElementById('resultado-mensagem').innerHTML = mensagem;
        }

        function reiniciar() {
            perguntaAtual = 0;
            acertos = 0;
            pontuacao = 0;
            dinheiroCofre = 0;
            errosConsecutivos = 0;
            acertosConsecutivos = 0;
            bonusAtivo = false;
            respondidas = new Array(20).fill(null);
            quizFinalizado = false;
            
            pontuacaoEl.innerHTML = '0';
            acertosEl.innerHTML = '0/20';
            errosConsecutivosEl.innerHTML = '0';
            sequenciaTexto.innerHTML = '🎯 Acertos seguidos: 0';
            barraProgresso.style.width = '0%';
            
            feedbackDiv.className = 'feedback';
            feedbackDiv.innerHTML = '';
            resultadoFinal.style.display = 'none';
            alertaFalencia.style.display = 'none';
            bonusAtivoDiv.style.display = 'none';
            
            atualizarCofre();
            atualizarRanking();
            carregarPergunta();
        }

        // ========== INICIALIZAÇÃO ==========
        atualizarCofre();
        carregarPergunta();
        atualizarRanking();
    </script>
</body>
</html>
