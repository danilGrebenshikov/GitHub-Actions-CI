\# Лабораторная работа: Настройка SSH-доступа к GitHub



\*\*Студент:\*\* Данил Гребенщиков

\*\*GitHub:\*\* \[danilGrebenshikov](https://github.com/danilGrebenshikov)

\*\*Репозиторий:\*\* https://github.com/danilGrebenshikov/GitHub-Actions-CI



\## 1. Установка SSH-клиента и генерация ключевой пары



Проверка наличия SSH-клиента:



&#x20;   ssh -V



Генерация ключа ed25519 с passphrase:



&#x20;   ssh-keygen -t ed25519 -C "danilgrebensikov7@gmail.com"



Ключ сохранён в `\~/.ssh/id\_ed25519`, приватный ключ защищён passphrase.



!\[ssh -V](images/01\_ssh\_version.png)

!\[ssh-keygen](images/02\_ssh\_keygen.png)

!\[ls \~/.ssh](images/03\_ssh\_ls.png)



Проверка, что ключ защищён passphrase (команда запрашивает пароль):



&#x20;   ssh-keygen -y -f \~/.ssh/id\_ed25519



!\[passphrase check](images/04\_key\_passphrase\_check.png)



Публичный ключ:



&#x20;   cat \~/.ssh/id\_ed25519.pub



!\[public key](images/05\_public\_key.png)



\## 2. Добавление публичного ключа в GitHub



Ключ добавлен: GitHub → Settings → SSH and GPG keys → New SSH key.



!\[github key](images/06\_github\_key.png)



\## 3. Проверка SSH-подключения



&#x20;   ssh -T git@github.com



Результат:



&#x20;   Hi danilGrebenshikov! You've successfully authenticated, but GitHub does not provide shell access.



!\[ssh -T](images/07\_ssh\_T.png)



\## 4. Работа с репозиторием по SSH



Клонирование по SSH-URL:



&#x20;   git clone git@github.com:danilGrebenshikov/GitHub-Actions-CI.git

&#x20;   cd GitHub-Actions-CI



Создание коммита и push:



&#x20;   echo "# SSH Test" >> test.md

&#x20;   git add test.md

&#x20;   git commit -m "Test SSH push"

&#x20;   git push origin main



Push выполнен без запроса пароля GitHub (используется SSH-ключ).



!\[push](images/08\_push.png)

