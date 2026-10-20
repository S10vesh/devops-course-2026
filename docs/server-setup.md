\# Конфигурация виртуальной машины devops-vm



\## 1. Параметры машины

\- Объем памяти: 2048 МБ

\- Количество ядер: 2

\- Объем диска: 25 ГБ (VDI, динамически расширяемый)



\## 2. Сетевые интерфейсы

\- enp0s3: NAT (10.0.2.15) — доступ в Интернет, обновления

\- enp0s8: Host-only (192.168.56.101) — доступ с хоста, веб-сервер (ПР №6)



\## 3. Правило проброса портов

\- Порт хостовой системы: 2222 → Порт гостевой системы: 2222 (TCP)



\## 4. Учётные записи

\- student: состоит в группе sudo, аутентификация по паролю

\- devops: состоит в группе sudo, аутентификация по ключу (\~/.ssh/devops\_vm)



\## 5. Служба SSH

\- Порт: 2222

\- Расположение файла конфигурации: /etc/ssh/sshd\_config.d/99-hardening.conf

\- Изменённые директивы:

&#x20; - PermitRootLogin no

&#x20; - PasswordAuthentication no

&#x20; - PubkeyAuthentication yes

&#x20; - PermitEmptyPasswords no

&#x20; - MaxAuthTries 3

&#x20; - LoginGraceTime 30

&#x20; - AllowUsers devops

&#x20; - X11Forwarding no

&#x20; - ClientAliveInterval 300

&#x20; - ClientAliveCountMax 2



\## 6. Правила межсетевого экрана (UFW)

\- Политика по умолчанию: deny incoming, allow outgoing

\- Перечень правил:

&#x20; - 2222/tcp LIMIT (SSH)

&#x20; - 80/tcp (HTTP)

&#x20; - 443/tcp (HTTPS)





