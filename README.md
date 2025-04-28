# Stellar Final - Atomic Swap Smart Contract

## Proje Hakkında
Bu proje, **Soroban SDK** kullanılarak geliştirilmiş bir **Atomic Swap** akıllı kontratıdır. Amacı, iki kullanıcının birbirlerine güven duymadan farklı tokenları adil şekilde takas etmesini sağlamaktır. Ekstra olarak **freeze (dondurma)** ve **unfreeze (açılma)** işlevleri de eklenmiştir.

Kontrat başarıyla **Stellar Testnet** üzerine deploy edilmiştir.

## Özellikler
- **Atomic Swap:**
  - İki taraf token değişimini karşlılıklı ve güvenli bir şekilde yapar.
  - Her iki taraf da minimum kabul edilebilir miktarlar belirleyebilir.

- **Freeze Hesap:**
  - Admin, bir kullanıcı hesabını dondurabilir.
  - Dondurulan hesaplar token gönderemez veya alamaz.

- **Unfreeze Hesap:**
  - Admin, dondurulan hesapları açabilir.
  - Açılan hesaplar normal şekilde işlem yapabilir.

- **Admin Yetkilendirmesi:**
  - Sadece Admin kullanıcı freeze ve unfreeze işlemlerini yapabilir.

## Kontrat Adresi
`CD2TWKKSUS6BURDOUWNHSFEZXBKQALV5V7ENBRJEQ4GLCSNWYTHINTZC`

(Stellar **Testnet** üzerinde yayında)

## Nasıl Çalışır?
1. İki taraf takas için anlaşır.
2. Her iki taraf da özel şartları (minimum miktarlar gibi) onaylar.
3. Tokenlar, önce kontrat hesabına transfer edilir.
4. Ardından belirtilen şartlara uygun şekilde karşı taraflara dağıtılır.
5. Eğer hesap donmuşsa, swap işlemi iptal edilir.
6. Freeze ve unfreeze yetkisi yalnızca admin kullanıcıdadır.

## Kullanılan Teknolojiler
- **Rust** Programlama Dili
- **Soroban SDK**
- **Stellar Testnet**

## Notlar
- Swap işlemleri tamamen atomiktir; ya tamamen gerçekleşir ya da iptal olur.
- Freeze sistemi sayesinde şüpheli aktiviteler kolayca durdurulabilir.
- Tüm işlemler yetkilendirme (authentication) mekanizması ile korunur.

---

Bu proje, **Stellar Fullstack Bootcamp** kapsamında gelistirilmistir. 🚀

