import requests
import gzip
import shutil
from pathlib import Path

# Liste de départements 
```
DEPARTEMENTS = [
    # Métropole
    "01","02","03","04","05","06","07","08","09","10",
    "11","12","13","14","15","16","17","18","19","21",
    "22","23","24","25","26","27","28","29","2A","2B",
    "30","31","32","33","34","35","36","37","38","39",
    "40","41","42","43","44","45","46","47","48","49",
    "50","51","52","53","54","55","56","57","58","59",
    "60","61","62","63","64","65","66","67","68","69",
    "70","71","72","73","74","75","76","77","78","79",
    "80","81","82","83","84","85","86","87","88","89",
    "90","91","92","93","94","95","971","972","973","974","976"
]
```

BASE_URL = "https://www.data.gouv.fr/datasets/donnees-climatologiques-de-base-quotidiennes"

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


