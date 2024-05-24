# Обновление коробки для стенда

## Инструкция по работе с Docker-файлом и установке компонентов

### Скачивание репозитория

Скачайте репозиторий локально:
```bash
git clone https://gitlab-dev.ispsystem.net/team/vm/box.git
cd box
```

### Создание новой ветки

Создайте новую ветку от ветки `master`:
```bash
git checkout -b my_feature_branch
```

### Редактирование Docker-файла

В скачанном репозитории найдите файл `Dockerfile` и откройте его для редактирования:
```bash
vi Dockerfile
```
*Либо же через редактор текста/кода*.

![Dockerfile](https://sun9-34.userapi.com/impg/OCc-ygEzezwA-NsOqOwrO9X3Ski27KlGrRsvRA/FTcfiwPA3b4.jpg?size=748x529&quality=95&sign=c8be3718b1600e1bcef4c54c1ccc60f3&type=album)


### Указание версий компонентов

В файле будут строки, определяющие версии компонентов. Найдите строки, начинающиеся с `ARG VERSION_`, и укажите необходимые версии компонентов для вашей сборки. Получить актуальные версии можно в соответствующих репозиториях.

### Сохранение изменений и отправка в репозиторий

Сохраните изменения в `Dockerfile` и зафиксируйте их:
```bash
git add Dockerfile
git commit -m "Update versions for the box"
```

Отправьте изменения в удаленный репозиторий:
```bash
git push origin my_feature_branch
```

### Создание чернового Merge Request

Создайте черновой Merge Request (MR) в ветку `master` через интерфейс GitLab. Дождитесь завершения всех пайплайнов:

![pipelines](https://sun9-9.userapi.com/impg/gUB9gT2QVFlieoU1Q1vgtMpLnoqisJo-yKJLUQ/HIlFylgMW3U.jpg?size=1024x225&quality=95&sign=cee48d11740a102c88d37f01f4e0eae8&type=album)

### Обработка ошибок

Если пайплайны завершились с ошибкой, кликните по иконке пайплайна, чтобы выяснить причину ошибки. Исправьте ошибки в `Dockerfile`, повторите шаги выше:

![pipelines_err](https://sun9-46.userapi.com/impg/N1JTrHsdFasjJEy9qmn2gGME0qcGE1P4C9Z9Ww/tlJq5SK-_8M.jpg?size=1015x118&quality=95&sign=46339b6afc92c32ac68b5bd0acef094b&type=album)

![Лог ошибок](https://sun9-9.userapi.com/impg/h9wqvLlqKo_aLmIrGCEwHzvCdGB2k47yMDbYhA/qCBhDPezMNQ.jpg?size=1024x1181&quality=95&sign=2fff4f10f65a773d4c7856112ef5b75a&type=album)

### Обновление стенда

Подключитесь к вашей виртуальной машине через SSH:
```bash
ssh root@vm-ip-address
```

Перейдите в папку `vm` и выполните команду для обновления:
```bash
cd ./vm
REPOSITORY_URL=http://intrepo.download.ispsystem.com/6/vm/branch/my_feature_branch/ vm update
```
!**где** `my_feature_branch` - **название ветки, из которой будет скачана коробка.**

Дождитесь завершения установки компонентов на стенд.

### Завершение

Поздравляю, вы великолепны!

---

Этот процесс описывает шаги для изменения версий компонентов в Docker-файле, создания и тестирования новых сборок, и обновления стенда. Убедитесь, что указанные версии компонентов корректны, чтобы избежать ошибок при сборке и установке.
