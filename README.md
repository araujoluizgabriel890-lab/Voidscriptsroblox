-- VOID SCRIPT - Documentos do Delta (Versão Celular)
local player = game.Players.LocalPlayer
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")

-- Criar GUI
local gui = Instance.new("ScreenGui")
gui.Name = "VoidScript"
gui.ResetOnSpawn = false
gui.Parent = player.PlayerGui

-- ===== FUNÇÃO DA BARRA DE CARREGAMENTO =====
local function animacaoCarregamento(callback)
    local loadFrame = Instance.new("Frame")
    loadFrame.Size = UDim2.new(0, 250, 0, 100)
    loadFrame.Position = UDim2.new(0.5, -125, 0.5, -50)
    loadFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    loadFrame.BackgroundTransparency = 0.05
    loadFrame.BorderSizePixel = 2
    loadFrame.BorderColor3 = Color3.fromRGB(156, 39, 176)
    loadFrame.Parent = gui
    
    local loadCorner = Instance.new("UICorner")
    loadCorner.CornerRadius = UDim.new(0, 12)
    loadCorner.Parent = loadFrame
    
    local tituloLoad = Instance.new("TextLabel")
    tituloLoad.Size = UDim2.new(1, 0, 0, 20)
    tituloLoad.Position = UDim2.new(0, 0, 0, 5)
    tituloLoad.Text = "⏳ Carregando Documento..."
    tituloLoad.TextColor3 = Color3.fromRGB(156, 39, 176)
    tituloLoad.TextSize = 13
    tituloLoad.Font = Enum.Font.SourceSansBold
    tituloLoad.BackgroundTransparency = 1
    tituloLoad.Parent = loadFrame
    
    local barraFundo = Instance.new("Frame")
    barraFundo.Size = UDim2.new(0.85, 0, 0, 14)
    barraFundo.Position = UDim2.new(0.075, 0, 0.5, 0)
    barraFundo.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    barraFundo.BorderSizePixel = 1
    barraFundo.BorderColor3 = Color3.fromRGB(156, 39, 176)
    barraFundo.Parent = loadFrame
    
    local barraCorner = Instance.new("UICorner")
    barraCorner.CornerRadius = UDim.new(0, 7)
    barraCorner.Parent = barraFundo
    
    local barraPreenchimento = Instance.new("Frame")
    barraPreenchimento.Size = UDim2.new(0, 0, 1, 0)
    barraPreenchimento.BackgroundColor3 = Color3.fromRGB(156, 39, 176)
    barraPreenchimento.BorderSizePixel = 0
    barraPreenchimento.Parent = barraFundo
    
    local preenchCorner = Instance.new("UICorner")
    preenchCorner.CornerRadius = UDim.new(0, 7)
    preenchCorner.Parent = barraPreenchimento
    
    local textoPorcentagem = Instance.new("TextLabel")
    textoPorcentagem.Size = UDim2.new(1, 0, 0, 16)
    textoPorcentagem.Position = UDim2.new(0, 0, 0.75, 0)
    textoPorcentagem.Text = "0%"
    textoPorcentagem.TextColor3 = Color3.fromRGB(255, 255, 255)
    textoPorcentagem.TextSize = 12
    textoPorcentagem.Font = Enum.Font.SourceSansBold
    textoPorcentagem.BackgroundTransparency = 1
    textoPorcentagem.Parent = loadFrame
    
    local progresso = 0
    coroutine.wrap(function()
        while progresso < 100 do
            progresso = progresso + 1
            barraPreenchimento.Size = UDim2.new(progresso/100, 0, 1, 0)
            textoPorcentagem.Text = progresso .. "%"
            wait(0.015)
        end
        wait(0.2)
        loadFrame:Destroy()
        callback()
    end)()
end

