# PRD — artirdim.com (Laravel 12 + Inertia + Vue 3 Canlı Müzayede Platformu)

## Problem / Bağlam
GitHub public repo (https://github.com/xprlyzed/projectv1) üzerinde geliştirilmekte olan,
canlı yayınlı (LiveKit/WebRTC SFU) açık artırma/müzayede platformu. Satıcılar canlı yayın açar,
alıcılar izler + gerçek zamanlı sohbet + teklif verir. TikTok/Kick tarzı mobil tam ekran deneyim mevcut.

## Teknoloji
- Backend: Laravel 12 (PHP 8.2), MySQL/MariaDB, Redis (cache), queue (database)
- Frontend: Inertia.js + Vue 3 (Composition API), Vite build, Ziggy, Metronic (Bootstrap) teması
- Canlı yayın: LiveKit (Cloud) — token: POST /livekit/token; chat: polling
- Servis (preview): php-fpm 8.2 + nginx (port 3000), supervisor: laravel-fpm/nginx/scheduler/queue + mariadb/redis

## Kullanıcı Rolleri
- Admin (admin@test.com), Satıcı (seller@test.com), Alıcı (buyer@test.com) — şifre: password

## Yapılanlar (tarih sırası)
- (Önceki oturumlar) Blade→Inertia/Vue dönüşümü, canlı yayın (LiveKit) + chat + teklif, sipariş/ödeme (demo bakiye),
  hikayeler (story), mobil TikTok tarzı MobileLiveRoom.vue.
- 2026-09-03: G1 yanlış "yayın başlatılmadı" mesajı fix, G2 freeze fix, G3 mobil oda renkler/yeniden giriş/masaüstü gizleme.
- 2026-09-04 (bu oturum):
  - Proje GitHub'dan bu ortama sıfırdan kuruldu (PHP 8.2 + MariaDB + Redis + nginx, migrate + seed, vite build). Site HTTP 200.
  - LiveKit .env bilgileri eklendi (url/key/secret).
  - **Bölüm 5 — Masaüstü tam ekran canlı yayın: DesktopLiveRoom.vue eklendi**, Show.vue'ya simetrik entegre.
    testing_agent iteration_3: 7/7 PASS, 0 console hatası, mobil regresyon temiz. MobileLiveRoom.vue değiştirilmedi.
  - Preview'da Laravel Debugbar kapatıldı (mobil input'u kapatan overlay giderildi).

## Backlog / Sonraki
- P1: Bağlantı kalite göstergesi (sinyal barı — İyi/Orta/Zayıf) [önceki G5].
- P1: Yayıncı tek-tık başlat / izleyici otomatik bağlan sadeleştirme [önceki G6].
- P2: DesktopLiveRoom/MobileLiveRoom izleyici sayısı ile sayfa rozeti arasındaki -1 tutarsızlığı.
- P2: Show.vue isMobile için resize/orientationchange listener (şu an mount'ta tek-sefer).
- Prod: gerçek ödeme sağlayıcı (İyzico/PayTR/Stripe) — şu an bakiye DEMO. Reverb (anlık chat) opsiyonel.

## Notlar
- PUSH HEDEFİ SADECE: https://github.com/xprlyzed/projectv1 (process.md SABİT KURAL). Push kullanıcı "push et" deyince, "Save to Github" ile.
- Preview ortamı Laravel'i kalıcı barındırmaz (pod restart'ta PHP/DB sıfırlanır) — .emergent/system_deps.txt ile yeniden kurulur.
