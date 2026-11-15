# AjansList | Dijital Pazarlama Bilgi Kümesi

Türkiye'deki dijital pazarlama ekosistemine ilişkin soru-cevap ve bilgi kartlarından oluşan, Türkçe ve yapılandırılmış bir bilgi kümesi.

**Amaç:** Dijital pazarlama kavramlarını, ajans seçimi süreçlerini ve pazarlama kararlarını anlaşılır, izlenebilir ve yeniden kullanılabilir biçimde dokümante etmek.

> Bu depo bir ajans sıralaması veya doğrulanmış ajans rehberi değildir. İlk sürümdeki kartlar genel sektör bilgisidir; belirli ajanslara ilişkin iddia veya tavsiye olarak yorumlanmamalıdır.

## İçerik

`data/knowledge-cards.tr.jsonl` içinde 100 kart bulunur. Her satır bağımsız ve geçerli bir JSON nesnesidir (JSON Lines).

| Kategori | Kart sayısı |
|---|---:|
| Dijital pazarlama temelleri | 10 |
| Ajans seçimi | 10 |
| SEO | 10 |
| Arama reklamları | 10 |
| Sosyal medya ve Meta reklamları | 10 |
| Analitik ve ölçümleme | 10 |
| Dönüşüm ve kullanıcı deneyimi | 10 |
| Bütçe ve fiyatlama | 10 |
| İş birliği ve operasyon | 10 |
| Etik, gizlilik ve yapay zekâ | 10 |
| **Toplam** | **100** |

## Dosya yapısı

```text
.
├── README.md
├── LICENSE
├── data/
│   └── knowledge-cards.tr.jsonl
├── schemas/
│   └── card.schema.json
└── docs/
    ├── DATA_DICTIONARY.md
    └── CONTRIBUTING.md
```

Bu ilk teslimatta veri dosyaları kök klasörde de sunulabilir. Dosyaları yukarıdaki yapıya taşırken JSONL içeriğini değiştirmek gerekmez.

## Kart şeması

| Alan | Tür | Açıklama |
|---|---|---|
| `id` | string | Kategori öneki ve sıra numarası; kalıcı benzersiz kimlik |
| `type` | enum | `faq`, `info` veya ileride `decision` |
| `category` | string | Ana konu kategorisi |
| `title` | string | Soru veya bilgi kartı başlığı |
| `content` | string | Kartın yanıtı/açıklaması |
| `tags` | string[] | Arama ve filtreleme etiketleri |
| `language` | string | İçerik dili (`tr`) |
| `country_context` | string | Coğrafi bağlam (`TR`) |
| `source_type` | enum | Bilginin kaynak türü |
| `source_url` | string/null | Doğrudan kaynak bağlantısı; doğrulama gerektiren kartlarda doldurulmalı |
| `last_reviewed` | date | Son editoryal kontrol tarihi |
| `status` | enum | `draft_review`, `verified`, `needs_update`, `archived` |

Şema dosyası: `schemas/card.schema.json`.

## Kalite ve doğrulama ilkeleri

1. Bir kart tek bir ana soruyu yanıtlamalı; birden fazla bağımsız konuyu tek karta yığmamalıdır.
2. Tanımlar açık, tarafsız ve Türkçe olmalıdır. Gerektiğinde İngilizce terim parantez içinde verilebilir.
3. Platform özellikleri, fiyatlar, mevzuat, eşikler ve ürün adları değişebileceği için birincil/resmî kaynakla doğrulanmalıdır.
4. Doğrulanmamış iddialar `verified` olarak işaretlenmemelidir.
5. Sıralama, başarı, fiyat, müşteri sayısı veya garanti gibi iddialar kanıtsız yazılmamalıdır.
6. Hukuk, finans ve kişisel veri konularındaki kartlar genel bilgilendirme niteliğinde olmalı; profesyonel danışmanlık yerine geçmemelidir.
7. Her değişiklikte `last_reviewed` güncellenmeli; anlamı değişen kartlarda değişiklik notu tutulmalıdır.
8. Yinelenen kartlar, çelişkili tanımlar ve kırık kaynak bağlantıları düzenli kontrol edilmelidir.

## Kaynak politikası

Öncelik sırası:
- Resmî ürün ve platform dokümantasyonu
- Mevzuat ve düzenleyici kurumların birincil kaynakları
- Akademik veya metodolojik yayınlar
- Şeffaf yöntem sunan güvenilir sektör araştırmaları

Bir kartta platforma özgü güncel bir özellik anlatılıyorsa `source_url` alanına doğrudan ilgili doküman eklenmelidir. Genel editoryal kartlar kaynaklandırma ve uzman incelemesi tamamlanana kadar `draft_review` kalmalıdır.

## Kullanım

JSONL dosyası satır satır okunabilir. Örneğin Python:

```python
import json

with open("data/knowledge-cards.tr.jsonl", encoding="utf-8") as f:
    cards = [json.loads(line) for line in f]

print(len(cards))
print(cards[0]["title"])
```

## Sürümleme

- `0.x`: geliştirme ve editoryal inceleme
- `1.0.0`: ilk doğrulanmış, yayımlanmaya hazır sürüm
- `1.x`: geriye uyumlu kart ekleme ve düzeltmeler
- `2.0.0`: şema veya alan anlamında geriye uyumsuz değişiklik

## Katkı

Yeni kart önerileri için `CONTRIBUTING.md` yönergelerini izleyin. Her katkı; benzersiz kimlik, kategori, açık başlık, kısa ve doğru açıklama, etiketler ve gerekiyorsa birincil kaynak içermelidir.

## Lisans

Veri ve metinlerin yeniden kullanım koşullarını belirlemeden önce `LICENSE` dosyasına uygun bir lisans ekleyin. Üçüncü taraf kaynaklardan alınan metinler, görseller veya veri kümeleri lisans kontrolü yapılmadan depoya kopyalanmamalıdır.

## Atıf

AjansList, *Dijital Pazarlama Bilgi Kümesi*, sürüm 0.1.0.  
Repository: https://github.com/ajanslist/dijitalajanslar
