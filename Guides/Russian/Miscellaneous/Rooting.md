## Подготовка
- [KernelSU](https://github.com/tiann/KernelSU/releases) / [KernelSU Next](https://github.com/KernelSU-Next/KernelSU-Next/releases) / [Magisk](https://github.com/topjohnwu/Magisk/releases)
- [Payload dumper go](https://github.com/ssut/payload-dumper-go)
- Полноценный пакет обновления (Full ota) под ваше устройство (найти его можно [здесь](https://t.me/gt3neo5hub/175404))
- [Модифицированный OrangeFox recovery](https://github.com/realme-pineapple-devs/recovery_device_realme_pineapple/releases)
> [!CAUTION]
> Текущая версия модифицированного рекавери находится в разработке, а функционал, который данное рекавери предоставляет, в данный момент не полный. В будущем все утилиты будут добавлены, а ошибки - исправленны.

## Установко модифицированного рекавери
- Скачайте **.img** и **.zip** образы со страницы релиза рекавери.
- Перезагрузитесь в загрузчик (Bootloader), отключив свой девайс, и затем зажав кнопки **питание** и **громкость-** одновременно.
- Подключите устройство к компьютеру и пропишите следующую комманду в терминале:
```
$ fastboot flash recovery /path/to/recovery.img
```
- Перезагрузитесь в установленное рекавреи удобным для вас способом.
- В рекавери, включите ADB sideload, переподключите устройство и пропишите следующую комманду:
```
$ adb sideload /path/to/recovery-zip-package.zip
```
Устройство автоматически перезагрузится в полноценно установленное рекавери.

## Получение прав суперпользователя (Rooting)
### Извлечение образа init_boot
- Распакуйте файл payload.bin из архива полноценного пакета обновления (full ota), переместите его в папку с установленным и настроенным payload dumper go
- Введите следующие комманды для распаковки payload.bin, в зависимости от вашей ОС:
```
# Windows:
$ payload-dumper-go.exe /path/to/payload.bin

# Linux:
$ payload-dumper-go /path/to/payload.bin
```
- Копируйте образ init_boot из папки, в которую распаковался payload.bin (обычно она называется "extracted-...") на ваше устройство.
### KernelSU Next / KernelSU
KernelSU (Next) Может работать в двух режимах: [GKI](https://kernelsu.org/guide/installation.html#gki-mode) и [LKM](https://kernelsu.org/guide/installation.html#lkm-mode).

#### Режим GKI (Доступен для KernelSU и его Next форка)
- Со страницы релиза скачайте пакет AnyKernel3 с общим образом ядра, содержащим KernelSU (Next) (например: AnyKernel3-android14-6.1.99_2024-10.zip. Для нашего же устройства будут актуальны пакеты android14-6.1.XX).
- Перезагрузитесь в модифицированное рекавери, включите ADB sideload.
- Подключите устройство к компьютеру и введите следующую коммаду:
```
$ adb sideload /path/to/gki-package.zip
```
- Перезагрузите устройство в Android и всё! (не забудьте установить приложение для управление рут правами.)

#### Режим LKM
- Переместите извелеченный init_boot образ на своё устройство.
- Откройте приложение-менеджер для рута.
- Выберите опцию "выбрать файл" в предложенных вариантах установки, затем выберите init_boot в открывшемся файловом менеджере. Пропатчите образ.
- Move patched init_boot image to your computer, then reboot your device into bootloader, connect it to computer and type into terminal:
```
$ fastboot flash init_boot /path/to/patched-init-boot.img
```
Reboot your device into system and you are done!

### Magisk
Инструкция похожа с патчем [режима LKM для KernelSU](https://github.com/InternalHellhound/realme-bale-linwin-project/blob/main/Guides/Russian/Miscellaneous/Rooting.md#%D1%80%D0%B5%D0%B6%D0%B8%D0%BC-lkm-%D0%B4%D0%BE%D1%81%D1%82%D1%83%D0%BF%D0%B5%D0%BD-%D1%82%D0%BE%D0%BB%D1%8C%D0%BA%D0%BE-%D0%B4%D0%BB%D1%8F-kernelsu-%D1%82%D0%B0%D0%BA-%D0%BA%D0%B0%D0%BA-%D0%B2-%D0%B5%D0%B3%D0%BE-next-%D1%84%D0%BE%D1%80%D0%BA%D0%B5-%D0%BF%D0%BE%D0%B4%D0%B4%D0%B5%D1%80%D0%B6%D0%BA%D1%83-%D0%B4%D0%B0%D0%BD%D0%BD%D0%BE%D0%B3%D0%BE-%D1%80%D0%B5%D0%B6%D0%B8%D0%BC%D0%B0-%D0%BF%D1%80%D0%B5%D0%BA%D1%80%D0%B0%D1%82%D0%B8%D0%BB%D0%B8-%D1%81-%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D0%B8-107).