-- ===== DOCUMENTO PRAÇAS COMPLETO =====
local docPracas = [[
📋 RESUMO DO DOCUMENTO ⚔️ PRAÇAS E GRADUADOS

═══════════════════════════════════════════
TREINAMENTO FÍSICO — PRAÇAS E GRADUADOS
Documento Oficial — Exército Brasileiro do Delta
Ass: [PRES] Golgos
═══════════════════════════════════════════

1. INTRODUÇÃO

Olá, oficial responsável pela aplicação do treinamento.

Leia atentamente todo este documento antes de iniciar qualquer Treinamento Físico de Praças e Graduados. Durante a aplicação, nenhuma avaliação, regra, proibição ou informação deverá ser alterada, removida ou adicionada.

O instrutor deve seguir este documento exatamente como apresentado, garantindo uma avaliação justa, organizada e igual para todos os participantes.

─────────────────────────────────────────

1.1. REGRAS IMPORTANTES

- As regras devem ser seguidas exatamente como estão apresentadas no anúncio.
- Não coloque códigos de servidor incorretos.
- O participante que permanecer mais de 3 a 4 minutos AFK poderá ser retirado do treinamento por desistência.
- Caso o instrutor realize o anúncio incorretamente mais de 3 vezes, poderá ser rebaixado.
- Favoritismo durante a avaliação não será tolerado. Todos os participantes devem ser avaliados nas mesmas condições.
- Militares que não demonstrarem comportamento obediente e justo durante o treinamento poderão receber:
  • Ato disciplinar;
  • Pagamento de 10 JJs;
  • Retirada de 1 ponto.

─────────────────────────────────────────

1.2. PROIBIÇÕES

É proibido:

- Utilizar xerifes;
- Utilizar alunos de char;
- Demorar mais de 6 horas para entregar as patentes;
- Dar meio ponto por quase realizar uma atividade dentro do tempo;
- Utilizar tempos diferentes para participantes com ou sem burla;
- Abandonar o treinamento sem justificativa;
- Conceder pontos extras por desempenho.

─────────────────────────────────────────

1.3. SUGESTÕES

Para facilitar a aplicação do treinamento:

- É recomendável utilizar a função da prancheta para salvar os nomes dos participantes.
- É aconselhável que o instrutor ou um auxiliar grave a tela para garantir maior segurança e precisão durante a avaliação.
- No primeiro treinamento, solicite auxílio de um superior experiente.
- Oriente os militares a falarem exclusivamente pela placa, mantendo a organização.

COMANDOS IMPORTANTES:

";countdown (Tempo)" — Inicia um temporizador.
";h (Mensagem)" — Envia uma mensagem para todos do servidor.
";title (Nick)" — Nomeia um jogador.
";kick (Nick)" — Retira um jogador do servidor.

─────────────────────────────────────────

1.4. ANÚNCIO DO TREINAMENTO FÍSICO

TREINAMENTO FÍSICO (01/50)
◈─────────────────────────◈
| • Instrutor: @(Sua marcação)
| • Auxiliares: @(Apenas Oficiais)
| • Patente do Instrutor: (Aspirante a Oficial ou acima)
| • Patente dos Auxiliares: (Aspirante a Oficial ou acima)
◈─────────────────────────◈
| • Marcação: (Patente que realizará o treinamento)
◈─────────────────────────◈
| • Horário: (00:00)
| • Código do Servidor: (Gerado no jogo)
◈─────────────────────────◈

→ OBSERVAÇÕES E NORMAS ←

1. Todos os participantes deverão formar uma fila organizada no STS e permanecer em silêncio, aguardando as orientações do instrutor.

2. Não é permitido falar sem autorização. Para solicitar a palavra, utilize "PPF!" (Permissão Para Falar) e aguarde a autorização do instrutor.

3. Discussões, desentendimentos ou qualquer tipo de briga não serão tolerados. Os envolvidos serão imediatamente dispensados do treinamento.

4. Militares que entrarem atrasados poderão ser retirados do servidor ou impedidos de participar.

5. Qualquer tentativa de burlar comandos, instruções ou atividades poderá resultar em desconto de pontos ou eliminação do treinamento.

6. Não é permitido questionar o resultado das avaliações durante a realização do treinamento.

7. Todos devem manter postura, disciplina, respeito e organização durante todo o treinamento.

8. Caso um militar entre atrasado, deverá solicitar autorização ao instrutor. A decisão final caberá ao responsável pelo treinamento.

─────────────────────────────────────────

2. ANTES DO TREINAMENTO

Antes de iniciar:

1. Não publique o anúncio sem estar dentro do servidor.
2. Os alunos devem estar utilizando o fardamento obrigatório ao lado do STS Central.
3. Organize os clones em frente ao STS da Central para indicar onde os militares deverão formar a fila.
4. Aguarde o tempo de tolerância informado no anúncio.
5. Após o término da tolerância, abra o portão.
6. Organize os militares no STS.
7. Faça os militares saudarem a bandeira.
8. Cumprimente os militares no STS.
9. Inicie as avaliações.

─────────────────────────────────────────

3. AVALIAÇÕES

Todas as avaliações devem ser realizadas de maneira justa, organizada e eficiente.

Os critérios de pontuação de cada avaliação devem ser seguidos exatamente como apresentados neste documento.

O instrutor deve permanecer atento durante todo o treinamento e acompanhar o desempenho de cada participante.

─────────────────────────────────────────

3.1. JJs (POLICHINELOS) — 1,0 PONTO

PRAÇAS:
150 JJs em 210 segundos

GRADUADOS:
170 JJs em 230 segundos

O participante que realizar os JJs após o término do timer será dispensado.

É recomendável que o instrutor grave a tela para consultar os resultados com maior precisão, principalmente quando houver muitos participantes.

─────────────────────────────────────────

3.2. TEXTO GRAMATICAL — 2,0 PONTOS

Tempo para todos: 300 segundos.

Cada militar deverá escrever um texto com no mínimo 4 linhas.

TEMA:
O texto deverá abordar um dos seguintes temas:
- Exército Brasileiro; ou
- Exército Brasileiro do Delta.

PONTUAÇÃO:
• Mais de 3 erros gramaticais: 0 pontos.
• De 1 a 3 erros: 1 ponto.
• Nenhum erro: 2 pontos.
• Fugiu do tema: 0 pontos.

O instrutor deverá sempre apontar os erros gramaticais encontrados.

O texto gramatical poderá ser realizado logo após os JJs ou no final do treinamento.

Após essa etapa, realize uma marcha até o primeiro Parkour.

─────────────────────────────────────────

3.3. PARKOURS — 1,0 PONTO CADA

Cada Parkour vale 1,0 ponto.

PRAÇAS:
Parkour 1: 35s | 30s | 30s | 35s
Parkour 2: 40s | 35s | 35s | 30s
Parkour 3: 30s | 30s | 35s | 30s
Parkour 4: 32s | 28s | 40s | 40s

GRADUADOS:
Parkour 1: 30s | 27s | 25s | 27s
Parkour 2: 35s | 30s | 27s | 25s
Parkour 3: 27s | 27s | 27s | 25s
Parkour 4: 29s | 25s | 30s | 30s

TORRE:
PC e Console: 15s | Celular: 16s

É permitido burlar.

Após concluir os Parkours, todos deverão retornar ao STS Central.

─────────────────────────────────────────

3.4. PERGUNTAS — 1,0 PONTO

O instrutor deverá fazer 1 pergunta relacionada ao Exército Brasileiro ou ao Exército Brasileiro do Delta.

REGRAS:

- Apenas receberá o ponto quem responder corretamente.
- O instrutor deverá colocar um timer de 40 segundos.
- Os participantes deverão colocar suas respostas na placa.
- A resposta não poderá ser dada antes do término do timer.
- Caso a pergunta tenha mais de uma resposta correta, todas as respostas corretas deverão ser aceitas.
- Caso a pergunta esteja mal formulada, ela deverá ser refeita.

─────────────────────────────────────────

4. PONTUAÇÃO

Mínimo para aprovação:

PRAÇAS: 4 pontos
GRADUADOS: 5 pontos

Pontuação máxima: 9,0 pontos.

─────────────────────────────────────────

5. RELATÓRIO DE PROMOÇÃO

Após finalizar o treinamento, o instrutor deverá elaborar o relatório.

RELATÓRIO DE PROMOÇÃO (01)
◈─────────────────────────◈
Instrutor: (sua marcação)
Auxiliares: (apenas oficiais)
◈─────────────────────────◈

APROVADOS:
(Militares aprovados - patente atual - nova patente)

Caso o aprovado esteja em CDP pelo site,
coloque ao lado do nome: (Em CDP).

REPROVADOS:
(Não é obrigatório colocar os nicks dos reprovados)

◈─────────────────────────◈
Data e hora: (o Discord já mostra)
Observações: (OBRIGATÓRIO)
◈─────────────────────────◈
Comprovações: (FOTOS — EXTREMAMENTE OBRIGATÓRIO)

Após tirar as fotos das comprovações, informe aos Praças e Graduados sobre a existência do Discord do EB do Delta.

─────────────────────────────────────────

6. PROMOÇÃO DOS APROVADOS

Após concluir o relatório, o instrutor deverá acessar:

https://ebdelta.com/

Em seguida, deverá promover todos os militares aprovados que estejam aptos.

A não promoção de um aprovado que esteja em condições de receber a promoção poderá resultar em punição ao instrutor.

Após clicar no botão de promoção, a patente e a CDP serão entregues automaticamente.

PRAZO PARA PROMOÇÃO:

É obrigatório entregar a patente de todos os aprovados em até 6 horas.

Caso o prazo não seja cumprido, o instrutor poderá ser punido.

Também é obrigatório enviar o relatório de promoção no canal:

#📗relatório-de-promoção

─────────────────────────────────────────

📌 RESUMO PARA O INSTRUTOR

ANTES:
Anúncio → Organizar fila → Fardamento → Tolerância → STS → Saudação à bandeira.

AVALIAÇÕES:
1. JJs → 1 ponto
2. Texto gramatical → 2 pontos
3. Parkour 1 → 1 ponto
4. Parkour 2 → 1 ponto
5. Parkour 3 → 1 ponto
6. Parkour 4 → 1 ponto
7. Torre → conforme avaliação
8. Pergunta → 1 ponto

APROVAÇÃO:
- Praças: mínimo 4 pontos
- Graduados: mínimo 5 pontos
- Máximo: 9 pontos

DEPOIS:
Relatório → Fotos das comprovações → Informar sobre o Discord → Promover aprovados → Enviar relatório no canal correto.

═══════════════════════════════════════════
FIM DO DOCUMENTO
⚔️ PRAÇAS E GRADUADOS ⚔️
═══════════════════════════════════════════
]]

