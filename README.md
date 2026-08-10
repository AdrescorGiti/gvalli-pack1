<img width="1169" height="1169" alt="Gemini_Generated_Image_k0o74ik0o74ik0o7-no-bg-preview (carve photos)" src="https://github.com/user-attachments/assets/9a143b1a-5286-4b91-96aa-6aa11c47f54d" />
const char* README_MARKDOWN = R"(
# 🛡️ VTest — Core Security & Malware Inspection Engine for G OS

<p align="center">
 <img width="500" height="500" alt="Gemini_Generated_Image_k0o74ik0o74ik0o7-no-bg-preview (carve photos)" src="https://github.com/user-attachments/assets/9a143b1a-5286-4b91-96aa-6aa11c47f54d" />
</p>

> **VTest** — это высокопроизводительный, легкий и бескомпромиссный антивирусный движок, разработанный специально для экосистемы **G OS** и пакетов формата `.gpkg`.

---

## 🚀 Ключевые особенности

* **⚡ Высокая скорость работы:** Минимальное потребление системных ресурсов за счет оптимизированных алгоритмов анализа.
* **🔍 Многоуровневое сканирование:**
  * **Static ELF Inspection:** Анализ заголовков и структуры бинарных файлов Linux.
  * **Heuristic Script Engine:** Поиск вредоносных сценариев, реверс-шеллов и опасных команд.
  * **Entropy Analysis:** Детектирование зашифрованных, обфусцированных и упакованных данных.
* **🌐 Интеграция с G OS & GValli:** Проверка входящих артефактов в CI/CD пайплайнах репозитория `gvalli-repo`.
* **🛡️ Интеллектуальный Whitelist:** Поддержка белых списков хешей (SHA-256) для исключения ложных срабатываний на сложные сетевые утилиты (Sing-box, Hiddify, Happ).

---

## 🛠️ Установка и сборка

### Быстрая установка через GValli

    curl -sSLf -o vtest.gpkg https://github.com/AdrescorGiti/gvalli-repo/raw/refs/heads/main/vtest-0.1.0.gpkg
    sudo gvalli install ./vtest.gpkg

### Сборка из исходников (Rust)

    git clone https://github.com/AdrescorGiti/vtest.git
    cd vtest
    cargo build --release
    sudo cp target/release/vtest /usr/local/bin/

---

## 📖 Использование CLI

### Проверка пакета .gpkg

    # Базовая проверка артефакта
    vtest check package.gpkg

    # Сканирование распакованной директории
    vtest scan /tmp/unpack_dir/

### Коды возврата (Exit Codes)

| Код | Статус | Описание |
| :--- | :--- | :--- |
| `0` | **CLEAN** | Файл безопасен и готов к установке/публикации. |
| `1` | **MALWARE / RISK** | Обнаружена угроза, подозрительная энтропия или вредоносный скрипт. |
| `2` | **ERROR** | Ошибка чтения файла или поврежденный архив. |

---

## ⚙️ Интеграция в CI/CD (GitHub Actions)

    - name: Run VTest Security Inspection
      run: |
        vtest check package.gpkg
        if [ $? -ne 0 ]; then
          echo "Security audit failed!"
          exit 1
        fi

---

## 📄 Лицензия

Распространяется под лицензией **MIT**. Разработано в рамках инициативы **G OS Security Standard**.
)";
