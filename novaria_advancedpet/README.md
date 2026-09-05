# Novaria - Premium Pet Sistemi v3.0 (AMX Mod X)

## 🇰🇷 한국어

안녕하세요, 사랑하는 한국 친구들! 💚
한국의 모든 게이머와 커뮤니티 여러분께 진심 어린 사랑과 존경의 인사를 전합니다. 🇰🇷❤️

### 플러그인 소개
**Novaria Premium Pet Sistemi**, Counter-Strike 1.6 (AMX Mod X / ReAPI) 서버를 위한 애완동물(Pet) 시스템입니다. 플레이어는 서버 내 화폐(모드에 따라 CS 현금, Ammo Pack, Coin 등)를 사용하여 자신을 따라다니는 펫을 구매하고, 여러 마리를 소유하며 원하는 펫으로 전환할 수 있습니다. 설정은 nVault에 저장되어 재접속 시에도 유지됩니다.

### 주요 기능
- `/pet` 또는 `/pets` 명령어로 메뉴 열기
- 펫 구매, 소유한 펫 목록 보기 및 활성 펫 전환
- 관리자 패널: 특정 플레이어에게 펫 지급 / 회수 / 데이터 초기화
- 여러 게임 모드 지원 (아래 참고), 화폐 시스템 자동 연동
- 펫은 플레이어를 따라다니며 점프, 순찰(idle), 달리기, 사망 애니메이션을 재생
- 거리에 따라 순간이동(텔레포트) 및 속도 조절 로직 포함
- 리스폰 시 및 라운드 시작 시 자동으로 활성 펫 재생성
- PRE_Pets.ini 설정 파일을 통해 관리자가 원하는 만큼 펫 모델 추가 가능
- 다국어 지원: 영어(EN), 터키어(TR), 한국어(KO)

### 지원되는 게임 모드 (ACTIVE_MOD)
| 값 | 모드 | 화폐 시스템 |
|----|------|------------|
| 1 | PRO_PUBLIC | CS 현금 (money) |
| 2 | ZOMBIE_PLAGUE | Ammo Pack |
| 3 | JAILBREAK | Coin |
| 4 | BIOHAZARD | BioPoint |

> ⚠️ 소스 코드 상단의 `#define ACTIVE_MOD ZOMBIE_PLAGUE` 줄을 서버에서 사용 중인 모드에 맞게 수정한 후 컴파일해야 합니다.

### 설치 방법
1. `addons/amxmodx/scripting/novaria_advancedpet.sma` 및 컴파일된 `.amxx` 파일을 서버에 업로드하세요.
2. `addons/amxmodx/data/lang/PRE_Petsv3.txt` 언어 파일을 업로드하세요.
3. `addons/amxmodx/configs/PRE_Pets.ini` 파일에 원하는 펫 목록을 정의하세요 (파일이 없으면 플러그인이 예시 파일을 자동 생성합니다).
4. `plugins.ini` 파일에 플러그인을 추가하세요.
5. 서버를 재시작하거나 플러그인을 다시 로드하세요.

---

## 🇹🇷 Türkçe

### Eklenti Hakkında
**Novaria Premium Pet Sistemi**, Counter-Strike 1.6 (AMX Mod X / ReAPI) sunucuları için geliştirilmiş, oyunculara kendilerini takip eden bir "pet" (evcil hayvan) sahibi olma imkanı tanıyan bir eklentidir. Oyuncular sunucu para birimiyle (moda göre CS parası, Ammo Pack veya Coin) pet satın alabilir, birden fazla pete sahip olabilir ve aralarında geçiş yapabilir. Veriler nVault ile kalıcı olarak saklanır.

### Özellikler
- `/pet` veya `/pets` yazarak menüyü açma
- **Pet Satın Al** menüsü: `PRE_Pets.ini` dosyasında tanımlı petleri fiyatlarıyla listeler
- **Petlerim** menüsü: sahip olunan petler arasından aktif peti seçme
- **Admin Paneli** (sadece `ADMIN_RCON` yetkisine sahip oyunculara görünür):
  - Bir oyuncuya pet hediye etme
  - Bir oyuncudan pet geri alma
  - Oyuncunun pet verilerini sıfırlama
- Pet, sahibini otomatik olarak takip eder; mesafeye göre koşma/yürüme animasyonu oynatır, çok uzaklaşılırsa ışınlanarak (teleport) sahibine yaklaşır
- Zıplama (jump), boşta bekleme (idle) ve ölüm (death) animasyonları desteklenir, uçan (fly) hareket tipi de mevcuttur
- `pet_is_spawn` cvar'ı ile pet davranışı ayarlanır:
  - `0` → Oyuncu öldüğünde ve raund bittiğinde pet kaybolur
  - `1` → Aynı, fakat oyuncu respawn olunca pet geri gelir
  - `2` → Deathmatch (DM) sunucuları için özel davranış
