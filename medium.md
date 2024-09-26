# Medium



Nesa — это Layer1 блокчейн, выполняющий критические выводы ИИ по запросам, требующим высокой степени конфиденциальности, безопасности и доверия, с использованием передовых методов на цепочке, включая машинное обучение с нулевым знанием (ZKML), раздельное обучение (SL) и другие.

Nesa была создана как альтернатива ChatGPT и другим современным платформам вывода, которые централизованы и контролируются крупными игроками. Эти платформы имеют нулевую видимость или подотчетность в своих результатах по вашим критическим операциям и обеспечивают нулевую конфиденциальность ваших данных и результатов.

Nesa представляет первый модельно-агностический подход к гибридному шардингу, наслоенный на программно-аппаратный протокол конфиденциальности. Это решение распределяет вычислительную нагрузку между несколькими узлами децентрализованной сети вывода. Распределенный протокол Nesa обеспечивает обработку данных с сохранением конфиденциальности, а также способствует масштабируемому и проверяемому выполнению выводов ИИ. На рисунке ниже показаны ключевые компоненты

**Установка Майнера**

Данное программное обеспечение находится в стадии бета-тестирования и в первую очередь предназначено для машин Ubuntu/Debian с графическими процессорами с поддержкой CUDA, однако графический процессор не является обязательным для запуска узла майнера. Поддержка других аппаратных и программных конфигураций является экспериментальной и будет улучшена со временем.

_**Рекомендуемые технические характеристики**_

_**Подготовка сервера**_

```
sudo apt update && sudo apt upgrade -y
apt install curl iptables build-essential git wget jq make gcc nano tmux htop nvme-cli pkg-config libssl-dev libleveldb-dev libgmp3-dev tar clang bsdmainutils ncdu unzip llvm libudev-dev make protobuf-compiler -y
```

_**Устанавливаем Docker и Docker Compose**_

```
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.ascecho \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get updatesudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
docker --version
```

_**Далее вводим следующее**_

```
sudo groupadd docker
sudo usermod -aG docker $USER
apt install jq
```

_**Создаем API Токен на Hugging Face**_

* Регистрируемся на сайте [https://huggingface.co/docs/hub/security-tokens](https://huggingface.co/docs/hub/security-tokens)
* Переходим в настройки аккаунта и выбираем Access Tokens
* Нажимаем “Cteate new token” — и сохраняем наш API токена в надежном месте!

_**Установка**_

```
bash <(curl -s https://raw.githubusercontent.com/nesaorg/bootstrap/master/bootstrap.sh)
```

_Далее скрипт будет просить нас ввести различные данные_

_Select Mode - выбираем Wizardy_

_Moniker- вводим имя Ноды_

_Hostname, Domain- пропускаем нажимаем Enter_

_Email Node- вводим свой EMail_

_Далее выбираем Miner_

Далее нас попросят Приватный ключ. Ключ нам необходим не от EVM а от Cosmos. Чтобы вытащить ключ нам понадобится кошелек Leap

_Далее выбираем- Non-Distributed_

_Далее выбираем модель, например_ [_meta-llama/Meta-Llama-3.1-70B-Instruct_](https://huggingface.co/meta-llama/Meta-Llama-3.1-70B-Instruct) _и вводим ее._

Затем переходим сюда [https://huggingface.co/meta-llama/Meta-Llama-3.1-70B-Instruct](https://huggingface.co/meta-llama/Meta-Llama-3.1-70B-Instruct) и нажимаем ‘Dismiss” в правом углу.

Теперь нас попросят ввести API ключ который мы сохраняли ранее- вводим его

Затем мы увидим нашу конфигурацию, нажимает Y и ждем появления логов..

_Логи должны быть такого типа:_

_**Просмотр статистики в браузере**_

```
node_id=$(cat $HOME/.nesa/identity/peer_id.id)
echo https://node.nesa.ai/nodes/$node_id
```

_**Просмотр логов**_

```
docker logs -f -n 100 orchestrator
docker logs -f -n 100 ipfs_node
docker logs -f -n 100 mongodb
```

**Тестнет**

[**https://beta.nesa.ai/**](https://beta.nesa.ai/)

Для того чтобы попасть на платформу тестнета необходимо написать и получить Whitelist у @fielding в Дискорде — [https://discord.com/invite/Z4jZPTdfcY](https://discord.com/invite/Z4jZPTdfcY)

После того как получили доступ на платформу переходим во вкладку Faucet подключаем Twitter и коннектим свой Keplr или Leap кошелек
