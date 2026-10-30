# Radar Criativo Mafê

Painel HTML de análise e criação de vídeos para o TikTok Shop da **Mafê Bolsas**.

- **Versão do painel:** v4.2 — Didática e Validação
- **Vídeos de referência:** 26 (V01–V26), métricas coletadas em 21/10/2026
- **Manual:** `Manual_Radar_Criativo_Mafe.html` (tela) e `Manual_Radar_Criativo_Mafe.pdf` (impressão). O mesmo conteúdo está dentro do painel, no botão **📖 Guia passo a passo**.

## Estrutura

```
index.html                         Painel completo (arquivo único, sem dependências externas, funciona offline)
Manual_Radar_Criativo_Mafe.html    Manual com modo noite e zoom (gerado a partir do index final)
Manual_Radar_Criativo_Mafe.pdf     Versão para imprimir (modo claro, analogias no apêndice)
README.md                          Este arquivo
dados/videos.json                  Cópia de referência dos 26 vídeos (não mudou nesta versão)
.gitignore                         Bloqueia backups, planilhas, vendas e segredos
```

## Como usar

1. Dê dois cliques em `index.html`. Abre no navegador e funciona sem internet.
2. Toque em **📖 Guia passo a passo** e siga os 7 passos: Analisar → Planejar → Gravar → Testar → Medir → Vender → Repetir.
3. Em cada seção, abra **📖 Como usar esta seção** para ver para que serve, o que fazer e o que fazer depois.

> Tudo o que você digita fica no `localStorage` **deste navegador**, não neste repositório.
> Faça **💾 Dados ▾ → 💾 Backup completo (JSON)** toda semana. Para voltar: **📤 Restaurar backup**.
> Vídeos e fotos analisados nunca saem do aparelho: o painel guarda só a nota e os números.

## Regras deste repositório

1. **Mantenha o repositório privado.** Ele contém legendas e textos originais de terceiros e a estratégia criativa da marca.
2. **Não versione dados de vendas** (cliques, pedidos, faturamento) nem backups `.json`. Guarde em `dados/privado/`, que o `.gitignore` ignora.
3. **Nunca coloque tokens ou chaves de API** no HTML. Os endereços `seu-dominio.com` do Centro de Inteligência são exemplos. O token digitado ali não é salvo.
4. **Arquivo único:** sem CDN, sem fonte externa, sem chamada de rede. Mudanças são aditivas: não remova funções existentes.
5. **Honestidade:** nada de prova, preço, estoque ou escassez inventados; urgência só se for verdade; metas são do curso, não benchmarks oficiais do TikTok; a nota é indicador, não garantia; campo vazio nunca vira zero.
6. `dados/videos.json` é cópia de referência: o painel lê os dados que estão dentro do `index.html`. Se editar um, atualize o outro.

## Chaves no navegador (todas entram no backup)

| Chave | O que guarda | Desde |
|---|---|---|
| `mafeNotasV1` | Notas da ⭐ Nota do Vídeo, ID, objetivo e métricas da calibração (sem o vídeo) | v4.1 |
| `mafeMetasV1` | Metas editadas em 🎯 Metas | v4.2 |
| `mafeRoteirosV1` | Últimos 30 roteiros gerados, com ID | v4.2 |
| `mafeHashtagsV1` | Conjuntos de hashtags já usados (para avisar repetição) | v4.2 |
| `mafeGuiaV1` | Passos marcados à mão no 📖 Guia passo a passo | v4.2 |
| `mafeManualTema`, `mafeManualZoom` | Tema e zoom do arquivo do manual | v4.2 |

O backup completo leva todas as chaves que contêm "mafe" ou "radar". Restaurar em modo **Mesclar** não apaga dados que não estavam no backup.

## Fluxo de versões

- Uma mudança = um commit, com mensagem clara (ex.: `v4.2: guia passo a passo e manual`).
- Ao fechar uma versão, crie uma tag: `git tag v4.2` e `git push --tags`.
- Antes de cada versão: abra o painel, rode **🧪 Verificar integridade** e, no Centro de Inteligência, **Executar bateria de testes**. As duas devem ficar em 100%.

## Publicar online (opcional)

O GitHub Pages grátis exige repositório público. Para manter privado com link, use Cloudflare Pages + Access ou Netlify com senha.

