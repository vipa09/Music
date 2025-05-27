import os
import zipfile
import urllib.request

# === Einstellungen ===
ZIP_URL = "https://example.com/deine.zip"   # ❗️Hier deine echte URL einsetzen
ZIELORDNER = "/sdcard/Download/Projekt"     # ❗️Anpassen je nach Speicherort

# ZIP-Datei temporär speichern
TEMP_ZIP = "/sdcard/Download/temp.zip"

# Zielverzeichnis anlegen
try:
    os.makedirs(ZIELORDNER, exist_ok=True)
except:
    pass  # Falls es schon existiert oder kein Zugriff

# ZIP herunterladen
try:
    print("📥 Lade ZIP herunter...")
    urllib.request.urlretrieve(ZIP_URL, TEMP_ZIP)
except Exception as e:
    print("❌ Fehler beim Download:", e)
    exit()

# ZIP entpacken
try:
    print("📦 Entpacke ZIP...")
    with zipfile.ZipFile(TEMP_ZIP, 'r') as zip_ref:
        for file in zip_ref.namelist():
            zielpfad = os.path.join(ZIELORDNER, file)

            # Wenn Datei, extrahiere & überschreibe
            if not file.endswith('/'):
                os.makedirs(os.path.dirname(zielpfad), exist_ok=True)
                with zip_ref.open(file) as quelle, open(zielpfad, "wb") as ziel:
                    ziel.write(quelle.read())

    print("✅ Entpackt nach:", ZIELORDNER)
    os.remove(TEMP_ZIP)

except Exception as e:
    print("❌ Fehler beim Entpacken:", e)
