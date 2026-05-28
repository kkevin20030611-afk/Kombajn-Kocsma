# Kombájn-Kocsma (AgroPour) - Okos Italadagoló

A **Kombájn-Kocsma** egy ESP32 mikrovezérlővel hajtott, teljesen automatizált italadagoló robot, amely egy Bruder (vagy hasonló) játék kombájn belsejébe van rejtve. A projekt célja egy olyan bulieszköz létrehozása, ami okostelefonról vezérelve, beépített szervómotorral fordul a poharak fölé, és precízen teletölti azokat.

---

## Hogyan fog működni a rendszer?

A gép egy zárt, "okos" ökoszisztémaként funkcionál, a felhasználóknak csak a poharakat kell a megfelelő helyre tenniük.

* **Csatlakozás (Webszerver):** Bekapcsolás után az ESP32 létrehoz egy saját Wi-Fi hálózatot. A játékosok a telefonjukkal rácsatlakoznak, és megnyitják a beépített webes felületet.
* **Rendelés leadása:** A telefonos felületen kiválasztható a kívánt felesek (poharak) száma.
* **A Cső Kifordulása (Szervó):** Az indítás után a kombájn eredeti ürítőcsövébe rejtett szilikoncső egy szervómotor segítségével kifordul az első pohár fölé.
* **Töltés (Pumpa):** Egy 5V-os relé rákapcsolja az áramot az R385-ös vízpumpára. A gép tizedmásodperc pontosan annyi ideig pumpál, amíg a beállított italmennyiség a pohárba nem kerül.
* **Sorozat-töltés és Befejezés:** A motor továbbfordul a következő poharakhoz (ha többet állítottak be), mindegyiket teletölti, majd a munka végeztével a cső visszazár az alap, elrejtett pozícióba.

---

## Tervezett Alkatrészek (Beszerzés alatt)

A játék gyári burkolata alá az alábbi hardverelemek kerülnek beépítésre:

* **ESP32-C3 Super Mini:** A rendszer agya, amely a Wi-Fi webszervert futtatja és a hardvereket vezérli.
* **R385 Membránszivattyú:** A folyadék felszívásáért és adagolásáért felelős egyenáramú motor.
* **SG90 / MG996R Szervómotor:** A kombájn ürítőcsövének precíz, fokra pontos mozgatását végzi.
* **5V 1-csatornás Relé Modul:** Megvédi az ESP32-t, és biztonságosan rákapcsolja a nagyobb áramot a vízpumpára.
* **Élelmiszeripari Szilikoncső (6x9mm):** A belső folyadéktartály és az ürítőcső közötti biztonságos összeköttetésért felel.
* **Áramforrás:** 4 db AA elem (6V) vagy egy 5V Powerbank a stabil és hordozható működéshez.

---

## Jelenlegi Státusz: Tervezési és Prototípus Fázis

> **INFO:** A projekt jelenleg a hardveres és szoftveres tervezés szakaszában van. A végleges kapcsolási rajz (Wiring) és a fizikai beépítés dokumentációja a sikeres tesztek után kerül publikálásra.

**Aktuális mérföldkövek:**
* Hardverelemek (ESP32, pumpa, csövezés, relé) kiválasztása és beszerzése folyamatban.
* Az alapvető működési logika (gombnyomásra történő szervó-mozgatás és relé-kapcsolás) Wokwi szimulátorban sikeresen letesztelve.
* A "Sorozatlövő" (több poharat egymás után megtöltő) algoritmus matematikai alapjai és időzítései elkészültek.
* **Következő lépések:** Alkatrészek asztali tesztelése próbapanelen, forrasztás, Wi-Fi webszerver kódolása, majd a legnehezebb fizikai fázis: az alkatrészek roncsolásmentes beépítése a kombájn műanyag testébe.
