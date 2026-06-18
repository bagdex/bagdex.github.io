# 🍺 Legendários do Álcool — Bolão Copa 2026

Mini sistema de classificação para o bolão da Copa do Mundo 2026.

## 📁 Estrutura de Arquivos

```
bolao-legendarios/
├── index.html   ← Aplicação completa (não editar)
├── data.js      ← ARQUIVO DE DADOS (editar aqui!)
└── README.md    ← Este arquivo
```

---

## 🚀 Deploy no GitHub Pages

1. Crie um repositório no GitHub (pode ser privado ou público)
2. Faça upload dos 3 arquivos (`index.html`, `data.js`, `README.md`)
3. Vá em **Settings → Pages → Source: main branch / root**
4. Aguarde 1-2 minutos e acesse `https://seu-usuario.github.io/nome-do-repo`

---

## ⚽ Como Inserir Resultados dos Jogos

### Opção 1 — Pelo painel Admin (recomendado no dia a dia)
1. Abra o site e clique na aba **⚙️ Admin**
2. Digite o PIN (padrão: `1234`)
3. Insira os placares no formato `2x1`, `0x0`, etc.
4. Clique em **💾 Salvar Resultados**

> ⚠️ Os resultados inseridos pelo Admin ficam salvos no **localStorage do navegador**.
> Isso significa que **apenas você** (no seu dispositivo) verá a classificação atualizada.
> Para que **todos** vejam, use a Opção 2 abaixo.

### Opção 2 — Atualizar data.js (para todos verem)
1. No painel Admin, clique em **📋 Exportar data.js**
2. Copie o bloco de `results` gerado
3. Abra `data.js` no GitHub e localize a rodada correspondente
4. Substitua o `results: {}` pelo bloco copiado
5. Faça commit → o site atualiza em ~1 minuto

**Exemplo** de `results` preenchido em `data.js`:
```js
results: {
  "República Tcheca x África do Sul": "1x0",
  "Suíça x Bósnia": "2x1",
  "Canadá x Catar": "3x0",
  // ... continua
}
```

---

## 🏆 Regras de Pontuação

| Acerto | Pontos |
|--------|--------|
| Placar exato (ex: apostou `2x1`, saiu `2x1`) | ✅ **1 ponto** |
| Qualquer outro resultado | ❌ **0 pontos** |

A classificação é ordenada automaticamente do maior para o menor total de pontos.

---

## 🔄 Como Adicionar uma Nova Rodada

Abra `data.js` e, dentro do array `rounds`, adicione um novo bloco:

```js
rounds: [
  {
    id: "rodada2",   // ← rodada atual (já existe)
    // ...
  },
  {
    id: "rodada3",                        // ← ID único da nova rodada
    label: "Rodada 3",                    // ← Nome exibido no site
    dates: "24–29 jun 2026",              // ← Período dos jogos
    matches: [
      "País A x País B",
      "País C x País D",
      // ... todos os jogos desta rodada
    ],
    results: {}                           // ← Preencher após os jogos
  }
],
```

Para cada participante em `participants`, adicione as previsões da nova rodada:
```js
{
  name: "Breno",
  predictions: {
    "rodada2": [...],        // ← já existe
    "rodada3": [             // ← adicionar
      "2x1", "1x0", "3x0",  // ... um placar por jogo, na mesma ordem que matches[]
    ]
  }
}
```

---

## 🔐 Alterar o PIN do Admin

No `data.js`, altere a linha:
```js
adminPin: "1234",   // ← troque por qualquer número de 4 dígitos
```

---

## 🛠️ Tecnologias

- HTML + CSS + JavaScript puro (zero dependências externas)
- Armazenamento local via `localStorage`
- Compatível com GitHub Pages (sem backend necessário)
