import requests
import gzip
import shutil
from pathlib import Path

# Liste de départements (exemple)
DEPARTEMENTS = ["75", "77", "78", "91", "92", "93", "94", "95"]

BASE_URL = "https://static.data.gouv.fr/resources/donnees-climatologiques-de-base-quotidiennes"

FILES = ["RR-T-Vent","autres-parametres"]

DATA_DIR = Path("data")
DATA_DIR.mkdir(exist_ok=True)

for dep in DEPARTEMENTS:
    dep_dir = DATA_DIR / dep
    dep_dir.mkdir(exist_ok=True)

    for ftype in FILES:
        filename = f"QUOT_departement_{dep}_periode_2025-2026_{ftype}.csv.gz"
        url = f"{BASE_URL}/{filename}"

        gz_path = dep_dir / filename
        csv_path = dep_dir / filename.replace(".csv.gz", ".csv")