-- ===== DOCUMENTO AMAN COMPLETO =====
local docAman = [[
📋 DOCUMENTO AMAN - ACADEMIA MILITAR DAS AGULHAS NEGRAS

═══════════════════════════════════════════
CURSO DA AMAN — FORMAÇÃO DE OFICIAIS
Documento Oficial — Exército Brasileiro do Delta
═══════════════════════════════════════════

1. INTRODUÇÃO À AMAN

O instrutor deve ler e seguir todo o script com cautela. Não deve remover, adicionar ou alterar avaliações, regras, proibições ou informações importantes.

A AMAN tem como objetivo formar novos oficiais, portanto o instrutor deve demonstrar aptidão, vontade, organização e proatividade durante a formação dos cadetes.

─────────────────────────────────────────

1.1. REGRAS IMPORTANTES

- O anúncio deve seguir exatamente o formato estabelecido.
- Não colocar códigos de servidor incorretos.
- AFK por mais de 3–4 minutos poderá resultar em retirada por desistência.
- Anunciar o curso incorretamente mais de 3 vezes poderá resultar em rebaixamento.
- Favoritismo não será tolerado.
- Todos devem ser avaliados nas mesmas condições.
- Má conduta, desobediência ou injustiça poderá resultar em:
  • Ato disciplinar;
  • Pagamento de 25 JJs;
  • Retirada de 1 ponto, informando o motivo ao Cadete.
- É permitido 1 xerife.
- Jargões como "bisonho" e "mocorongo" são permitidos, mas com limite.

─────────────────────────────────────────

1.2. PROIBIÇÕES

- Proibido alunos de char.
- Proibido demorar mais de 6 horas para entregar as patentes.
- Proibido dar 0,5 ponto por quase realizar dentro do tempo.
- Proibido usar tempo diferente com ou sem burla.
- Proibido abandonar o treinamento sem justificativa.
- Proibido divulgar códigos do curso fora dos canais da AMAN.
- Proibido dar pontos extras por desempenho.

─────────────────────────────────────────

1.3. SUGESTÕES

- Usar a prancheta para salvar nomes.
- É aconselhável gravar a tela durante as avaliações.
- Solicitar que os militares falem exclusivamente pela placa.

COMANDOS:
;countdown (Tempo) — temporizador.
;h (Mensagem) — mensagem para todo o servidor.
;title (Nick) — nomeia um jogador.
;kick (Nick) — retira um jogador.

─────────────────────────────────────────

1.4. ANÚNCIO DO CURSO

CURSO DA AMAN (1/10)
◇-----------------------------------◇
INSTRUTOR: (Você)
AUXILIARES: (apenas aplicadores da AMAN)
PATENTE DO INSTRUTOR: General de Brigada ou acima
◇----------------------------------◇
MARCAÇÃO: @Praças Especiais
◇-----------------------------------◇
HORÁRIO: (você escolhe)
TOLERÂNCIA: 5 minutos.
CÓDIGO: (código do servidor)
◇----------------------------------◇

OBSERVAÇÕES E REGRAS

- Fazer fila no STS e aguardar o instrutor.
- Não falar sem "PPF!"; caso fale, haverá desconto de ponto.
- Sem brigas; caso aconteça, os envolvidos serão dispensados.
- Atrasados serão analisados e o instrutor decidirá o que fazer.
- Não é permitido perguntar se passou ou não.

─────────────────────────────────────────

2. ANTES DO CURSO

- Cadetes devem usar o fardamento obrigatório ao lado do STS Central.
- Chars só podem ser liberados com autorização do instrutor.
- Organizar os clones em frente ao STS Central para indicar onde formar a fila.
- Aguardar os 5 minutos de tolerância.
- Após o tempo, abrir o portão e organizar os cadetes no STS.
- Fazer os cadetes saudarem a bandeira.
- Cumprimentar os cadetes e iniciar as avaliações.

─────────────────────────────────────────

3. AVALIAÇÕES

Todas devem ser realizadas de forma justa e eficiente, seguindo exatamente os critérios estabelecidos.

─────────────────────────────────────────

3.1. JJ's — 1,0 PONTO

- PC e Console: 75 JJs.
- Celular: 100 JJs.
- Tempo: 100 segundos.

Quem fizer JJs após o timer será dispensado.

É aconselhável gravar a tela para conferir resultados com maior precisão.

─────────────────────────────────────────

3.2. TEXTO GRAMATICAL — 2,0 PONTOS

- Tempo: 400 segundos para todos.
- Mínimo de 5 linhas.
- Tema sobre o Exército Brasileiro do Delta ou a função de um Aspirante no EB.

PONTUAÇÃO:
• Mais de 3 erros gramaticais: 0 pontos.
• De 1 a 3 erros: 1 ponto.
• Nenhum erro: 2 pontos.
• Fugiu do tema: 0 pontos.

O instrutor deve sempre apontar o erro gramatical.

O texto pode ser feito após os JJs ou no final do treinamento.

Depois, escolher 1 xerife e realizar a marcha até o primeiro parkour.

─────────────────────────────────────────

3.3. PARKOURS — 1,0 PONTO CADA

PARKOUR     | VERSÃO A | VERSÃO B | VERSÃO C | VERSÃO D
Parkour 1   |   19s    |   16s    |   16s    |   17s
Parkour 2   |   22s    |   17s    |   17s    |   16s
Parkour 3   |   19s    |   16s    |   17s    |   15s
Parkour 4   |   17s    |   15s    |   18s    |   16s

TORRE:
- PC e Console: 12s
- Celular: 11s

É permitido burlar.

─────────────────────────────────────────

3.4. COMANDOS — 1,0 PONTO

Os comandos devem ser realizados em no máximo 12 vezes. Qualquer erro resulta em 0 ponto.

- DIREITA VOLVER!
- ESQUERDA VOLVER!
- RETAGUARDA VOLVER!
- VANGUARDA VOLVER!

O instrutor pode utilizar comandos falsos para testar os cadetes.

Os comandos podem ser feitos pela call ou pelo chat, mas o instrutor deve informar qual será utilizado.

Se o candidato virar um pouco em um comando falso ou virar para o lado errado do volver, será considerado erro.

─────────────────────────────────────────

3.5. PERGUNTAS — 1,0 PONTO

- Fazer 2 perguntas relacionadas ao EB do Delta ou ao Exército Brasileiro.
- Não existe 0,5 ponto por acertar apenas 1 pergunta.
- Só recebe o ponto quem acertar todas as perguntas.
- Colocar timer de 25 segundos.
- Ao final do timer, os candidatos devem colocar as respostas na placa.
- Não podem responder antes do timer acabar.
- Se houver mais de uma resposta correta, todas devem ser aceitas.
- Perguntas mal formuladas devem ser refeitas.

─────────────────────────────────────────

4. PONTUAÇÃO

- Máximo: 10,0 pontos.
- Mínimo para aprovação: 7 pontos.
- Máximo de aprovados: 4 Cadetes.

Se houver mais de 4 aprovados, a decisão será feita através do PvP de FAL.

Não importa se o aprovado fez 7 ou 10 pontos: todos os aprovados devem participar do PvP.

─────────────────────────────────────────

5. RELATÓRIO DE PROMOÇÃO

RELATÓRIO DE EXAME AMAN (01/10)
◈─────────────────────────◈
Instrutor: (Você)
Auxiliares: (Aplicadores da AMAN)
Patente do Instrutor: (Sua patente)
◈─────────────────────────◈

APROVADOS:
Cadetes aprovados + patente atual + nova patente.
Se estiver em CDP pelo site, colocar (Em CDP) ao lado do nome.

REPROVADOS: opcional.
◈─────────────────────────◈
Observações: descrever detalhadamente o que foi realizado.
◈─────────────────────────◈
Horário: fornecido automaticamente pelo Discord.
◈─────────────────────────◈
Comprovações: imagem dos aprovados conforme o exemplo do documento.

─────────────────────────────────────────

6. PROMOÇÃO DOS APROVADOS

Após o relatório, acessar https://ebdelta.com/ e promover os aprovados.

A não promoção de um aprovado apto poderá resultar em punição.

Ao clicar em promover, a patente e a CDP são entregues automaticamente.

Todos os aprovados devem receber a patente dentro de 6 horas.

O descumprimento desse prazo poderá gerar punição.

O relatório deve ser enviado no canal #📗relatório-de-promoção.

═══════════════════════════════════════════
FIM - 🎓 AMAN - ACADEMIA MILITAR DAS AGULHAS NEGRAS
═══════════════════════════════════════════
]]

-- ===== DOCUMENTO OFICIAIS COMPLETO =====
local docOficiais = [[
🪖 TREINAMENTO FÍSICO — OFICIAIS
📋 RESUMO COMPLETO | EXÉRCITO BRASILEIRO DO DELTA
━━━━━━━━━━━━━━━━━━━━━━

⚠️ 01 | REGRAS GERAIS

• Seguir o script e o formato do anúncio corretamente.
• Não utiliza
