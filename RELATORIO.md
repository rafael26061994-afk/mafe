# Relatório — Radar Criativo Mafê v4.2

## Resumo
- **Testes automatizados:** 130 de 130 aprovados (Playwright/Chromium headless + vídeos e fotos de teste gerados com ffmpeg/Pillow). Zero erros de console em 360 px e 1280 px, claro e escuro.
- **🧪 Verificar integridade:** 57/57. **Bateria do Centro V4:** 39/39 (o arquivo original dava 38/39 por um teste com seletor errado, corrigido).
- **Manual:** HTML com modo noite e zoom + PDF de impressão, gerados por script a partir do index final. 94 nomes de botões e campos citados no manual foram conferidos contra a tela; 57 de 57 seções cobertas.

## O que já existia (inventário do Passo 2)

| Item | Situação encontrada | O que foi feito |
|---|---|---|
| a) Mapa do vídeo e 6 técnicas | Existia incompleto: não dizia que os tempos são referência | Nota "referência, não esticar"; texto dos cortes corrigido |
| b) 6 tipos de gancho | Existia; outros módulos usavam outros nomes (Status, Dor/Espaço) | Equivalência explicada em 3 lugares; ganchos do roteiro rotulados pelo tipo |
| c) Hashtags e legenda | Existia incompleto: conferidor sem variação nem plataforma; regra da legenda só em texto | Avisos de plataforma e de conjunto repetido; conferidor de legenda novo |
| d) Cadastro do produto | Existia; faltava estado vazio e erro útil de imagem | Mensagens novas (inclui HEIC) |
| e) Metas e rotina | Existia incompleto: metas não eram salvas; 25% × 30% sem explicação | Metas salvas e no backup; cabeçalho; explicação 25–30% |
| f) Roteiro por foto e objetivo | Existia incompleto: ganchos sem tipo; legenda sem gancho e cortada no meio; hashtag gigante; sem SEO; sem exportar | Tudo isso + ID do vídeo + .txt + atalho para a Nota |
| g) Nota do vídeo | Existia com erros: silêncio = "voz alta demais"; sem áudio = 0 pontos; HEVC sem explicação; histórico curto | Corrigido; nota parcial honesta; histórico com data e ID |
| h) Calibração | Existia | ID, nota parcial, remover registro, decimais em português |
| i) Vender | Existia e funciona (contas conferidas à mão) | Rótulo do ROAS de equilíbrio corrigido (é sobre faturamento bruto) |
| j) Português e inconsistências | Erros pontuais | "não cabem", "até o fim", decimais, frase da calibração |
| Didática (Passo 3) | Parcial: "Como ler" em parte das seções, "Modo de usar" geral, manual de 5 etapas | "📖 Como usar esta seção" nas 57 seções; 📖 Guia passo a passo; exemplos; telas vazias e erros reescritos |

## Melhorias extras (e por quê)
- **ID do vídeo** ligando roteiro → nota → calibração: saber qual resultado é de qual roteiro.
- **⬇️ Baixar roteiro (.txt)**: levar o roteiro para o celular ou para quem grava.
- **🔎 Busca no menu**: 58 links são muitos para rolar no celular.
- **Atalhos "Ir para…"** no fim de cada quadro de ajuda: uma etapa leva à próxima.
- **Simulador começa em 0,0**: antes mostrava 10,0 sem nada feito, o que parecia aprovação.
- **Proposta de IA real** descrita no README, fora do HTML (servidor próprio; nada implementado).

## Teste de leigo
Um agente independente, que não viu o trabalho, leu só o manual e executou na tela real (360 px e 1280 px) o caminho em 7 passos, o exemplo de ponta a ponta e 24 seções. Zero erros de console. Os números do exemplo bateram com a tela, um a um. Achados e o que foi feito:

| Achado (gravidade) | Correção |
|---|---|
| Digitar 129,90 virava 12990 sem aviso (alta) | O painel troca vírgula por ponto ao digitar, em todos os campos numéricos, e avisa se o número não for entendido. Teste novo |
| Menu mostra só o grupo da área aberta; seção "some" (média) | "Onde clicar" e Problemas comuns explicam: toque em 🌐 Todas as Áreas ou use 🔎 Buscar |
| Cap. 5 não citava o campo obrigatório "Nome do Produto" (média) | Passo reescrito com os 3 campos |
| Biblioteca: caixinhas de V01–V26 são travadas (média) | Passo indica 🔍 Comparar Vídeos para referências |
| Centro V4: botões dentro de blocos fechados (média) | Passos dizem qual bloco abrir |
| Restaurar: Mesclar × Substituir sem explicação (média) | Explicado no cap. 2 |
| Nomes curtos do manual não achados na busca (média) | Manual usa os nomes do menu e a busca também procura no título da seção e no "para que serve" |
| Cap. 3 não dizia a aba de cada seção; "Marcar como feito" não citado (baixa) | Coluna mostra a aba; texto explica o que marca sozinho |
| "2,9%" × "2,86%"; Ponte antes da Calculadora (baixa) | 2,86%; calculadora antes da ponte |
| "Pronto." confundia com a faixa "pronto" (baixa) | Status virou "Análise concluída" |
| Rótulos colados com opções da lista; títulos internos (banner-framework, visao) (baixa) | Extração do texto corrigida |
| Jargão (ROAS, SEO, snapshot, JSON, lapela, packing, overlay, HEVC…) | 17 termos novos no glossário |
| Lacuna "4 a 7 posições", frase confusa da Matriz, crase, decimais "1.4" | Corrigidos |

Não alterado: títulos antigos do painel em inglês (Batch Shooting, Pinned Comment) e o texto "Confira o console" do 🧪 Verificar integridade, para não mudar funções existentes; os termos estão explicados no glossário.


## Tabela de testes

