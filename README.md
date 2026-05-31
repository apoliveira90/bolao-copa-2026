# ⚽ Bolão Copa 2026

App de bolão para a Copa do Mundo 2026 — glassmorphism, placar ao vivo, ranking com premiação automática e palpites sincronizados via Google Drive.

---

## 🚀 Publicar no GitHub Pages

1. Crie repositório público `bolao-copa-2026`
2. Faça upload do `index.html`
3. **Settings → Pages → Branch: main / root → Save**
4. Acesse: `https://SEU-USUARIO.github.io/bolao-copa-2026/`

---

## 🔄 Sincronização de palpites via Google Drive

O `appsscript.gs` lê automaticamente os arquivos `.xlsx` da pasta do Drive e publica os palpites via endpoint JSON.

### Setup (uma única vez)

1. Acesse [script.google.com](https://script.google.com) → Novo projeto
2. Cole o conteúdo de `appsscript.gs`
3. Serviços → adicione **Drive API**
4. Execute `testar()` e autorize o acesso
5. **Implantar → Web App → Qualquer pessoa → Implantar**
6. Copie a URL `/exec` e cole em `index.html`:
   ```js
   const APPS_SCRIPT_URL = 'https://script.google.com/macros/s/.../exec';
   ```
7. Execute `configurarTrigger()` → sincroniza a cada 30 min

### Estrutura dos arquivos Excel na pasta do Drive

```
NomeParticipante - Qualquer texto.xlsx
```
- Coluna A: Nome do time 1
- Coluna B: Gols time 1 ← palpite
- Coluna C: Gols time 2 ← palpite
- Coluna D: Nome do time 2
- Linha 1 = cabeçalho (ignorado), dados a partir da linha 2

---

## 🏅 Regras de pontuação

| Resultado | Pontos |
|---|---|
| Placar exato | **5 pts** |
| Vencedor/empate certo | **3 pts** |
| Errou | **0 pts** |

## 💰 Premiação

- Cada participante: **R$ 30,00**
- **1º lugar:** 80% do acumulado
- **2º lugar:** 20% do acumulado
- **Empate no 1º:** 100% dividido igualmente, 2º sem premiação

---

## ✨ Funcionalidades

| | |
|---|---|
| 🏆 Ranking | Pódio, medalhas, distância do líder, indicador ▲▼▬ |
| 💰 Premiação | Cálculo automático por número de participantes |
| ⚽ Jogos | 72 jogos com bandeiras, filtros por grupo, placar ao vivo |
| 🔮 Simulador | Simule cenários e veja ranking projetado + ganho |
| 📊 Histórico | Aproveitamento por participante e gráfico de evolução |
| 🎯 Toast | Animação ao acertar placar exato |
| 🔄 Drive Sync | Palpites atualizados automaticamente do Google Drive |
| 📱 Responsivo | Funciona em mobile e desktop |
