📋 DumpSight Platform — FINAL PROMPT v3.1 (PRODUCTION-READY)
1. PROJE TANIMI & VİZYON
DumpSight, kurumsal düzeyde çalışan, tüm .NET ekosistemini kapsayan, akıllı ve genişletilebilir bir dump analiz platformudur. Temel felsefesi "ZERO LOCK-IN, MAXIMUM FLEXIBILITY" — dump nereден gelirse gelsin, hangi yolla girerse girsin, aynı kalitede analiz ve rapor üretilir.

YAML
Uygulama Adı    : DumpSight
Versiyon        : v1.0.0
GitHub Repo     : esattunc/dumpsight
Ortam           : Air-gapped Kubernetes (RKE2)
Mimari          : Event-Driven Hybrid Microservice + Agent
Backend         : .NET 8 Minimal API / Worker Services
Frontend        : React 18 + TypeScript + Ant Design
Felsefe         : Zero Lock-in, Maximum Flexibility
2. PLATFORM & ALTYAPI
YAML
Kubernetes:
  Rancher Version : v2.11.1
  Provider        : RKE2
  K8s Version     : v1.32.3+rke2r1
  Architecture    : amd64
  Target Cluster  : test
  Internet        : YOK — Tam air-gapped

Cluster:
  Master Nodes    : 3
  Worker Nodes    : 6
  Total CPU       : 72 Cores
  Total RAM       : 281 GiB
  Node OS         : Linux only (amd64)

Storage (NFS):
  /dumps/incoming     → Tüm kaynaklardan gelen dump'lar
  /dumps/processing   → Aktif analiz geçici alan
  /dumps/archived     → Tamamlanan dump arşivi
  /dumps/compressed   → Sıkıştırılmış soğuk arşiv
  /dumps/watch        → NFS Drop Zone (otomatik izleme)
  /reports            → Üretilen raporlar
  /plugins            → Custom analyzer plugin'leri
  /audit-logs         → Audit log arşivi
  /agent-configs      → Agent konfigürasyonları
  /grafana-data       → Grafana persistent storage

Registry:
  Harbor  : https://cr-test.kuveytturk.com.tr/
  Nexus   : https://kttesthub/
  Helm    : Harbor OCI Registry
  TLS     : *.kuveytturk.com.tr wildcard
3. DUMP TOPLAMA — TÜM YOLLAR (ZERo LOCK-IN)
YAML
OTOMATİK YOLLAR:
  1. Linux Agent (K8s Sidecar/DaemonSet)
     → CPU/Memory threshold tetikleyici
     → Exception auto-capture (1st/2nd chance)
     → Process crash (last-chance)
     → Hang/deadlock tespiti
     → Scheduled (cron bazlı)

  2. Windows Agent (Windows Service)
     → IIS AppPool izleme
     → WMI process keşfi
     → ProcDump entegrasyonu
     → Tüm .NET 4.8/Framework triggerları

MANUEL YOLLAR:
  3. UI Upload         → Drag-drop, chunked (30GB+)
  4. UI Agent Tetik    → UI'dan agent'a "dump al" komutu
  5. NFS Watch Folder  → /dumps/watch'a bırak, otomatik alır
  6. WinRM/SSH Tetik   → Windows Server'a uzaktan komut

ENTEGRE YOLLAR:
  7. REST API          → POST /api/v1/dumps/upload
  8. CI/CD Pipeline    → Crash → API trigger → analiz
  9. Webhook Trigger   → Dış sistemden HTTP tetik

KAYNAK ETİKETİ (Her dump için):
  source: agent-auto | agent-manual | ui-upload |
          api | nfs-watch | ci-cd | winrm | scheduled

UNIFIED PIPELINE KURALI:
  Dump hangi yolla gelirse gelsin →
  Aynı pipeline → Aynı kalite analiz →
  Aynı rapor formatı → Aynı audit kaydı
