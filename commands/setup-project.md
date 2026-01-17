---
description: Yeni proje için Claude yapılandırması oluştur
---

Şu anki dizinde yeni bir proje için Claude Code yapılandırması oluştur:

1. `.claude/` dizini oluştur
2. `.claude/CLAUDE.md` ile proje kurallarını yaz:
   - Teknoloji stack'i
   - Code style kuralları
   - Önemli dizin yapısı
   - Proje-spesifik talimatlar

3. `.claude/settings.json` oluştur:
   - Model tercihi
   - İzinler
   - Hooks

4. `.mcp.json` oluştur (varsa proje-spesifik MCP'ler için)

5. `.gitignore`'a ekle:
   ```
   .claude/settings.local.json
   .claude/*.lock
   ```

Mevcut proje yapısını analiz et ve önerilerde bulun.
