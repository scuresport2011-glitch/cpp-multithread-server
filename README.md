# cpp_multithread_server

[![build](https://github.com/scuresport2011-glitch/cpp-multithread-server/actions/workflows/build.yml/badge.svg)](https://github.com/scuresport2011-glitch/cpp-multithread-server/actions/workflows/build.yml)

Многопоточный TCP-сервер на C++17 с кастомным текстовым протоколом.
Проект написан для изучения сокетов, сетевых протоколов и параллельного
программирования: всё собрано на стандартной библиотеке и POSIX, без
внешних зависимостей.

## Что умеет

- Принимает TCP-подключения на заданном порту.
- Обслуживает клиентов в пуле потоков, не блокируя accept.
- Понимает текстовый протокол команд (`PING`, `ECHO`, `TIME`, `STATS`, `QUIT`, `HELP`).
- Потокобезопасный логгер с уровнями `DEBUG/INFO/WARN/ERROR`.
- Ограничение числа клиентов, idle-timeout, лимит длины строки запроса.
- Корректное завершение по `Ctrl+C` (SIGINT/SIGTERM) — дожидается активных клиентов.

## Сборка и запуск

```bash
cmake -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build -j
./build/cpp_multithread_server --port 8080 --threads 4 --max-clients 100