4. ANA MİMARİ
YAML
Katmanlar:

  [DUMP KAYNAKLARI]
  Agent-Auto | UI-Upload | API | NFS-Watch | CI-CD
        │
        ▼
  [DUMP INTAKE SERVICE]
  Checksum doğrulama, metadata zenginleştirme,
  kaynak etiketleme, NFS yazma, Priority Queue'ya ekleme
        │
        ▼
  [RabbitMQ — Priority Queue 0-10]
  Durable, persistent, Dead Letter Exchange
        │
        ├──► [DETECTOR SERVICE]
        │    Magic byte, CLR version, dump tipi,
        │    platform, bitness, uygulama tipi tespiti
        │
        ├──► [ANALYZER ROUTER]
        │    ├─ Linux Analyzer  (.NET Core/5/6/7/8)
        │    │  ClrMD + dotnet-dump + LLDB+SOS
        │    └─ Windows VM Bridge (.NET 4.8/FX)
        │       Mevcut Windows Server → WinDbg + ClrMD
        │       (Linux başarısız → otomatik escalate)
        │
        ├──► [AI RULE ENGINE]
        │    Pattern matching, severity scoring,
        │    TR/EN plain-language özet, çözüm önerileri
        │
        ├──► [REPORT SERVICE]
        │    HTML / PDF / JSON üretimi
        │
        ├──► [DIFF ENGINE]
        │    İki dump karşılaştırma
        │
        ├──► [TREND SERVICE]
        │    Zaman serisi, anomali tespiti,
        │    haftalık rapor, proaktif uyarı
        │
        ├──► [PLAYBOOK SERVICE]
        │    Hazır + kullanıcı tanımlı analiz setleri
        │
        ├──► [NOTIFICATION SERVICE]
        │    Email/Teams/Slack/Webhook/SignalR
        │
        └──► [AUDIT SERVICE]
             Tüm eventler, oturum süreleri,
             per-user metrikler

  [AGENT MANAGER SERVICE]
  Agent kayıt, versiyon yönetimi,
  merkezi config, health monitoring

  [API GATEWAY]
  JWT+LDAP auth, rate limiting, routing,
  SignalR hub, Swagger/OpenAPI

  [REACT UI]
  Dashboard, Upload, Jobs, Analysis, Reports,
  Agents, Trends, Diff, Playbooks, Admin

  [PostgreSQL]
  Metadata, LDAP config, kullanıcılar,
  audit logları, trend verileri

  [Redis]
  JWT blacklist, session cache, real-time state

  [Prometheus + Grafana]
  Platform metrikleri, custom dashboardlar
5. ANALİZ ENGINE — B & C HİBRİT
YAML
Seçenek C — Linux Analyzer (Default):
  .NET Core, .NET 5/6/7/8 → TAM destek
  .NET Framework 4.8      → Best-effort (kısmi)
  Engine: ClrMD 3.x + dotnet-dump + LLDB+SOS
  Toggle: Helm values + UI'dan per-engine on/off

Seçenek B — Windows VM Bridge (Fallback):
  .NET Framework 2.0→4.8 → TAM destek
  ASP.NET IIS             → TAM destek
  Engine: WinDbg + ClrMD + ProcDump
  Tetik: runtime==net48 VEYA Linux analiz başarısız
  Bağlantı: Mevcut Windows Server REST API endpoint

Engine Toggle (Helm + UI):
  clrmd:      enabled: true   # Her zaman açık
  dotnetDump: enabled: true
  lldbSos:    enabled: true
  windbg:     enabled: true   # Windows VM varsa
  superDump:  enabled: false  # Opsiyonel
6. AGENT SİSTEMİ
YAML
Linux Agent:
  Teknoloji  : dotnet-monitor tabanlı, özelleştirilmiş
  Image      : cr-test.kuveytturk.com.tr/dumpsight/agent-linux
  Deployment : Sidecar (annotation inject) veya DaemonSet
  Annotation : dumpsight.io/inject: "true"
               dumpsight.io/project: "my-project"
               dumpsight.io/triggers: "cpu:85,mem:80,exc:true"

Windows Agent:
  Teknoloji  : Windows Service + ProcDump + WMI
  Paket      : MSI installer (offline kurulum)
  Image      : cr-test.kuveytturk.com.tr/dumpsight/agent-windows
  Kurulum    : Mevcut Windows Server'a MSI ile

