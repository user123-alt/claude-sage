# Claude Code - Optimal İş Akışı Rehberi

## 🎯 Ana Prensip

**"Analyze First, Fix Later"**

Hızlı fix yerine doğru fix. Kod değiştirmeden önce tam anla.

---

## 🔄 Standard Problem-Solving Workflow

### 1️⃣ Analiz Aşaması (ASLA ATLANMAZ)

```bash
/analyze
```

**Ne olur:**
- problem-analyst çağrılır
- Sadece okuma yetkisi var (Write/Edit yok)
- Detaylı root cause analysis
- Impact değerlendirmesi
- Öneri listesi

**Çıktı:**
- Detaylı analiz raporu
- Basit mi / Kritik mi / Belirsiz mi?
- Sonraki adım önerisi

### 2️⃣ Karar Aşaması

**Eğer Basit Fix İse:**
```
Sen: "Tamam, fix'i uygula"
→ controlled-fixer çağrılır
```

**Eğer Kritik / Mimari İse:**
```bash
/architect
```
- solution-architect çağrılır
- Ultrathink modu aktif
- 3+ alternatif yaklaşım
- Trade-off analizi
- Sen karar verirsin

**Eğer Belirsiz / Takılı Kalındıysa:**
```bash
/explore
```
- horizon-explorer çağrılır
- Alternatif perspektifler
- Farklı teknolojiler araştırılır
- "Doğru yere bakıyor muyuz?" sorusu

### 3️⃣ Uygulama Aşaması (Senin Onayınla)

```bash
/fix
```

**Pre-conditions:**
- [ ] Analiz yapıldı
- [ ] Plan yapıldı (kritikse)
- [ ] Sen onayladın

**Ne olur:**
- controlled-fixer çağrılır
- Test-driven değişiklik
- Küçük, atomic commits
- Rollback planı hazır

---

## 🚨 Kritik Durumlar

### Cron Jobs / Pipeline Jobs

**Yaklaşım:**
1. `/analyze` → problem-analyst detaylı analiz yapsın
2. Job logs, schedule, dependencies analiz et
3. Eğer timing/concurrency issue varsa:
   ```bash
   /architect
   ```
4. Ultrathink ile:
   - Race condition analizi
   - Retry logic
   - Idempotency check
   - Monitoring stratejisi

### Mimari Değişiklik Gerektiren Sorunlar

**Yaklaşım:**
1. `/analyze` → Sorun tespit edilir
2. `/architect` → 3 alternatif plan
3. `/explore` → Başka sistemler nasıl yapmış? (isteğe bağlı)
4. Sen karar verirsin
5. `/fix` → Dikkatli implementation

### "Saatlerce Uğraşıyoruz Ama Çözemedik"

**Yaklaşım:**
1. `/explore` → Horizon explorer çağır
   - "Doğru yere bakıyor muyuz?"
   - Alternative approaches
   - Cross-domain solutions
2. Yeni perspektifle `/analyze` tekrar
3. `/architect` ile yeni plan

---

## 🤝 Agent'lar Arası İşbirliği

### Workflow 1: Standard Debug

```
problem-analyst
    ↓ (basitse)
controlled-fixer
```

### Workflow 2: Kritik Değişiklik

```
problem-analyst
    ↓
solution-architect (ultrathink)
    ↓
controlled-fixer
```

### Workflow 3: Belirsiz Sorun

```
problem-analyst
    ↓ (belirsiz)
horizon-explorer
    ↓ (yeni perspektif)
problem-analyst (tekrar)
    ↓
solution-architect
    ↓
controlled-fixer
```

### Workflow 4: Tam Araştırma

```
problem-analyst ┐
                ├→ solution-architect
horizon-explorer┘       ↓
                  controlled-fixer
```

---

## 📋 Hızlı Komutlar

