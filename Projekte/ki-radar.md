# KI-Radar – Projekt

## Status
✅ Fertig gebaut (2026-05-31)

## Was wurde gebaut
1. **n8n-Workflow JSON** → `~/Desktop/AI/Claude/ki-radar-n8n-workflow.json`
2. **Notion-Doku** → https://www.notion.so/37135d19172d8121b388d59dcd0eba72

## Was der Workflow macht
- Jeden Sonntag 09:00 CET
- Holt RSS (Simon Willison, Anthropic Community, HuggingFace Blog)
- Holt Arena LLM + Arena Code Leaderboards (JSON API)
- Claude Sonnet 4 analysiert und rankt nach: Architektur / Algorithmik / Datenextraktion
- Ergebnis → Notion-DB + Telegram

## Verifizierte Datenquellen (Mai 2026)
- Simon Willison: https://simonwillison.net/atom/entries/
- Anthropic (Community): https://raw.githubusercontent.com/taobojlen/anthropic-rss-feed/main/anthropic_news_rss.xml
- HuggingFace: https://huggingface.co/blog/feed.xml
- Arena LLM API: https://api.wulong.dev/arena-ai-leaderboards/v1/leaderboard?name=text
- Arena Code API: https://api.wulong.dev/arena-ai-leaderboards/v1/leaderboard?name=code

## Wichtige Entscheidungen
- Code-Architekt = Aider --chat-mode architect + Claude (Architekt) + gratis OpenRouter-Modell (Editor)
- Kein offizieller Anthropic RSS → Community-Feed von taobojlen/anthropic-rss-feed
- Anthropic-Node Bug (#26300): Workaround via HTTP Request Node ist in Notion-Doku beschrieben
- Halluzinierte Tools von DeepSeek nicht verwenden (in Notion-Doku gelistet)

## Setup noch offen (Rémy muss das selbst machen)
1. Anthropic Credentials in n8n
2. Telegram Bot + Chat-ID als TELEGRAM_CHAT_ID env var
3. Notion DB anlegen + ID in Workflow eintragen
4. Workflow manuell testen, dann aktivieren

## Code-Architekt Aider-Befehl
```bash
aider --chat-mode architect \
  --model anthropic/claude-sonnet-4-20250514 \
  --editor-model openrouter/qwen/qwen3-coder:free
```
