## Репозиторий с конфигурационными файлами Terraform

Для начала, с помощью Terraform, был создан S3 бакет и учетная запись для Terraform Backend:

https://github.com/jaack1/diploma-terraform-init

Затем, с помощью новых манифестов была развернута инфраструктура - сеть, подсети,
K8s региональный мастер, NAT шлюз для узлов k8s и сами узлы

https://github.com/jaack1/diploma-terraform

далее, в кластере была развернут nginx-ingress
система мониторинга, пакет [kube-prometheus](https://github.com/prometheus-operator/kube-prometheus)
и [atlantis](https://www.runatlantis.io/) для отслеживания изменений инфраструктуры
для доступности извне были настроены ingress для этих сервисов.

## Пример pull request с комментариями созданными atlantis'ом

Через вэбхуки была настроена связанность atlantis и github, при pull request в ветку main, atlantis проводит
тестирование plan и отображает результат в комментариях к PR. Далее, я выбираю необходимое действие (например apply),
пишу соответсвующий комментарий в PR, создаётся вэбхук и atlantis выполняет команду.

https://github.com/jaack1/diploma-terraform/pull/11

## Репозиторий с Dockerfile тестового приложения и ссылка на собранный docker image.

Создано тестовое приложение (Nginx раздаёт статическую страницу. Настроена автосборка в реестр по коммиту и деплой на стенд по тегу.
CI/CD реализован через GitHub Actions. Для описания манифестов приложения используется Helm Chart.

https://github.com/jaack1/diploma-docker-app

## Ссылка на тестовое приложение и веб интерфейс Grafana с данными доступа.

Для доступности приложения извне в Helm Chart был добавлен манифест с ingress.

http://app.mylukomore.ru/

http://grafana.mylukomore.ru/
