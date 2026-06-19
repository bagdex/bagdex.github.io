# 🍺 Legendários do Álcool — Bolão Copa 2026

## 📁 Arquivos

```
bolao-legendarios/
├── index.html   ← Aplicação (não editar)
├── data.js      ← Dados e configuração do Google Sheets
└── README.md
```

---

## 🚀 Deploy no GitHub Pages

1. Crie um repositório no GitHub
2. Faça upload dos 3 arquivos
3. **Settings → Pages → Source: main branch / root**
4. Acesse `https://seu-usuario.github.io/nome-do-repo`

---

## 🔗 Conectar ao Google Sheets (fonte dos resultados)

### Passo 1 — Crie a planilha

Crie uma planilha no Google Sheets com **uma aba chamada `Resultados`** e estas colunas:

| Rodada   | Jogo                          | Resultado |
|----------|-------------------------------|-----------|
| rodada2  | Brasil x Haiti                | 4x0       |
| rodada2  | Alemanha x Costa do Marfim    | 2x1       |
| rodada2  | Argentina x Áustria           | 3x0       |

> ⚠️ Os nomes dos jogos devem ser **idênticos** aos que estão em `data.js`.

### Passo 2 — Torne a planilha pública

`Compartilhar → Alterar para "Qualquer pessoa com o link" pode visualizar`

### Passo 3 — Copie o ID da planilha

Na URL da planilha:
```
https://docs.google.com/spreadsheets/d/  1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgVE2upms  /edit
                                         ↑─────────────── este é o ID ──────────────────↑
```

### Passo 4 — Cole o ID no data.js

```js
googleSheet: {
  sheetId: "1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgVE2upms",  // ← seu ID aqui
  tabName: "Resultados",
  autoRefreshMinutes: 5
},
```

Faça commit e push. Pronto — o site busca os resultados automaticamente a cada 5 minutos!

---

## ⚽ Como atualizar um resultado

1. Abra sua planilha do Google Sheets
2. Adicione (ou edite) a linha com `rodada | jogo | placar`
3. O site atualiza automaticamente dentro de até 5 minutos, ou clique em **🔄 Atualizar**

---

## 🏆 Pontuação

| Acerto | Pontos |
|--------|--------|
| Placar exato (ex: apostou `2x1`, saiu `2x1`) | ✅ **1 ponto** |
| Qualquer outro resultado | ❌ 0 pontos |

---

## 🔄 Como adicionar nova rodada

Em `data.js`, adicione um bloco em `rounds[]` e as previsões em `participants[]`.

```js
// Em rounds[]:
{
  id: "rodada3",
  label: "Rodada 3",
  dates: "...",
  matches: ["País A x País B", ...],
  results: {}
}

// Em cada participante (predictions):
"rodada3": ["2x1", "0x0", ...]
```

Na planilha, adicione as linhas com `rodada3 | jogo | placar` normalmente.