Agent Workflow:
  1. Keşif    → Tüm .NET process tara, runtime tespit
  2. Kayıt    → DumpSight API'ye process envanteri gönder
  3. İzleme   → Trigger koşullarını sürekli kontrol
  4. Tetik    → Uygun dump tipini otomatik seç ve al
  5. Transfer → NFS'e yaz, checksum hesapla
  6. Bildirim → DumpSight API'ye zengin metadata POST

Dump Tipi Otoseçimi:
  Exception → Full Memory Dump
  CPU spike → MiniDump + Heap
  Memory    → Full Heap Dump
  Hang      → Full Memory Dump
  Scheduled → Configurable

Deployment Modları:
  MOD 1: K8s Sidecar    (annotation ile otomatik inject)
  MOD 2: K8s DaemonSet  (tüm node'lardaki process'ler)
  MOD 3: Windows Service (IIS + .NET Framework)
  MOD 4: Agentsiz       (sadece manuel upload/trigger)
7. ANALİZ MODÜLLERİ
YAML
Memory:
  heap-stat, LOH-analysis, fragmentation-score,
  leak-pattern-detection, pinned-object-analysis,
  finalizer-queue, object-retention-path,
  duplicate-string, array-distribution, gc-generations

Thread:
  thread-list-stacktrace, deadlock-auto-detect,
  thread-starvation, threadpool-state,
  sync-objects (Monitor/Mutex/Semaphore),
  blocked-thread-detail, async-state-machine,
  cpu-time-distribution

Exception:
  exception-chain, inner-exception-tree,
  all-threads-exceptions, frequency-pattern,
  stack-unwinding

GC:
  segment-map, generation-sizes, pause-time,
  gc-pressure, finalizer-queue-detail, gc-root

CLR:
  appdomain-list, assembly-list, module-map,
  jit-methods, clr-internal-state

ASP.NET / ASP.NET Core:
  active-httprequest-list, httpcontext-detail,
  session-state, request-queue-depth,
  middleware-pipeline-state, signalr-connections,
  endpoint-routing-table, di-container-services

.NET 8+:
  frozen-object-segments, nativeaot-metadata,
  minimal-api-routes, generic-math-analysis

AI Rule Engine:
  antipattern-detection, severity-scoring (Critical/High/Medium/Low),
  turkish-english-summary, solution-suggestions,
  knowledge-base-yaml-hotreload, ollama-ready-interface
8. PLAYBOOK SİSTEMİ
YAML
Hazır Playbook'lar:
  "Memory Leak"       → heap + LOH + finalizer + retention
  "Deadlock"          → thread + sync + deadlock-detect
  "ASP.NET Perf"      → request + threadpool + middleware
  "Crash Analizi"     → exception + crash-thread + clr
  "Thread Starvation" → threadpool + blocked + async
  "GC Baskı"          → gc-segments + gen + pause + roots
  "Full Audit"        → tüm modüller

Kullanıcı Playbook:
  - UI'dan drag-drop modül sıralama
  - Public / Private / Team paylaşım
  - Versiyon geçmişi
  - Agent trigger → otomatik playbook çalıştırma

Akıllı Öneri:
  Agent metadata → Detector → otomatik playbook önerisi
9. DIFF ENGINE
YAML
Karşılaştırma Alanları:
  Heap     : obje sayısı/boyut delta, yeni/kaybolan tipler
  Thread   : count delta, yeni/kaybolan thread'ler
  Exception: yeni/çözülen exception'lar, frekans delta
  GC       : generation boyut değişimleri

UI: Side-by-side, renk kodlu (kırmızı/yeşil), yüzde delta
10. TREND ANALİZİ & ANOMALİ
YAML
Takip Edilen Metrikler:
  Memory, Thread Count, Exception Frequency,
  GC Pressure (zaman serisi, uygulama bazlı)

Anomali Tespiti:
  - Baseline: ilk N dump'tan hesaplanır
  - Standart sapma bazlı anomali skoru
  - Proaktif uyarı (eşik aşılmadan önce)
  - "Son 30 günde kötüleşiyor" tespiti

