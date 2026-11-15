# Veri Sözlüğü

- `id`: Kartın değişmeyen kimliği.
- `type`: `faq` soru-cevap, `info` bilgi kartı, `decision` karar desteği kartı.
- `category`: Kartın ait olduğu ana konu.
- `title`: Kullanıcı sorusu veya kart başlığı.
- `content`: Açıklama/yanıt metni.
- `tags`: Konu araması ve filtreleme için etiketler.
- `language`: İçerik dili.
- `country_context`: İçeriğin coğrafi bağlamı.
- `source_type`: Bilginin kaynağının niteliği.
- `source_url`: Doğrudan doğrulama kaynağı; yoksa `null`.
- `last_reviewed`: ISO 8601 tarih biçiminde son inceleme tarihi.
- `status`: Editoryal doğrulama durumu.

`draft_review`, içeriğin otomatik olarak yanlış olduğu anlamına gelmez; yayımdan önce editoryal ve kaynak kontrolü gerektiğini belirtir.
