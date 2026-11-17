# Irrigation Tree

Notebook studi kasus decision tree untuk keputusan kapan pompa irigasi sawah harus menyala:
[`irigation-decision-tree.ipynb`](irigation-decision-tree.ipynb).

## Menjalankan notebook

```bash
python -m venv .venv
.venv\Scripts\activate        # Windows
# source .venv/bin/activate   # macOS / Linux

pip install notebook
jupyter notebook irigation-decision-tree.ipynb
```

Dependensi notebook (`numpy`, `pandas`, `matplotlib`, `scikit-learn`) tidak perlu dipasang
manual: sel pertama otomatis menginstal paket yang belum ada lewat `pip`.
Jika kernel sudah telanjur berjalan, restart kernel lalu jalankan ulang sel tersebut.

## Output notebook tidak ikut di-commit

Repo ini memakai [nbstripout](https://github.com/kynan/nbstripout) sebagai git clean filter.
Output sel, `execution_count`, dan metadata kernel dibuang saat file di-`git add`, sehingga
diff notebook tetap bersih dan tidak ada konflik karena output.

`.gitattributes` sudah berisi konfigurasi filternya, tetapi filter harus didaftarkan sekali
di setiap clone (pengaturan git bersifat lokal, tidak ikut ter-commit):

```bash
pip install -r requirements-dev.txt
nbstripout --install
```

Perintah di atas mengatur `filter.nbstripout.clean` dan `diff.ipynb.textconv` di `.git/config`.
Cek dengan:

```bash
nbstripout --is-installed
```

Untuk membersihkan output pada file yang sudah ada tanpa commit:

```bash
nbstripout irigation-decision-tree.ipynb
```
