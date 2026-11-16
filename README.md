# Лабораторная работа: Настройка SSH-доступа к GitHub

**Студент:** Данил Гребенщиков

**GitHub:** [danilGrebenshikov](https://github.com/danilGrebenshikov)

**Репозиторий:** https://github.com/danilGrebenshikov/GitHub-Actions-CI

## 1. Установка SSH-клиента и генерация ключевой пары

Проверка наличия SSH-клиента:

```bash
ssh -V
Генерация ключа ed25519 с passphrase:

bash
ssh-keygen -t ed25519 -C "danilgrebensikov7@gmail.com"
Ключ сохранён в ~/.ssh/id_ed25519, приватный ключ защищён passphrase.

https://images/01_ssh_version.png

https://images/02_ssh_keygen.png

https://images/03_ssh_ls.png

Проверка, что ключ защищён passphrase (команда запрашивает пароль):

bash
ssh-keygen -y -f ~/.ssh/id_ed25519
https://images/04_key_passphrase_check.png

Публичный ключ:

bash
cat ~/.ssh/id_ed25519.pub
https://images/05_public_key.png

## 2. Добавление публичного ключа в GitHub
Ключ добавлен: GitHub → Settings → SSH and GPG keys → New SSH key.

https://images/06_github_key.png

## 3. Проверка SSH-подключения
bash
ssh -T git@github.com
Результат:

text
Hi danilGrebenshikov! You've successfully authenticated, but GitHub does not provide shell access.
https://images/07_ssh_T.png

## 4. Работа с репозиторием по SSH
Клонирование по SSH-URL:

bash
git clone git@github.com:danilGrebenshikov/GitHub-Actions-CI.git
cd GitHub-Actions-CI
Создание коммита и push:

bash
echo "# SSH Test" >> test.md
git add test.md
git commit -m "Test SSH push"
git push origin main
Push выполнен без запроса пароля GitHub (используется SSH-ключ).

https://images/08_push.png

## Вывод
В ходе работы настроен SSH-доступ к GitHub: сгенерирован ключ ed25519 с passphrase, публичный ключ добавлен в аккаунт, проверено подключение через ssh -T, выполнены clone/commit/push по SSH-URL без запроса пароля GitHub. Навыки работы с SSH-ключами и Git освоены.
