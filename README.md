[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23573936&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** buicaochinh0811@gmail.com
**Name:** Bùi Cao Chinh

---

## Mo ta

Bai lab nay xay dung mot ETL pipeline don gian de doc du lieu tu `raw_data.json`, kiem tra chat luong du lieu, chuan hoa va them thong tin quan sat truoc khi luu ra `processed_data.csv`.

Ngoai phan ETL, du an con co mot thuc nghiem nho de so sanh hanh vi cua agent khi dung du lieu sach va du lieu “garbage”. Ket qua duoc tong hop trong `experiment_report.md`.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

Script se:
- doc du lieu tu `raw_data.json`
- loai bo ban ghi co `price <= 0` hoac `category` trong
- tao cot `discounted_price` va `processed_at`
- luu ket qua ra `processed_data.csv`

### Chay Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python agent_simulation.py
```

Lenh dau tao `garbage_data.csv` tu bo du lieu co loi. Lenh thu hai chay agent simulation tren ca `processed_data.csv` va `garbage_data.csv` de quan sat su khac nhau trong cau tra loi.

### Chay test neu can
```bash
python -m pytest -q
```

---

## Cau truc thu muc

```
├── agent_simulation.py     # Mo phong agent tra loi dua tren du lieu
├── experiment_report.md    # Bao cao thi nghiem Data Quality
├── generate_garbage.py     # Tao bo du lieu loi de stress test
├── garbage_data.csv        # Du lieu loi duoc sinh ra
├── processed_data.csv      # Output cua ETL pipeline
├── raw_data.json           # Input goc cho ETL pipeline
├── solution.py              # ETL Pipeline script
├── tests/                   # Autograder tests
└── README.md                # File nay
```

---

## Ket qua

Sau khi chay pipeline, `raw_data.json` co tong cong 5 ban ghi. Trong do:

- 3 ban ghi hop le duoc giu lai va luu vao `processed_data.csv`
- 2 ban ghi bi loai bo trong buoc validation do `price <= 0` hoac `category` trong

Du lieu dau ra bao gom cac cot `discounted_price` va `processed_at`, trong khi `category` duoc chuan hoa ve Title Case.

O phan stress test, agent tra loi on dinh hon voi `processed_data.csv` va de bi sai lech hon khi dung `garbage_data.csv`. Phan tich chi tiet co trong `experiment_report.md`.
