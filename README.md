# CloudCase — Como o Claude construiu o modelo do Consignado

Apresentação interativa em HTML (offline, arquivo único) que mostra, com
trechos verbatim das sessões reais do Claude Code, como o projeto
Consignado (modelo de risco de perda de emprego com RAIS/Novo CAGED) foi
construído do zero — do download dos dados públicos ao treino em GPU e à
apresentação para a diretoria.

## Arquivos

| Arquivo | Papel |
|---|---|
| `extrair_trechos.py` | Minera os transcripts `.jsonl` das sessões do Claude Code e gera `dados_apresentacao.json` (trechos verbatim + estatísticas reais) |
| `dados_apresentacao.json` | Dados extraídos (momentos, sessões, números) |
| `gerar_apresentacao_claude.py` | Gera `apresentacao_claude_consignado.html` a partir do JSON, com figuras reais do projeto embutidas em base64 |
| `apresentacao_claude_consignado.html` | A apresentação — 15 slides, autossuficiente, sem dependências |
| `fonts_dejavu.css` | Fonte DejaVu Sans embutida (base64), mesma do deck original |

## Como regenerar

```bash
python3 extrair_trechos.py        # lê ~/.claude/projects/<projeto>/*.jsonl
python3 gerar_apresentacao_claude.py
```

Abra o HTML no navegador.

## Navegação e recursos

- Botões à direita, setas do teclado, espaço, PgUp/PgDn, Home/End
- **Revelação progressiva**: nos slides de conversa, cada avanço revela a
  próxima bolha (com efeito "digitando…")
- **F** alterna tela cheia; pontinhos no rodapé pulam direto para um slide
- Barra de progresso laranja no rodapé; transição suave entre slides
- Timeline clicável (sessões reais), heatmap de atividade dia × hora,
  gráfico de mensagens por sessão e output real de comando no slide de
  anatomia — tudo com dados medidos dos transcripts
- `Ctrl+P` imprime um slide por página (exportável em PDF)

Gerado com Claude Code a partir do histórico real das sessões.