Otomatik Raporlar:
  - Haftalık trend e-postası
  - Aylık sağlık raporu
  - Dashboard trend widget'ları

Agent Entegrasyonu:
  Trend bozukluğu → Agent'a otomatik dump talimatı
11. REST API & ENTEGRASYON
YAML
Swagger/OpenAPI 3.0 — Tam dokümanlı
API Key Auth — LDAP dışı sistemler için

Endpoints:
  /api/v1/agents/*      → Agent CRUD + trigger
  /api/v1/dumps/*       → Upload + durum + silme
  /api/v1/analysis/*    → Trigger + sonuç + rapor
  /api/v1/reports/*     → HTML / PDF / JSON
  /api/v1/trends/*      → Zaman serisi + özet
  /api/v1/playbooks/*   → CRUD + çalıştırma
  /api/v1/admin/*       → LDAP + kullanıcı + sistem
12. GÜVENLİK & KİMLİK
YAML
LDAP:
  Config: Helm values ↔ UI Settings ↔ PostgreSQL (sync)
  Roller: Admin / Analyst / Viewer
  Group eşleştirme: LDAP group → DumpSight role
  Test butonu: UI'da LDAP bağlantı testi

JWT:
  Access token: 15 dakika
  Refresh token: 8 saat rolling
  Blacklist: Redis
  Concurrent session limiti: configurable

TLS:
  *.kuveytturk.com.tr wildcard
  K8s TLS Secret
  NGINX Ingress TLS termination

Agent Güvenliği:
  Agent registration JWT token
  mTLS (v2 roadmap)
13. AUDIT LOGGING
YAML
Kullanıcı   : Giriş/çıkış, IP, browser, oturum süresi,
              sayfa kalma süreleri, başarısız girişler
Dump        : Upload, analiz talep, silme, paylaşma,
              kaynak etiketi, trigger tipi
Agent       : Kayıt, tetik olayları, dump alma, hata
Rapor       : Export (format, boyut), paylaşma, silme
Sistem      : LDAP config, plugin, rol değişiklikleri
Metrikler   : Per-user analiz sayısı, kullanım süresi,
              en çok kullanılan analiz tipi, export sayısı

Per-User Dashboard:
  Toplam analiz, platform süresi, favori analiz tipi
14. BİLDİRİM & WEBHOOK
YAML
Kanallar:
  E-posta    : SMTP, analiz tamamlandı/başarısız
  Teams      : Incoming Webhook, rich card
  Slack      : Bot token / Incoming Webhook
  HTTP       : Custom endpoint, Handlebars payload,
               retry (3x, exponential backoff)
  SignalR    : Real-time progress, toast, critical alert

Tetikleyiciler:
  Analiz tamamlandı/başarısız, Critical AI finding,
  Storage eşiği (%70 uyarı, %85 kritik),
  Trend anomalisi, Agent bağlantı kesildi

Kullanıcı Tercihleri:
  Kanal seçimi, quiet hours, digest modu
15. STORAGE MANAGER & RETENTION
YAML
Dashboard: NFS kullanım (toplam/kullanılan/boş),
           klasör bazlı breakdown, trend grafik,
           en büyük dump'lar listesi

Retention (Admin configurable):
  /dumps/incoming   : 24 saat
  /dumps/processing : 1 saat
  /dumps/archived   : 30 gün (default)
  /dumps/compressed : 365 gün
  /reports          : 365 gün
  /audit-logs       : 730 gün

Özellikler:
  Otomatik gzip/zstd sıkıştırma, compress ratio raporu
  Soft-delete + 7 gün geri alma
  Manuel toplu temizleme (filtre bazlı)
  Decompress → yeniden analiz desteği
16. PROMETHEUS + GRAFANA
YAML
Custom Metrikler:
  dumpsight_analysis_total / duration_seconds / queue_depth
  dumpsight_upload_bytes_total / active_uploads
  dumpsight_nfs_used_bytes / dump_count_by_status
  dumpsight_agent_count / agent_trigger_total
  dumpsight_active_sessions / login_total / login_failed

Grafana Dashboard'ları:
  1. Platform Overview    5. Agent Status
  2. Storage Dashboard    6. Trend Analytics
  3. User Activity        7. Windows VM Health
  4. System Health
17. MULTI-TENANT PROJE YÖNETİMİ
YAML
Özellikler:
  LDAP group ↔ Proje eşleştirme
  Storage kotası per proje
  Proje bazlı agent yönetimi
  Proje bazlı webhook config
  Proje bazlı retention override
  Cross-project karşılaştırma (Admin only)
  Proje bazlı audit log filtreleme
18. UI — REACT DASHBOARD
YAML
Stack    : React 18 + TypeScript + Ant Design
           + Apache ECharts + SignalR + Redux Toolkit
Theme    : Dark Mode varsayılan + Light toggle
i18n     : Türkçe varsayılan + İngilizce

Sayfalar :
  /                  Dashboard (real-time)
  /upload            Chunked drag-drop upload
  /jobs              Analiz iş kuyruğu
  /analysis/:id      Detaylı analiz sonuçları
  /diff              İki dump karşılaştırma
  /reports           Rapor listesi + export
  /playbooks         Playbook yönetimi
  /plugins           Plugin yönetimi
  /agents            Agent listesi + tetikleme
  /agents/:id        Agent detay + config
  /trends            Trend grafikleri + anomali
  /trends/:appId     Uygulama detaylı trend
  /audit             Audit log + per-user metrik
  /notifications     Bildirim merkezi
  /api-keys          API key yönetimi
  /swagger           Swagger UI
  /admin/users       Kullanıcı yönetimi
  /admin/ldap        LDAP config + test
  /admin/settings    Sistem ayarları
  /admin/storage     NFS dashboard + temizleme
  /admin/projects    Proje + kota yönetimi
19. HELM CHART YAPISI
Code
dumpsight/
├── Chart.yaml
├── values.yaml
├── values-dev.yaml
├── values-prod.yaml
├── charts/
│   ├── postgresql-15.x.x.tgz
│   └── rabbitmq-12.x.x.tgz
└── templates/
    ├── _helpers.tpl / NOTES.txt
    ├── namespace / configmap / secret
    ├── serviceaccount / rbac
    ├── ingress (wildcard TLS)
    ├── pv-nfs / pvc
    ├── network-policy
    ├── pod-disruption-budget
    ├── api-gateway/
    ├── upload-service/
    ├── detector-service/
    ├── analyzer-service/ (+ hpa.yaml)
    ├── windows-vm-bridge/
    ├── report-service/
    ├── notification-service/
    ├── audit-service/
    ├── playbook-service/
    ├── diff-engine/
    ├── trend-service/
    ├── agent-manager/
    └── ui/
20. AIR-GAPPED BUILD & DEPLOY
YAML
Harbor Images:
  cr-test.kuveytturk.com.tr/dumpsight/
    api-gateway, upload-service, detector-service,
    analyzer-service, windows-vm-bridge,
    report-service, notification-service,
    audit-service, playbook-service, diff-engine,
    trend-service, agent-manager,
    agent-linux, agent-windows,
    ui, charts/dumpsight (OCI Helm)

Nexus Proxy: nuget + npm + docker mirror
Dockerfile  : Multi-stage, Nexus üzerinden paket
Agent MSI   : Windows offline kurulum paketi
Base Images : mcr.microsoft.com/* → Harbor mirror
21. YAZMA SIRASI
Code
1.  Helm Chart iskeleti + values.yaml
2.  API Gateway + Auth (JWT/LDAP) + Redis
3.  Upload Service + NFS Watch + Intake Pipeline
4.  Detector Service (fingerprinting engine)
5.  Linux Analyzer (ClrMD + dotnet-dump + LLDB)
6.  Windows VM Bridge Service
7.  AI Rule Engine
8.  Report Service (HTML/PDF/JSON)
9.  Playbook + Diff + Trend + Audit servisleri
10. Notification Service
11. Agent Manager Service
12. Linux Agent (dotnet-monitor tabanlı)
13. Windows Agent (MSI + ProcDump)
14. React UI (tüm sayfalar)
15. Prometheus metrics + Grafana dashboards
16. E2E test + Helm lint + CI pipeline
