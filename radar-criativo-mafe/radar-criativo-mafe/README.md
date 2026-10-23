# Radar Criativo Mafê

Painel HTML de análise de vídeos de referência (TikTok) da **Mafê Bolsas**.

- **Versão do painel:** v4 — Inteligência e Validação
- **Vídeos:** 26 (V01–V26)
- **Data de coleta das métricas:** 21/10/2026

## Estrutura

```
index.html          Painel completo (arquivo único, sem dependências externas)
dados/videos.json   Cópia dos dados dos 26 vídeos, para histórico e comparação
.gitignore          Bloqueia backups, planilhas, vendas e segredos
```

## Como usar

Abra `index.html` direto no navegador (duplo clique). Funciona offline.

> Tudo que você digita no painel (vídeos adicionados, testes A/B, histórico de métricas)
> fica no `localStorage` **do seu navegador**, não neste repositório.
> Use o backup/importação do próprio painel para levar dados entre dispositivos.

## Regras deste repositório

1. **Mantenha o repositório privado.** Ele contém legendas e textos originais de terceiros
   e a estratégia criativa da marca.
2. **Não versione dados de vendas** (cliques, pedidos, faturamento). Guarde em `dados/privado/`,
   que o `.gitignore` já ignora.
3. **Nunca coloque tokens ou chaves de API** no HTML. Os endereços `seu-dominio.com`
   do módulo de sincronização são apenas exemplos.
4. `dados/videos.json` é uma **cópia de referência**: o painel lê os dados que estão
   dentro do `index.html`. Se editar um, atualize o outro.

## Fluxo de versões

- Uma mudança = um commit, com mensagem clara (ex.: `v4: integra legendas originais ao SEO`).
- Ao fechar uma versão nova, crie uma tag: `git tag v4.1` e `git push --tags`.

## Publicar online (opcional)

O GitHub Pages grátis exige repositório público. Para manter privado com link, use
Cloudflare Pages + Access ou Netlify com senha.
