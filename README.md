<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pesquisar no Google</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
        }
        .container {
            text-align: center;
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 90%;
            max-width: 500px;
        }
        input[type="text"] {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 16px;
            margin-bottom: 10px;
        }
        button {
            padding: 10px 20px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            margin: 5px;
        }
        button:hover {
            background-color: #0056b3;
        }
        .dicas, .historico, .explicacao, .outros-recursos {
            margin-top: 20px;
            text-align: left;
            background-color: #f9f9f9;
            padding: 15px;
            border-radius: 8px;
            border: 1px solid #ddd;
        }
        .dicas ul {
            list-style-type: disc;
            padding-left: 20px;
        }
        .dicas li {
            margin: 5px 0;
        }
        .feedback {
            margin-top: 10px;
            color: #007BFF;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Pesquisar no Google</h1>
        <input type="text" id="campoPesquisa" placeholder="Digite sua pergunta...">
        <button onclick="pesquisarGoogle()">Pesquisar no Google</button>

        <!-- Feedback visual -->
        <div id="feedback" class="feedback" style="display: none;">
            <p>Pesquisando...</p>
        </div>

        <!-- Dicas de pesquisa -->
        <div class="dicas">
            <h3>Exemplos de perguntas:</h3>
            <ul>
                <li>O que é inteligência artificial?</li>
                <li>Como aprender programação?</li>
                <li>Qual a capital da França?</li>
            </ul>
        </div>

        <!-- Histórico de pesquisas -->
        <div id="historico" class="historico">
            <h3>Histórico de Pesquisas:</h3>
            <p>Nenhuma pesquisa realizada ainda.</p>
        </div>

        <!-- Explicação do funcionamento -->
        <div class="explicacao">
            <h3>Como funciona?</h3>
            <p>
                Quando você digita uma pergunta e clica em "Pesquisar", o sistema redireciona você para o Google com a sua pergunta.
                O Google então busca na web os resultados mais relevantes para o que você perguntou.
            </p>
        </div>

        <!-- Integração com outros recursos -->
        <div class="outros-recursos">
            <h3>Pesquisar também em:</h3>
            <button onclick="pesquisarYouTube()">YouTube</button>
            <button onclick="pesquisarWikipedia()">Wikipedia</button>
        </div>
    </div>

    <script>
        let historico = []; // Array para armazenar o histórico

        function pesquisarGoogle() {
            const pergunta = document.getElementById('campoPesquisa').value;

            if (pergunta.trim() !== "") {
                // Mostra o feedback
                document.getElementById('feedback').style.display = 'block';

                // Simula um pequeno atraso para o feedback
                setTimeout(() => {
                    const query = encodeURIComponent(pergunta);
                    window.open(`https://www.google.com/search?q=${query}`, '_blank');

                    // Adiciona a pergunta ao histórico
                    historico.push(pergunta);
                    atualizarHistorico();

                    // Oculta o feedback
                    document.getElementById('feedback').style.display = 'none';
                }, 500); // 500ms de atraso
            } else {
                alert("Por favor, digite uma pergunta antes de pesquisar.");
            }
        }

        function pesquisarYouTube() {
            const pergunta = document.getElementById('campoPesquisa').value;
            if (pergunta.trim() !== "") {
                const query = encodeURIComponent(pergunta);
                window.open(`https://www.youtube.com/results?search_query=${query}`, '_blank');
            }
        }

        function pesquisarWikipedia() {
            const pergunta = document.getElementById('campoPesquisa').value;
            if (pergunta.trim() !== "") {
                const query = encodeURIComponent(pergunta);
                window.open(`https://pt.wikipedia.org/wiki/${query}`, '_blank');
            }
        }

        function atualizarHistorico() {
            const historicoDiv = document.getElementById('historico');
            historicoDiv.innerHTML = "<h3>Histórico de Pesquisas:</h3>";

            if (historico.length > 0) {
                historico.forEach((pesquisa, index) => {
                    historicoDiv.innerHTML += `<p>${index + 1}. ${pesquisa}</p>`;
                });
            } else {
                historicoDiv.innerHTML += "<p>Nenhuma pesquisa realizada ainda.</p>";
            }
        }
    </script>
</body>
</html>