| Função | Teste | Resultado |
|---|---|---|
| Código | node --check nos 24 <script> do index | ✅ 24/24 sem erro de sintaxe |
| Código | node --check nos 2 <script> do manual | ✅ 2/2 |
| Segurança | Sem chaves de API ou tokens no index e no manual | ✅ busca por padrões sk-, AIza, ghp_, xox, Bearer, api_key |
| Segurança | Sem recursos externos (src/href http) no index | ✅ arquivo único, offline |
| Carregamento | Abrir em 1280 px sem erros de console | ✅ 0 erros |
| Zoom do painel | Navegador novo abre em 100% (corrigido: antes abria em 70%) | ✅ 100% |
| Navegação | Clicar nos 58 links do menu: seção abre e tem conteúdo | ✅ 58/58 |
| Navegação | Abas de área (todas, analisar, planejar, testar, vender) filtram e não ficam vazias | ✅ ok |
| Didática | Quadro "📖 Como usar esta seção" em todas as 57 seções, recolhido, sem duplicar | ✅ sem: 0; duplicados: 0; formato: ok |
| Didática | Atalho "Ir para…" de cada quadro aponta para seção existente (57) | ✅  |
| Didática | Atalho "Ir para: 🗣️ SEO…" leva à seção certa | ✅ seção visível no topo |
| Didática | Campos visíveis sem exemplo (placeholder) e sem valor | ✅ 0:  |
| Busca no menu | Digitar "roas" acha a calculadora e o resultado (busca também no título da seção) | ✅ 🧮 Calculadora Spark Ads & ROAS \| 💵 Resultado Financeiro Real |
| Busca no menu | Nome usado no manual ("calibração") é encontrado (achado do teste de leigo) | ✅ 1 link(s) |
| Busca no menu | Nome usado no manual ("lucro") é encontrado (achado do teste de leigo) | ✅ 1 link(s) |
| Busca no menu | Nome usado no manual ("ponte comercial") é encontrado (achado do teste de leigo) | ✅ 1 link(s) |
| Busca no menu | Busca sem acento ("gancho") acha várias seções | ✅ 8 links |
| Busca no menu | Busca sem resultado mostra o próximo passo | ✅ Nada encontrado. Tente outra palavra, como “gancho”, “nota” ou “lucro”. |
| Roteiro por Foto e Objetivo | 25 combinações (5 objetivos × 5 tipos): 5 blocos, 3 ganchos com tipo, mostre/provas, legenda com contador, hashtags, fixado, 48h, ID | ✅ 25/25 |
| Roteiro por Foto e Objetivo | Sem nome do produto: avisa o que fazer, sem travar | ✅ mensagem orientando |
| Roteiro por Foto e Objetivo | Foto escura: lê brilho/cor e diz que não reconhece o produto | ✅ Foto escura, tons quentes. A dica de fundo e luz entra no roteiro. O painel não reconhece o produto: só mede brilho e cor. |
| Roteiro por Foto e Objetivo | Arquivo que não é imagem: erro explica e orienta | ✅ Não consegui ler esta foto (formato HEIC ou arquivo corrompido). Exporte como JPG ou PNG e escolha de novo. O roteiro funciona mesmo sem fot |
| Roteiro por Foto e Objetivo | Exportar roteiro em .txt | ✅ roteiro_MAFE-TESTE-01.txt |
| Ligação por ID | Roteiro passa o ID para a Nota do Vídeo | ✅ MAFE-TESTE-01 |
| Roteiro por Foto e Objetivo | Legenda: gancho + palavra-chave na 1ª linha e CTA no fim | ✅ Você ainda tá comprando bolsa tote caramelo no lugar errado? Clica no carrinho. |
| Cadastro do Produto | Tela vazia diz o próximo passo | ✅ Preencha a palavra-chave, o tipo e o resultado. O título aparece aqui com a conferência das regras. |
| Cadastro do Produto | Título válido: 4 ✅ | ✅ ✅ palavra-chave no início; ✅ 48/255 caracteres; ✅ sem emoji; ✅ sem CAPSLOCK excessivo |
| Cadastro do Produto | Título com emoji: ❌ sem emoji | ✅ ✅ palavra-chave no início; ✅ 28/255 caracteres; ❌ sem emoji; ✅ sem CAPSLOCK excessivo |
| Cadastro do Produto | Título em CAPS: ❌ CAPS excessivo | ✅ ✅ palavra-chave no início; ✅ 43/255 caracteres; ✅ sem emoji; ❌ sem CAPSLOCK excessivo |
| Cadastro do Produto | Título com mais de 255: ❌ contador | ✅ ❌ 270/255 caracteres |
| Cadastro do Produto | Palavra-chave fora do início: ❌ | ✅ ❌ palavra-chave no início |
| Cadastro do Produto | Fotos: quadrada grande ✅✅; pequena ❌800; retangular ❌1:1; inválida com orientação | ✅ quadrada_grande.jpg: 1000×1000 ✅ 1:1 ✅ ≥800px \| retangular.jpg: 1200×800 ❌ não é 1:1 ✅ ≥800px \| quadrada_pequena.jpg: 600×600 ✅ 1:1 ❌ abaixo |
| Cadastro do Produto | Marcar as 3 fotos obrigatórias: 3/3 | ✅ Obrigatórias completas. Se puder, some resultado e variação. |
| Hashtags | 3 boas: ✅ dentro da regra | ✅ ✅ 3 hashtags, dentro da regra. Confira no TikTok se alguma passa de 5 bi de views (genérica demais). |
| Hashtags | Com #fyp: aviso | ✅ ⚠️ Tire #fyp/#parati. Confira no TikTok se alguma passa de 5 bi de views (genérica demais). |
| Hashtags | Mais de 5: aviso | ✅ ⚠️ Mais de 5 dilui o foco. Confira no TikTok se alguma passa de 5 bi de views (genérica demais). |
| Hashtags | Repetida: aviso | ✅ ⚠️ Há hashtag repetida. Confira no TikTok se alguma passa de 5 bi de views (genérica demais). |
| Hashtags | Menos de 3 e sem plataforma: avisos | ✅ ⚠️ Use pelo menos 3. 💡 Falta a de plataforma/compra (ex.: #tiktokshop). Confira no TikTok se alguma passa de 5 bi de views (genérica demais) |
| Hashtags | Guardar conjunto e repetir: avisa para variar | ✅ ⚠️ Você já usou exatamente este conjunto. Varie pelo menos 1 hashtag. Confira no TikTok se alguma passa de 5 bi de views (genérica demais). |
| Legenda | Legenda boa: 3 ✅ | ✅ ✅ 1ª linha com 59/150 caracteres; ✅ palavra-chave “bolsa tote” na 1ª linha; ✅ CTA no fim (ex.: “Clica no carrinho.”); 💡 Diga a palavra-chave |
| Legenda | Sem CTA e com mais de 150: ❌ nos dois | ✅ ❌ 1ª linha com 154/150 caracteres (o resto fica escondido; encurte); ❌ palavra-chave “bolsa tote” na 1ª linha; ❌ CTA no fim (ex.: “Clica no  |
| Legenda | Palavra-chave ausente na 1ª linha: ❌ | ✅ ❌ palavra-chave “mochila” na 1ª linha |
| Metas | Valores padrão 80 / 25 / 1 / 3 e vazio = "Sem medição" | ✅ ok |
| Metas | 82% retenção = ✅; 2,6% cliques = 🟡; 0,3% compart. = 🔴 com dica | ✅ ✅ Na meta \| 🟡 Perto da meta. Baixo: reveja a CTA e a prova. \| 🔴 Abaixo. Baixa: reforce curiosidade ou transformação. |
| Metas | Meta editada (conclusão 30%) continua após recarregar | ✅ 30 |
| Simulador | Começa em 0,0 e pede para marcar (antes começava em 10,0) | ✅ Nenhum item marcado ainda. Marque o que o seu roteiro já tem. |
| Simulador | Marcar gancho (1,5) + packing (2,0) = 3,5 | ✅ 3,5 |
| Vender | Sem vídeo próprio: Ponte/ROAS/Resultado travados com aviso | ✅ aviso 🔒 presente |
| Vírgula decimal | Digitar 129,90 no teclado vira 129.90 (antes virava 12990) | ✅ 129.90 |
| Vírgula decimal | Vale para todos os campos numéricos (meta de cliques 2,5) | ✅ 2.5 |
| Nota do Vídeo | Sem vídeo: mensagem diz o que fazer | ✅ Nenhum vídeo escolhido ainda. Toque em “Escolher arquivo” acima e selecione o vídeo gravado. |
| Nota do Vídeo | Vertical 1080×1920 com áudio + checklist completo: nota alta e dicas separadas | ✅ nota 7.3 em 15879 ms; Bom: ajuste 1 ou 2 itens |
| Nota do Vídeo | Vertical com voz forte, cortes a cada ~1,8 s e checklist completo: faixa "Pronto para postar" | ✅ nota 8.6; Áudio  Nada a corrigir aqui.  Gravação (imagem e formato)  Nada a corrigir aqui.  Roteiro e edição Quase nada se move nos 3 primei |
| Nota do Vídeo | Horizontal sem áudio: nota parcial, baixa, dica de 9:16 e de áudio | ✅ nota 3.1 |
| Nota do Vídeo | Áudio estourado: detecta clipping e tira ponto do áudio | ✅ nota 6.6 |
| Nota do Vídeo | Vídeo silencioso: "Não detectei voz", áudio 0 (antes dizia "voz alta demais") | ✅ nota 5.1 |
| Nota do Vídeo | Escuro, 75 s, voz baixa, sem movimento: dicas de luz, duração, voz e movimento | ✅ nota 3.9 |
| Nota do Vídeo | HEVC/H.265 (não suportado no navegador): mensagem útil, sem travar | ✅ Não consegui abrir este vídeo neste navegador. Isso costuma acontecer com vídeo HEVC/H.265 (padrão de alguns iPhones) ou (149 ms) |
| Nota do Vídeo | Faixas: ≥8,5 pronto; 7–8,4 ajustar; 5–6,9 regravar; <5 refazer | ✅ 8.6→Pronto, 7.3→Bom, 3.1→Refaça, 6.6→Regrave, 5.1→Regrave, 3.9→Refaça |
| Nota do Vídeo | Histórico das últimas notas aparece | ✅ · nota 5,1 · nota 6,6 · nota 3,1 · nota 8,6 · nota 7,3 |
| Nota do Vídeo | Vídeos analisados não saem do aparelho: só nota e números ficam no localStorage | ✅ 6 registros; maior: 205 bytes |
| Nota do Vídeo | Pesos dos componentes somam 10 (1, 1, 2, 1,5, 2, 2,5) | ✅ ok |
| Calibração | 10 registros: correlação nota × retenção 3s confere com o cálculo à mão (1.00) | ✅ Nota × resultado (10 vídeos): correlação forte (1,00). A nota acompanha o resultado. |
| Calibração | Por componente (Áudio técnico 1.00) e média por objetivo; aviso "correlação não prova causa" | ✅ Áudio técnico: forte (1,00) |
| Calibração | Trocar para cliques: correlação 0.06 | ✅ Nota × resultado (10 vídeos): correlação fraca (0,06). A nota ainda não prevê este resultado: revise os limites e o checklist. |
| Calibração | Campo vazio não vira zero: 3 sem conclusão → "Faltam 1 vídeo(s)" | ✅ Faltam 1 vídeo(s) com “Taxa de conclusão” preenchido para calibrar (mínimo 8). Hoje: 7. Preencha as métricas dos vídeos acima depois de 48h. |
| Calibração | Digitar a métrica no registro salva e recalcula | ✅ Nota × resultado (8 vídeos): correlação moderada e negativa (-0,37). A nota ainda não prevê este resultado: revise os limites e o checklist. |
| Calibração | Remover registro pede confirmação e remove | ✅ 10 → 9 |
| ROAS | Caso 1 confere à mão: margem R$ 43,52 e ROAS 2,98x | ✅ {"m":"R$ 43,52","r":"2,98x"} |
| ROAS | Caso 2 (com desconto) confere à mão: margem R$ 33,11 e ROAS 2,72x | ✅ {"m":"R$ 33,11","r":"2,72x"} |
| ROAS | Caso 3 (margem negativa): "Não viável" | ✅ {"m":"R$ -8,00","r":"Não viável"} |
| Resultado Financeiro | Confere à mão: contribuição paga R$ 551,45; resultado R$ 251,45; ROAS bruto 6,06x | ✅ Contribuição antes da mídia: R$ 551,45 \| Investimento em mídia: R$ 300,00 \| Resultado após mídia (lucro de contribuição): R$ 251,45 \| ROAS b |
| Resultado Financeiro | Rótulo do equilíbrio corrigido: é sobre o faturamento bruto (3,30x = 129,90 ÷ 39,39) | ✅ ROAS de equilíbrio (sobre o faturamento bruto, já com cancelamentos e devoluções): 3,30x: —: — |
| Ponte Comercial | Salva cliques e pedidos de vídeo próprio e mostra o funil | ✅ Pedidos / cliques: 2,86% |
| Comentário Fixado | Botão Copiar copia o modelo | ✅ Para quem perguntou: no vídeo testamos [itens que realmente foram colocados na b |
| Respostas Rápidas | Botão Copiar copia a resposta | ✅ Cabe sim: no vídeo mostramos [itens testados, ex.: caderno A5 e garrafa de 500 m |
| 📖 Guia passo a passo | Botão abre o guia: 7 passos, passos 2, 4 e 5 detectados, manual embutido | ✅ 3 de 7 passos feitos. · capítulos do manual: 7 |
| 📖 Guia passo a passo | Marcação manual (passo 1) fica salva | ✅ 4 de 7 passos feitos. |
| 📖 Guia passo a passo | "Ir para" fecha o guia e leva à seção | ✅ ok |
| Backup | Backup inclui as chaves novas (notas, metas, roteiros, hashtags, guia) | ✅ mafeNotasV1, mafeMetasV1, mafeRoteirosV1, mafeHashtagsV1, mafeGuiaV1 |
| Backup | Depois de limpar: dados novos somem (prova de que o teste é real) | ✅ mafeNotasV1 = null |
| Backup | Restaurar devolve todas as chaves novas idênticas | ✅ mafeNotasV1= mafeMetasV1= mafeRoteirosV1= mafeHashtagsV1= mafeGuiaV1= |
| Backup | Ida e volta: chaves do Radar comparadas antes × depois | ✅ 13 chaves idênticas |
| Backup | Botão ↶ Desfazer restauração aparece após restaurar | ✅ visível no menu 💾 Dados |
| Backup | Mesclar não apaga dado novo que não estava no backup | ✅ 10 registros |
| 🧪 Verificar integridade | Testes de regressão do próprio painel | ✅ Testes de regressão P0–P2: 57/57 aprovados.  Nenhuma falha detectada nos testes executados. Confira o console para o relatório completo. |
| Centro V4 | Bateria de testes do Centro de Inteligência: 100% (corrigido teste que usava seletor errado; o original dava 38/39) | ✅ 39/39 testes aprovad |
| Segurança | Token digitado no Centro V4 não é salvo no navegador | ✅ não encontrado em nenhuma chave |
| Carregamento | Sem erros de console depois de todos os testes (1280 px) | ✅ 0 erros |
| Celular/desktop | 360 px, claro: sem rolagem horizontal da página | ✅ scrollWidth 360 / largura 360 |
| Carregamento | 360 px, claro: zero erros de console | ✅ 0 |
| Celular/desktop | 360 px, escuro: sem rolagem horizontal da página | ✅ scrollWidth 360 / largura 360 |
| Carregamento | 360 px, escuro: zero erros de console | ✅ 0 |
| Celular/desktop | 1280 px, claro: sem rolagem horizontal da página | ✅ scrollWidth 1280 / largura 1280 |
| Carregamento | 1280 px, claro: zero erros de console | ✅ 0 |
| Celular/desktop | 1280 px, escuro: sem rolagem horizontal da página | ✅ scrollWidth 1280 / largura 1280 |
| Carregamento | 1280 px, escuro: zero erros de console | ✅ 0 |
| Acessibilidade | Contraste ≥ 4,5:1 nos elementos novos do painel (claro) | ✅ 3792 textos medidos; menor 4.87:1 |
| Acessibilidade | Contraste ≥ 4,5:1 nos elementos novos do painel (escuro) | ✅ 3792 textos medidos; menor 6.14:1 |
| Manual | 360 px: abre sem erros, padrão segue o aparelho (claro) | ✅ light |
| Manual | 360 px: alternar para escuro e recarregar mantém a escolha | ✅ {"th":"dark","txt":"☀️ Claro","pr":"true"} |
| Manual | 360 px · escuro · zoom 80%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"80","sw":360,"cw":360,"cut":0,"tblOk":true,"headBelowBar":true,"barH":87,"minBtn":44,"barInView":true} |
| Manual | 360 px · escuro · zoom 100%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"100","sw":360,"cw":360,"cut":0,"tblOk":true,"headBelowBar":true,"barH":87,"minBtn":44,"barInView":true} |
| Manual | 360 px · escuro · zoom 200%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"200","sw":360,"cw":360,"cut":0,"tblOk":true,"headBelowBar":true,"barH":87,"minBtn":44,"barInView":true} |
| Manual | 360 px · escuro: abrir e fechar uma analogia | ✅ {"abriu":true,"visivel":true,"fechou":true} |
| Manual | Contraste ≥ 4,5:1 (escuro, 360 px, analogias abertas) | ✅ 3116 textos; menor 8.45:1 |
| Manual | 360 px · claro · zoom 80%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"80","sw":360,"cw":360,"cut":0,"tblOk":true,"headBelowBar":true,"barH":87,"minBtn":44,"barInView":true} |
| Manual | 360 px · claro · zoom 100%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"100","sw":360,"cw":360,"cut":0,"tblOk":true,"headBelowBar":true,"barH":87,"minBtn":44,"barInView":true} |
| Manual | 360 px · claro · zoom 200%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"200","sw":360,"cw":360,"cut":0,"tblOk":true,"headBelowBar":true,"barH":87,"minBtn":44,"barInView":true} |
| Manual | 360 px · claro: abrir e fechar uma analogia | ✅ {"abriu":true,"visivel":true,"fechou":true} |
| Manual | Contraste ≥ 4,5:1 (claro, 360 px, analogias abertas) | ✅ 3116 textos; menor 6.97:1 |
| Manual | 360 px: valor de zoom inválido salvo volta a 100% | ✅ 100% |
| Manual | 1280 px: abre sem erros, padrão segue o aparelho (claro) | ✅ light |
| Manual | 1280 px: alternar para escuro e recarregar mantém a escolha | ✅ {"th":"dark","txt":"☀️ Claro","pr":"true"} |
| Manual | 1280 px · escuro · zoom 80%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"80","sw":1280,"cw":1280,"cut":0,"tblOk":true,"headBelowBar":true,"barH":61,"minBtn":44,"barInView":true} |
| Manual | 1280 px · escuro · zoom 100%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"100","sw":1280,"cw":1280,"cut":0,"tblOk":true,"headBelowBar":true,"barH":61,"minBtn":44,"barInView":true} |
| Manual | 1280 px · escuro · zoom 200%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"200","sw":1280,"cw":1280,"cut":0,"tblOk":true,"headBelowBar":true,"barH":61,"minBtn":44,"barInView":true} |
| Manual | 1280 px · escuro: abrir e fechar uma analogia | ✅ {"abriu":true,"visivel":true,"fechou":true} |
| Manual | Contraste ≥ 4,5:1 (escuro, 1280 px, analogias abertas) | ✅ 3116 textos; menor 8.45:1 |
| Manual | 1280 px · claro · zoom 80%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"80","sw":1280,"cw":1280,"cut":0,"tblOk":true,"headBelowBar":true,"barH":61,"minBtn":44,"barInView":true} |
| Manual | 1280 px · claro · zoom 100%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"100","sw":1280,"cw":1280,"cut":0,"tblOk":true,"headBelowBar":true,"barH":61,"minBtn":44,"barInView":true} |
| Manual | 1280 px · claro · zoom 200%: sem rolagem horizontal, sem texto cortado, título não fica sob a barra, botões ≥ 44 px | ✅ {"zoom":"200","sw":1280,"cw":1280,"cut":0,"tblOk":true,"headBelowBar":true,"barH":61,"minBtn":44,"barInView":true} |
| Manual | 1280 px · claro: abrir e fechar uma analogia | ✅ {"abriu":true,"visivel":true,"fechou":true} |
| Manual | Contraste ≥ 4,5:1 (claro, 1280 px, analogias abertas) | ✅ 3116 textos; menor 6.97:1 |
| Manual | 1280 px: valor de zoom inválido salvo volta a 100% | ✅ 100% |
| Manual | Com armazenamento bloqueado: página funciona (tema e zoom mudam, sem erro) | ✅ ok |
| Manual | Sem escolha salva, segue o aparelho em modo escuro | ✅ prefers-color-scheme: dark |
| Manual | Impressão: modo claro, tamanho normal, sem barra, analogias no apêndice (mesmo salvo em escuro + 200%) | ✅ {"barra":"none","fundo":"rgb(255, 255, 255)","texto":"rgb(0, 0, 0)","fonte":"14.6667px","analogia":"none","apendice":"block"} |
| Manual (PDF) | PDF gerado com apêndice de analogias | ✅ 72 páginas; apêndice: True |
| Painel | Modo escuro e zoom do painel ficam salvos após recarregar | ✅ {"th":"dark","z":"110%"} |

