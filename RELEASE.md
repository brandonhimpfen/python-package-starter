# Release Checklist

## 1. Update Version

Update the version in `pyproject.toml`:

```toml
version = "0.1.1"
```

---

## 2. Run Tests

```bash
python -m pytest
```

---

## 3. Clean Previous Builds

```bash
rmdir /s /q dist
rmdir /s /q build
rmdir /s /q src\PACKAGE_IMPORT_NAME.egg-info
```

(If a folder does not exist, ignore the error.)

---

## 4. Build Package

```bash
python -m build
```

---

## 5. Check Distribution

```bash
python -m twine check dist/*
```

---

## 6. Upload to PyPI

```bash
python -m twine upload dist/*
```

---

## 7. Verify Install

```bash
python -m pip install PACKAGE_NAME
```

---

## Notes

- Ensure your PyPI API token is set up (`__token__` login).
- Versions cannot be reused once uploaded.
- If upload fails, retry with:

```bash
python -m twine upload --verbose dist/*
```