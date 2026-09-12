# 🛰️ kmk_kosmo — Проектирование спутниковой группировки - KMKt3am

Веб-сервис для моделирования спутниковой группировки (48 аппаратов, 550 км)
и оценки доступности связи в северных районах. КосмоХакатон 2026.

---

## 📥 Скачать проект

**Через git:**
```bash
git clone https://github.com/Fgmod/kmk_kosmo.git
cd kmk_kosmo
Без git: GitHub → Code → Download ZIP → распаковать → открыть терминал в папке kmk_kosmo.
Также присутствует установка через сервис Gitverce

🍎 Запуск на macOS
cd ~/Downloads/kmk_kosmo (kmk_kosmo-main)
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
cd backend
uvicorn main:app --reload --host 127.0.0.1 --port 8000 (uvicorn main:app --reload --port 8000)

Открыть в браузере: http://localhost:8000
Остановить: Ctrl + C
Требуется Python 3.10+ — проверить: python3 --version.
Если не установлен: https://www.python.org/downloads/macos/

🪟 Запуск на Windows
Открыть PowerShell в папке kmk_kosmo:
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
cd backend
uvicorn main:app --reload --host 127.0.0.1 --port 8000

Если PowerShell блокирует активацию — один раз выполнить:
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
и подтвердить Y.
Открыть в браузере: http://localhost:8000
Остановить: Ctrl + C
Требуется Python 3.10+ — проверить: python --version.
Если не установлен: https://www.python.org/downloads/windows/ (галочка Add Python to PATH).

✅ Как проверить работу

    Выбрать сценарий 01_full_constellation → ▶ Рассчитать.

    Появятся доступность клиентов, карта, маршрут, диаграмма.

    Переключить «Очередь запуска» на 1 и пересчитать — доступность упадёт.

    Добавить отказ спутника → пересчитать → увидеть перерыв.

🆘 Частые ошибки
         Ошибка	                                            Решение
command not found: uvicorn	               Не активировано окружение — выполнить source .venv/bin/activate (mac)
                                           или venv\Scripts\Activate.ps1 (win)

ModuleNotFoundError: main	                       Запускать uvicorn из папки backend

Address already in use	                   Порт занят — заменить --port 8000 на --port 8001

python: command not found (win)	                  Использовать py вместо python

📁 Структура
kmk_kosmo/
├── backend/        # FastAPI, расчёты, маршрутизация
├── frontend/       # UI: карта, таймлайн, сравнение
├── data/           # 4 JSON-сценария
├── requirements.txt
└── README.md

🎯 Возможности сервиса
Загрузка сценариев cosmo-A-1.0 (4 встроенных + свои).
Редактирование: очередь запуска, RAAN, фазирование, угол возвышения, ISL.
Маршрутизация «клиент → спутники → шлюз» (BFS) с пересчётом на каждом шаге.
Учёт отказов спутников и шлюзов.
Сравнение вариантов, анализ уязвимых аппаратов.
Выгрузка результата в формате cosmo-A-result-1.0.