- `MENU_IMMUNITY` ayarı ile menünün sadece adminlere mi yoksa herkese mi açık olacağı belirlenebilir
- Ayarlanabilir cvar'lar: maksimum zıplama yüksekliği, takip mesafesi, ışınlanma mesafesi, maksimum hız, spawn yarıçapı
- Çoklu dil desteği: İngilizce (EN), Türkçe (TR), Korece (KO) — oyuncunun oyun diline göre otomatik değişir
- Kaynak kodu, ticari amaçla satılamayacak şekilde ücretsiz olarak paylaşılmıştır (bkz. dosya başındaki lisans notu)

### Desteklenen Modlar (ACTIVE_MOD)
| Değer | Mod | Para Birimi |
|-------|-----|-------------|
| 1 | PRO_PUBLIC | CS Parası (money) |
| 2 | ZOMBIE_PLAGUE | Ammo Pack |
| 3 | JAILBREAK | Coin |
| 4 | BIOHAZARD | BioPoint |

> ⚠️ Eklentiyi derlemeden önce dosyanın başındaki `#define ACTIVE_MOD ZOMBIE_PLAGUE` satırını kendi sunucunuzda kullandığınız moda göre değiştirmeniz gerekir.

### Cvar Listesi
- `pets_max_jump_height` (varsayılan: 350.0) — Petin maksimum zıplama yüksekliği
- `pets_follow_distantion` (varsayılan: 100.0) — Petin takip etmeye başlayacağı mesafe
- `pets_telep_distantion` (varsayılan: 1250.0) — Petin oyuncuya ışınlanacağı mesafe
- `pets_max_speed` (varsayılan: 370.0) — Petin oyuncuya ulaşma hızı
- `pets_max_radius_spawn` (varsayılan: 200.0) — Petin spawn olacağı maksimum yarıçap
- `pet_is_spawn` (varsayılan: 1) — Yukarıda açıklanan spawn davranışı modu

### Kurulum
1. `addons/amxmodx/scripting/novaria_advancedpet.sma` dosyasını, `ACTIVE_MOD` değerini kendi modunuza göre düzenleyip derleyin ve oluşan `.amxx` dosyasını sunucuya yükleyin.
2. `addons/amxmodx/data/lang/PRE_Petsv3.txt` dil dosyasını yükleyin.
3. `addons/amxmodx/configs/PRE_Pets.ini` dosyasına pet listenizi tanımlayın (isim, model yolu, yetki bayrağı, animasyon sıraları, hareket tipi ve fiyat). Dosya yoksa eklenti ilk açılışta örnek bir şablon oluşturur.
4. `plugins.ini` dosyasına eklentiyi ekleyin.
5. Sunucuyu yeniden başlatın veya eklentiyi reload edin.

### Ekran Görüntüsü

![Pet Sistemi Menüsü](screenshots/screenshot.png)

---

## 🇬🇧 English

### About the Plugin
**Novaria Premium Pet System** is a companion-pet plugin for Counter-Strike 1.6 (AMX Mod X / ReAPI) servers. Players spend the server's in-game currency (CS money, Ammo Packs, or Coins, depending on the active mod) to buy pets, own multiple pets, and switch between them. Progress is saved through nVault and restored automatically on reconnect.

### Features
- Opens with `/pet` or `/pets`
- **Buy a Pet** menu listing all pets defined in `PRE_Pets.ini` with their prices
- **My Pets** menu to switch the currently active pet among owned ones
- **Admin Panel** (visible only to players with `ADMIN_RCON`):
  - Give a pet to a player
  - Take a pet away from a player
  - Reset a player's pet data
- Pets automatically follow their owner, animate run/idle based on distance, and teleport back if they fall too far behind
- Supports jump, idle, run, death, and flying movement animations per pet
- `pet_is_spawn` cvar controls respawn behavior (persist after death, disappear at round end, or DM-specific mode)
- `MENU_IMMUNITY` setting restricts the menu to admins only, or opens it to everyone
- Configurable cvars for jump height, follow distance, teleport distance, max speed, and spawn radius
- Multi-language support: English (EN), Turkish (TR), Korean (KO) — automatically switches based on each player's game language
- Free for community use; may not be resold or claimed as someone else's own product

### Installation
1. Set `ACTIVE_MOD` at the top of the source to match your server's mod, compile it, and upload `novaria_advancedpet.amxx` to your server.
2. Upload the `PRE_Petsv3.txt` language file.
3. Define your pet list in `PRE_Pets.ini` (name, model path, access flag, animation sequences, movement type, price). If the file doesn't exist, the plugin auto-generates a template on first load.
4. Add the plugin to `plugins.ini`.
5. Restart the server or reload the plugin.

---

*Made with ❤️ by Novaria*
