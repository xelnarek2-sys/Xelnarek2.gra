# Release: Crimsonland Blood Shift v1.0.0 (Draft release notes)

Binary: Crimsonland_Blood_Shift_INSTALLABLE.apk
Raw download URL:
https://raw.githubusercontent.com/xelnarek2-sys/Xelnarek2.gra/main/Crimsonland_Blood_Shift_INSTALLABLE.apk

Verification
----------
1) Pobierz plik na komputer:
   wget -O Crimsonland_Blood_Shift_INSTALLABLE.apk "https://raw.githubusercontent.com/xelnarek2-sys/Xelnarek2.gra/main/Crimsonland_Blood_Shift_INSTALLABLE.apk"

2) Sprawdź sumę SHA‑256 (ważne — porównaj wynik z plikiem .sha256 w repo):
   sha256sum Crimsonland_Blood_Shift_INSTALLABLE.apk

Instalacja na urządzeniu Android
-------------------------------
1) Włącz Debugowanie USB (Ustawienia → Opcje programisty → Debugowanie USB) lub przygotuj plik na urządzeniu.
2) Upewnij się, że urządzenie pozwala instalować aplikacje z zewnętrznych źródeł (Settings → Apps → wybierz przeglądarkę/menedżer plików → Install unknown apps → Allow).
3) Podłącz urządzenie i zainstaluj przez ADB:
   adb devices
   adb install -r Crimsonland_Blood_Shift_INSTALLABLE.apk

4) (Opcjonalnie) Zweryfikuj podpis APK:
   apksigner verify --verbose Crimsonland_Blood_ShIFT_INSTALLABLE.apk

Rozwiązywanie problemów
-----------------------
- INSTALL_PARSE_FAILED_NO_CERTIFICATES / apksigner zwraca błąd:
  -> APK nie jest podpisane; podpisz lokalnie przed instalacją (instrukcja poniżej).

- INSTALL_FAILED_UPDATE_INCOMPATIBLE:
  -> Na urządzeniu jest zainstalowana inna wersja podpisana innym kluczem. Usuń starą:
     adb uninstall <package.name>
     adb install -r Crimsonland_Blood_Shift_INSTALLABLE.apk

- INSTALL_FAILED_VERSION_DOWNGRADE:
  -> Usuń wcześniejszą wersję lub użyj nowszego builda.

- Brak miejsca:
  -> Usuń niepotrzebne aplikacje lub zainstaluj na innym urządzeniu.

Jak podpisać APK lokalnie (jeśli wymaga tego apksigner)
-------------------------------------------------------
1) Wygeneruj lokalny keystore (tylko lokalnie):
   keytool -genkey -v -keystore debug.keystore -alias debug -keyalg RSA -keysize 2048 -validity 10000

2) Podpisz APK:
   apksigner sign --ks debug.keystore --ks-key-alias debug Crimsonland_Blood_Shift_INSTALLABLE.apk

3) Sprawdź podpis:
   apksigner verify --verbose Crimsonland_Blood_Shift_INSTALLABLE.apk

Uwagi końcowe
-------------
- Zalecane: po publikacji Release pobieraj APK z zakładki Releases (asset) — wtedy użytkownicy łatwiej pobiorą plik i zobaczą notkę wydania.
- Jeśli chcesz, mogę przygotować Draft Release w GitHub UI i przesłać tam plik jako asset. W tej chwili w repo jest raw URL (powyżej) do pobrania.

