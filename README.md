# sobreviver-ia

**🇧🇷 [Português](README.md) · 🇺🇸 [English](README.en.md) · 🇪🇸 [Español](README.es.md)**

[![sobreviver-ia](guia/assets/banner.jpg)](https://inematds.github.io/sobreviver-ia/guia/)

## O que é

O sobreviver-ia é um conjunto de ferramentas simples, que rodam no seu computador, para atravessar os próximos dois anos de IA com menos susto. Ele serve para qualquer pessoa ou família: calcula a comida, a água e o dinheiro de um kit de 14 dias, instala uma IA e a Wikipedia offline, mostra quais contas ainda dependem de SMS e mede, com tarefas do seu próprio trabalho, quanto a IA já faz por você. Precisa só de Python 3 (e, se quiser a IA offline, de espaço em disco). Nada usa chave de API.

## 📖 Guia de uso

Guia completo (landing + passo a passo, com dados e gráficos): **https://inematds.github.io/sobreviver-ia/guia/**

🎬 Vídeo: https://www.youtube.com/shorts/bgVHDEm1yGI

## Três horizontes de risco

| Horizonte | Risco | Ferramenta |
|---|---|---|
| Curto prazo | segurança física e digital | `kit/`, `offline/`, `seguranca/` |
| Médio prazo (2 anos) | trabalho e renda | `eval/`, `plano/` semanas 1–8 |
| Longo prazo | crenças e identidade | `plano/` semanas 9–13 |

Por que agora (fatos de 2026):
- **19%** — o emprego de 22 a 25 anos nas funções mais expostas à IA está cerca de 19% abaixo de onde estaria se acompanhasse as funções menos expostas. É um gap acumulado (13% → 15% → 19% nas versões do estudo), via contratação. Stanford Digital Economy Lab, "Canaries in the Coal Mine", ago/2026.
- **350+** — supermercados na França tiveram as geladeiras aquecidas até ~50 °C por ataque a controladores ligados à internet com senha fraca (11/10/2026, Reuters; outras fontes falam em 500–700).
- **Jul/2026** — modelos de IA em teste de segurança escaparam do sandbox e invadiram parte da Hugging Face.

## Ferramentas

| Arquivo | O que faz |
|---|---|
| `kit/calcula_kit.py` | pessoas × dias → calorias (2.000 kcal/pessoa/dia), água (1,5–2 L/pessoa/dia), galões, dinheiro de 1 mês, lista de não perecíveis; texto ou checklist markdown |
| `kit/checklist-casa.md` | comida, água, dinheiro, primeiros socorros, extintor, lanterna, rádio, power bank, pessoas |
| `offline/instala-offline.sh` | Ollama + modelo pequeno + Kiwix + Wikipedia (pt/en/es; mini/nopic/maxi). **Dry-run por padrão** |
| `seguranca/checklist-mfa.md` | sair do SMS: ordem de prioridade e passo a passo por conta |
| `seguranca/auditoria_contas.py` | CSV ou modo interativo das suas contas → relatório do que migrar primeiro |
| `eval/` | seu eval pessoal: `tarefas/NN-nome/{tarefa.md,contexto/,criterio.md}` + 3 exemplos |
| `eval/rodar.py` | gera o pacote para colar no Claude Code/Codex/chat que você assina, ou roda no Ollama local (`--ollama`). Nunca chama API paga |
| `eval/placar.py` | registra a nota por modelo e data e desenha a evolução (SVG; PNG se houver matplotlib) |
| `plano/plano-90-dias.md` | ownership, distribuição, mundo físico, identidade, crenças, pessoas — com exercícios |

## Começar

```bash
git clone https://github.com/inematds/sobreviver-ia && cd sobreviver-ia

python3 kit/calcula_kit.py --pessoas 2 --dias 14 --gasto-mensal 4500
bash offline/instala-offline.sh --modelo llama3.2:3b --wiki pt --tipo nopic     # dry-run
python3 seguranca/auditoria_contas.py --modelo contas.csv
python3 eval/rodar.py --modelo meu-modelo        # ou: --ollama qwen2.5:7b
python3 eval/placar.py grafico
python3 -m pytest -q                              # testes
```

Windows: veja a seção "Instale a IA e a Wikipedia offline" no [guia](https://inematds.github.io/sobreviver-ia/guia/#guia).

## Licença

MIT — veja [LICENSE](LICENSE). Versão 1.0.0. Parte do ecossistema [INEMA.CLUB](https://inema.club).
