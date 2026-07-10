# bupa-updates

BUPA scriptleri için **merkezi güncelleme + haber hub'ı**. Tüm scriptler
sürüm ve reklam bilgisini bu repodan çeker. **Public** olmalı.

## Yapı

```
bupa-updates/
├── news.txt            # tüm scriptlerde gösterilen ortak reklam metni
├── bupa-animpos.json   # bupa-animpos sürüm + changelog + indirme linki
└── (yeni script)       # her yeni script için bir .json ekle: bupa-garage.json ...
```

## Script sürüm dosyası formatı (`<script-adi>.json`)

```json
{
  "version": "1.5.0",
  "download": "https://portal.cfx.re/assets/granted-assets?search=bupa-animpos",
  "changelog": [
    "Ilk satir",
    "Ikinci satir"
  ]
}
```

| Alan | Açıklama |
| --- | --- |
| `version` | Scriptin en son sürümü. Scriptin `fxmanifest.lua` `version`'ından yüksekse müşteri "UPDATE AVAILABLE" görür. |
| `download` | Konsolda gösterilen indirme linki (Cfx.re portal / Tebex). |
| `changelog` | "What's new" altında satır satır listelenir (dizi). |

## Yeni sürüm çıkarınca

1. İlgili scriptin `fxmanifest.lua` `version`'ını yükselt (örn. `1.6.0`).
2. Buradaki `<script>.json` içindeki `version`'ı aynı sayıya çek, `changelog`'u güncelle.
3. `git push`. Eski sürümü çalıştıran tüm sunucular konsolda uyarıyı görür.

## Yeni script eklerken

Yeni scriptin `server.lua`'sındaki `UPDATES.Script` alanına dosya adını yaz
(örn. `bupa-garage`) ve bu repoya `bupa-garage.json` ekle. Hepsi aynı hub'dan beslenir.
