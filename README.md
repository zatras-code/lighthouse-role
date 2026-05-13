# Ansible Role: LightHouse

Ansible роль для установки и настройки **LightHouse** — веб-интерфейса для работы с ClickHouse.

Роль устанавливает веб-сервер nginx и разворачивает LightHouse как статическое веб-приложение.

---

## Возможности роли

- Установка `nginx` и `git`
- Клонирование репозитория LightHouse
- Размещение статики в web-root
- Деплой конфигурации nginx через template
- Включение сайта
- Запуск и включение nginx
- Идемпотентная установка

---

## Требования

- Ansible >= 2.14
- ОС: Debian / Ubuntu
- Доступ по SSH
- Права `sudo` (become задаётся в play)

---

## Переменные роли

Перем́еменные находятся в `defaults/main.yml`.

| Переменная | Описание | Значение по умолчанию |
|----------|----------|------------------------|
| `lighthouse_install_dir` | Каталог установки | `/var/www/lighthouse` |
| `lighthouse_repo` | Git-репозиторий LightHouse | `https://github.com/VKCOM/lighthouse/archive/refs/heads/master.tar.gz` |
| `nginx_listen_port` | Порт nginx | `80` |
| `nginx_server_name` | ServerName | `_` |

---

## Шаблоны

- `templates/lighthouse.conf.j2` — конфигурация nginx для LightHouse

---

## Handlers

- `Reload nginx` — перезагрузка nginx при изменении конфигурации

---

## Пример использования роли

```yaml
- name: Install LightHouse
  hosts: lighthouse
  become: true
  roles:
    - lighthouse_role
```
---