## Proposta separada: IA de verdade (não está no HTML)

O painel não transcreve fala nem reconhece o produto na imagem. Se valer a pena, o caminho seguro é **fora do HTML**: um servidor próprio (ex.: função na Cloudflare ou Netlify) que recebe o vídeo, chama um serviço de transcrição e de visão com a chave guardada **no servidor**, e devolve JSON com: transcrição com tempos, contagem da palavra-chave na fala, momento em que o produto aparece e texto na tela. O Centro de Inteligência V4 já tem o campo de endereço e o contrato de resposta. Custos, privacidade (vídeo sai do aparelho) e consentimento precisam ser decididos antes. Nada disso foi implementado.

## Histórico

### v4.2 — Didática e Validação (29/10/2026)

Correções
- Zoom: navegador novo abria em 70% (lia "vazio" como 0). Agora abre em 100%.
- Nota do Vídeo: vídeo em silêncio aparecia como "voz alta demais". Agora diz "Não detectei voz".
- Nota do Vídeo: vídeo sem trilha de áudio levava 0 em 3,5 pontos. Agora vira **nota parcial** reescalada, com aviso (campo não medido não vira zero).
- Nota do Vídeo: nota arredondada antes da faixa (8,46 não aparece como "8,5 ajustar"); casas decimais em português.
- Nota do Vídeo: vídeo que não abre (HEVC/H.265) agora tem mensagem com causa e solução; espera máxima de 20 s; libera o arquivo da memória sem erro no console.
- Simulador de Roteiro começava em 10,0 com tudo marcado. Agora começa em 0,0 e pede para marcar.
- Português: "não cabe" → "não cabem"; "até ao fim" → "até o fim"; decimais "1.5s" → "1,5 s"; frase da calibração reescrita.
- Ganchos com nomes diferentes entre módulos: agora todos se referem aos 6 tipos (Status = Desejo; Dor/Espaço = Dor).
- Meta de conclusão 25% × 30%: o painel usa 25% como mínimo e explica que o curso fala em 25–30%.
- Resultado Financeiro: o "ROAS líquido de equilíbrio" na verdade é sobre o faturamento bruto. Rótulo corrigido (a conta não mudou).
- Centro V4: o teste "Referências bloqueadas" falhava por usar o seletor errado. Agora 39/39.
- Mensagens de erro reescritas: dizem o que aconteceu e como corrigir.

Novas funções
- **📖 Guia passo a passo** (botão no topo e no menu): progresso nos 7 passos (3 detectados sozinhos) e o manual completo dentro do painel. Motivo: dar um caminho único para quem nunca usou.
- **📖 Como usar esta seção** em todas as 57 seções, recolhido, com atalho "Ir para…" a próxima etapa. Aproveita os quadros antigos sem duplicar. Motivo: cada tela explica a si mesma.
- **ID do vídeo** liga roteiro → nota → calibração. Motivo: saber qual resultado é de qual roteiro.
- Roteiro: palavra-chave própria, ganchos A/B/C com o tipo, legenda com gancho + palavra-chave + CTA (sem cortar no meio), hashtags por tipo de bolsa, linha de SEO, **⬇️ Baixar roteiro (.txt)** e atalho para a Nota. Motivo: cumprir as regras do caderno sem retrabalho.
- Conferidor de **legenda** (1ª linha ≤ 150, palavra-chave, CTA no fim). Motivo: a regra existia só em texto.
- Hashtags: aviso de falta da hashtag de plataforma e de conjunto repetido (**🔖 Guardar como usadas neste vídeo**). Motivo: "varie entre vídeos".
- Metas: cabeçalho das colunas, exemplos e metas salvas (entram no backup). Motivo: metas editáveis se perdiam ao recarregar.
- Calibração: mostra o ID, aceita nota parcial, remove registro com confirmação e explica correlação negativa. Motivo: corrigir testes errados sem apagar tudo.
- **🔎 Busca no menu** (sem acento). Motivo: 58 links são muitos para rolar.
- Exemplos (placeholder) nos campos importantes e telas vazias com o próximo passo.

### v4.1
- Roteiro por foto e objetivo, nota do vídeo (áudio e gravação), 6 tipos de gancho, cadastro de produto, metas e rotina. Tudo roda no navegador, sem enviar arquivos.
