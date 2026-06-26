# REQUISITOS_leiana-site.md
Auditoria de entrega — site Leiana Rodrigues  
Data: 2026-06-18 | Commit: a315431

---

## PRÉ-TRABALHO

| # | Tarefa | Critério de aceite | Status |
|---|--------|--------------------|--------|
| P01 | Criar branch `template-saude-pos-operatorio` a partir do HEAD atual (antes de qualquer alteração) e fazer push para o GitHub | Branch existe em `git branch -a` e no GitHub remoto; arquivos no branch são idênticos ao estado atual de `main` antes das edições | **FEITO** — branch local + remoto confirmado |

---

## REQUISITOS

| # | Descrição | Critério de aceite | Status |
|---|-----------|-------------------|--------|
| R01 | Substituir `href="#"` pelos links reais de WhatsApp nos 3 botões: hero, contato e flutuante | Cada `<a>` tem `href="https://wa.me/5561995289852?text=..."` com mensagem codificada; JS de tracking `data-wa` permanece intacto | **FEITO** — `grep 'href="#"' index.html` retorna zero |
| R02 | Substituir `COREN-DF Nº XXXXX-ENF` por `COREN-DF Nº 354-413-ENF` nos dois lugares, com comentário de aviso | Zero ocorrências de `XXXXX`; dois comentários `<!-- CONFIRMAR... -->` presentes | **FEITO** — linhas 454–455 e 695–696 |
| R03 | Remover a pasta `invite/`, seção `#presente`, `#aviso` e JS correspondente | `git ls-files invite/` vazio; busca por `btnAbrirPresente`/`fimVisto` retorna zero | **FEITO** — `invite/.invite-trunc.bak` e `invite/index.html` deletados; JS removido |
| R04 | Remover ícones e botões de Facebook, YouTube e TikTok e o modal "esse canal não existe" | Busca por `data-rede`, `modalRede`, `fecharModal`, `Facebook`, `YouTube`, `TikTok` retorna zero | **FEITO** — count = 0 verificado |
| R05 | Marcar como "em breve" os 3 serviços não confirmados com badge e opacidade reduzida | Os 3 cards têm `class="card soon"` e `<span class="badge-soon">Em breve</span>`; 4 confirmados sem alteração | **FEITO** — CSS `.card.soon` + `.badge-soon` adicionados |
| R06 | Seção "Onde atendo" com 22 localidades em texto corrido elegante | Todos os 22 topônimos no HTML; formatação usa `.atende-body p` (var CSS existentes); seção com `id="onde-atendo"` | **FEITO** — seção adicionada após `#contato` |
| R07 | Manter 4 depoimentos em texto como fallback; array `DEPOIMENTOS_IG` no topo do script; se slot tiver URL → embed; se vazio → texto | Array `DEPOIMENTOS_IG` presente; todos os `.q` cards têm `data-ig-slot`; embed.js só carregado se houver URL | **FEITO** — array na linha 712; lógica de swap na linha 764 |
| R08 | 2 novos cards FAQ: (a) laser + taping explicados; (b) ferida normal vs. alerta | Tipgrid de 6 → 8 cards; tom calmo/técnico; sem linguagem de venda | **FEITO** — R08a (`.lbl` `laserterapia · taping`) e R08b (`.lbl` `sinais de alerta`) adicionados |
| R09 | Bloco "Planos e valores" com formulário Web3Forms (nome, WA, e-mail, serviço); `WEB3FORMS_KEY` configurável; confirmação inline; cópia para leiana.rod.enf@gmail.com | `const WEB3FORMS_KEY = "COLAR_ACCESS_KEY_AQUI"` no topo; 4 campos + select; `action="https://api.web3forms.com/submit"`; `replyto` = leiana.rod.enf@gmail.com; sem preços no repo | **FEITO** — seção `#planos` adicionada antes de `#contato` |
| R10 | Botão "Agendar na agenda" (ghost) ao lado do WA na seção Contato | Botão existe com `href="COLAR_LINK_AGENDA_AQUI"` e comentário `<!-- COLAR LINK DA AGENDA... -->`  | **FEITO** — linha 659–661 |
| R11 | Regra de copy: sem linguagem agressiva de venda | Busca por `garantid`, `revolucionár`, `imediata` retorna zero nos trechos novos | **FEITO** — verificado nos 8 novos blocos |
| R12 | Regra de privacidade: sem dados financeiros/estratégicos no repositório | Busca por `faturamento`, `18-24`, `pacientes/mês` retorna zero | **FEITO** — count = 0 verificado |
| R13 | Regra de design: apenas variáveis CSS e classes já existentes nos blocos novos | Sem nova fonte, cor hex avulsa ou breakpoint; `.plans`, `.form-cta`, `.atende` usam somente `var(--*)` existentes | **FEITO** — inspeção do CSS confirma |

---

## Pendências para Bruno completar após entrega

| Ação | Onde |
|------|------|
| Gerar `access_key` em web3forms.com e colar em `WEB3FORMS_KEY` | Linha 707 de `index.html` |
| Configurar autoresponder no painel do Web3Forms com os planos e preços | web3forms.com → Forms → Autoresponder |
| Colar URL do Google Calendar em `href="COLAR_LINK_AGENDA_AQUI"` | Linha 659 de `index.html` |
| Colar URLs dos posts/reels do Instagram em `DEPOIMENTOS_IG` para ativar embeds | Linhas 713–716 de `index.html` |
| Confirmar número COREN-DF com a carteirinha real antes de publicar | Comentários nas linhas 454 e 695 |
| Push para `origin/main` para publicar no GitHub Pages | `git push origin main` |

---

## Itens cortados / não entregues
Nenhum. Todos os 13 requisitos foram entregues.
