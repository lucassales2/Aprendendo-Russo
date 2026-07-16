# 🇷🇺 Aprendendo Russo

Vault do Obsidian + repositório Git para aprender russo usando **comandos de voz com o Claude**.

Este README explica a arquitetura, como sincronizar (iCloud + Git) e como usar o Claude por voz para gerar as notas.

---

## 🧭 Arquitetura

```
┌─────────────────┐   voz    ┌──────────────┐   MD    ┌──────────────────────┐
│  App do Claude   │ ───────▶ │    Claude    │ ──────▶ │  Este vault (.md)     │
│  (celular)       │          │              │         │  = pasta do Obsidian  │
└─────────────────┘          └──────────────┘         └──────────┬───────────┘
                                                                  │
                          ┌───────────────────────────────────────┼───────────────┐
                          ▼                                       ▼
                  ┌───────────────┐                       ┌───────────────┐
                  │    iCloud     │  sincroniza           │      Git       │  versiona
                  │  (Mac/iPhone) │  dispositivos         │   (GitHub)     │  + Claude edita
                  └───────────────┘                       └───────────────┘
```

- **iCloud** mantém o vault igual entre Mac, iPhone e iPad em tempo real.
- **Git** versiona o histórico e é como o **Claude** lê/escreve nas notas.
- **Voz** entra pelo **app do Claude**: você fala, o Claude devolve a lição/correção e salva em `.md`.

---

## 📁 Estrutura — dois módulos

O vault é dividido em dois módulos independentes:

| Módulo | Para quê |
|--------|----------|
| **`modulo-solo/`** | Estudo autônomo com o Claude (prompts, lições, vocabulário, gramática) |
| **`modulo-aulas/`** | Acompanhar as aulas (resumos, tarefas, dúvidas) |
| `recursos/` | Links e materiais compartilhados entre os módulos |

Cada módulo tem seu próprio `README.md` explicando as pastas internas.

---

## ⚙️ Como configurar (iCloud + Git juntos)

### 1. Colocar o vault no iCloud
1. Clone este repositório para dentro do iCloud Drive, ex.:
   `~/Library/Mobile Documents/com~apple~CloudDocs/Obsidian/Aprendendo-Russo`
2. No Obsidian: **Abrir pasta como cofre (vault)** → selecione essa pasta.
3. No iPhone/iPad, o mesmo vault aparece via **Obsidian Mobile** (fonte: iCloud).

> ⚠️ iCloud e Git no mesmo diretório funcionam, mas evite fazer `git` e sincronização do iCloud gravando ao mesmo tempo. Faça commits quando o iCloud estiver "em dia".

### 2. Sincronizar com o Git
Opção A — plugin **Obsidian Git** (recomendado no desktop): commita/puxa automaticamente.
Opção B — manual no terminal:
```bash
git add -A && git commit -m "estudo do dia" && git push
```

### 3. Usar o Claude por voz (celular)
1. Abra o **app do Claude** e use o **microfone**.
2. Fale, por exemplo: *"Me dê uma lição de russo sobre o caso acusativo, nível iniciante, com 5 frases e áudio fonético."*
3. Copie a resposta para uma nota, **ou** peça ao Claude Code (web) para escrever direto no vault via este repositório.

---

## 🎙️ Fluxo de estudo sugerido

1. **Aquecimento** — revisão rápida do vocabulário (`modulo-solo/prompts/flashcards.md`).
2. **Conversa** — pratique diálogo com o tutor (`modulo-solo/prompts/tutor-conversa.md`).
3. **Correção** — cole o que você escreveu/falou e peça correção (`modulo-solo/prompts/correcao.md`).
4. **Registro** — salve a sessão em `modulo-solo/licoes/AAAA-MM-DD.md` (use o template do módulo).
5. **Commit** — `Commit-and-sync` no Obsidian para versionar o progresso.

---

## 🧩 Seus prompts

Coloque seus prompts bons em `modulo-solo/prompts/`, um por arquivo `.md`. Já deixei alguns modelos
prontos lá — pode substituir pelos seus. Formato recomendado no topo de cada prompt:

```markdown
---
titulo: Tutor de conversação
idioma: russo
nivel: iniciante
uso: colar no app do Claude
---
```

Cole aqui os seus prompts que eu adapto para esse formato e integro ao vault.