Capturas de tela em `testes/` (painel 360/1280 claro/escuro, nota do vídeo, manual em 200%, impressão).

## Autoavaliação (0 a 10)

| Item | Nota | Evidência |
|---|---|---|
| Funcionamento | 9 | 130/130 testes; 57/57 integridade; 39/39 Centro V4; 25 combinações de roteiro; contas de ROAS e financeiro conferidas à mão |
| Ausência de erros | 9 | `node --check` em 24 + 2 scripts; zero erros de console em 4 combinações de tela/tema e após todos os testes |
| Didática do painel | 9 | Quadro "Como usar" em 57/57 seções; guia de 7 passos com progresso; 0 campos visíveis sem exemplo; telas vazias e erros com próximo passo |
| Clareza do manual | 9 | Teste de leigo independente (acima) e correções aplicadas; nomes conferidos por script contra a tela |
| Acessibilidade | 7 | Contraste medido ≥ 4,5:1 em todos os textos novos (menor 4,87:1 claro); foco visível; aria-pressed; botões do manual ≥ 44 px. **Não testado com leitor de tela real**, por isso não passa de 7 |
| Uso no celular | 7 | 360 px sem rolagem horizontal, zoom 80–200% sem corte, barra não cobre títulos. **Testado em navegador emulado, não em aparelho real** (Safari iOS e Chrome Android), por isso não passa de 7 |
| Honestidade | 9 | Avisos de "indicador, não garantia", metas do curso, urgência só se for verdade; nota parcial em vez de zero; o painel diz que não reconhece o produto |
| Segurança dos dados | 9 | Sem chaves/tokens; sem recursos externos; vídeos e fotos ficam no aparelho (só nota e números no localStorage); token do Centro V4 não é salvo; backup ida e volta idêntico |

## Limitações conhecidas (o que não foi testado)
- **Aparelhos reais:** só navegador emulado (Chromium). Safari no iPhone toca HEVC e pode medir de forma diferente; Chrome no Android não foi aberto.
- **Leitor de tela** (VoiceOver/TalkBack/NVDA): não testado.
- **Vídeos reais com fala:** os testes usaram vídeos sintéticos (tom e ruído). Os limites da nota (dB, cortes, movimento) precisam ser calibrados com vídeos reais da Mafê — é para isso que serve a Calibração.
- **Impressão:** conferida por emulação de mídia de impressão e pelo PDF gerado; a janela de impressão do navegador não foi aberta.
- **Copiar para a área de transferência:** testado no Chromium com permissão; outros navegadores podem bloquear (há botão de baixar .txt como alternativa).

## Próximos passos
1. Analisar 8 vídeos reais da Mafê na Nota e preencher a Calibração depois de 48h.
2. Abrir o painel no celular de quem vai usar (iPhone e Android) e conferir o Guia passo a passo.
3. Se quiser transcrição automática, decidir sobre a proposta de servidor próprio do README.