| Komut | Agent | Ne Yapar | Kod Değiştirir mi? |
|-------|-------|----------|-------------------|
| `/analyze` | problem-analyst | Detaylı analiz ve rapor | ❌ Hayır |
| `/architect` | solution-architect | Stratejik plan (ultrathink) | ❌ Hayır |
| `/explore` | horizon-explorer | Alternatif yaklaşımlar | ❌ Hayır |
| `/fix` | controlled-fixer | Dikkatli implementation | ✅ Evet (onaylıysa) |

---

## ⚙️ Settings Özeti

**Mevcut Yapılandırma:**
```json
{
  "model": "sonnet",
  "alwaysThinkingEnabled": true,
  "permissions": {
    "defaultMode": "default",
    "allow": ["Bash(git:*)", "Bash(npm:*)", ...],
    "deny": ["Bash(rm:-rf:*)", ...]
  },
  "env": {
    "MAX_THINKING_TOKENS": "31999"
  }
}
```

**MCP Servers:**
- ✅ context7 (library documentation)
- ✅ exa web search (bleeding edge research)
- ✅ exa code context (code/API examples)
- ✅ deepseek (R1 model) - Optional: https://github.com/arikusi/deepseek-mcp-server

---

## 🎓 Best Practices

### DO ✅

1. **Her zaman /analyze ile başla**
2. **Kritik değişiklikler için /architect kullan**
3. **Takıldığında /explore ile perspektif değiştir**
4. **Onay vermeden /fix yapma**
5. **Ultrathink iste kritik kararlarda**

### DON'T ❌

1. **Hızlı fix isteme** → Quick fix = technical debt
2. **Analiz atlama** → Anlamamadan değiştirme
3. **Tek perspektifle takılı kalma** → horizon-explorer kullan
4. **Test olmadan prod'a değişiklik**
5. **Breaking change warning'siz değiştirme**

---

## 💡 Pro Tips

### Tip 1: Proaktif Mimari Review
Büyük feature başlamadan önce:
```bash
/architect
# "X özelliğini eklemek için en iyi yaklaşım nedir?"
```

### Tip 2: Alternative Research
Yeni teknoloji/pattern araştırırken:
```bash
/explore
# "Y problemi için modern best practices neler?"
```

### Tip 3: Postmortem Analysis
Bug çözüldükten sonra:
```bash
/analyze
# "Bu bug nasıl oluştu, tekrar oluşmasını nasıl önleriz?"
```

### Tip 4: Code Review Öncesi
PR göndermeden önce:
```bash
/architect
# "Bu değişikliğin uzun vadeli etkileri neler?"
```

---

## 🔮 Gelecek İyileştirmeler (İsteğe Bağlı)

### Eklenebilir Agent'lar:

1. **performance-profiler**: Sadece performance analizi
2. **security-auditor**: Security vulnerability scan
3. **doc-generator**: Documentation oluşturma
4. **test-writer**: Test case generation
5. **refactor-planner**: Refactoring stratejisi

### Eklenebilir Hooks:

```json
{
  "PostToolUse": [
    {
      "matcher": "Edit|Write",
      "hooks": [
        {"type": "command", "command": "prettier --write $FILE"},
        {"type": "command", "command": "eslint --fix $FILE"}
      ]
    }
  ],
  "PreToolUse": [
    {
      "matcher": "Bash(rm:*)",
      "hooks": [
        {"type": "command", "command": "echo 'DANGER: rm komutu!'", "exit": 2}
      ]
    }
  ]
}
```

---

## 📞 Yardım

- Agent çalışmıyor mu? → `ls ~/.claude/agents/`
- Komut bulunamıyor mu? → `ls ~/.claude/commands/`
- Settings bozuldu mu? → `cat ~/.claude/settings.json`

**Agent Test:**
```bash
# Ana conversation'da:
"problem-analyst agent'ını çağır ve X sorunu analiz et"
```

---

**Son Güncelleme:** 2026-01-17
**Agent Versiyon:** 2.0 (mature workflow)
