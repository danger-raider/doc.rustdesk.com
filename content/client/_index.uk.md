---
title: Клієнт RustDesk
description: "Встановлення й налаштування клієнта RustDesk у Windows, macOS, Linux, Android, iOS та Web. Дізнайтеся, як підключати пристрої, використовувати публічні або власні сервери та керувати налаштуваннями клієнта."
keywords: ["rustdesk client", "rustdesk download", "rustdesk installation", "rustdesk windows", "rustdesk mac", "rustdesk linux", "rustdesk android", "rustdesk ios", "rustdesk web client", "rustdesk client configuration"]
weight: 2
pre: "<b>1. </b>"
---

## Що таке клієнт RustDesk?
Клієнт RustDesk — це застосунок, який встановлюється на пристрої для початку або приймання сеансів віддаленого робочого столу через публічні сервери RustDesk або ваш власний RustDesk Server. У цьому посібнику описано, як завантажити правильну збірку, встановити її на кожній платформі, підключитися до іншого пристрою та налаштувати клієнт для роботи з RustDesk Server OSS або RustDesk Server Pro.

{{% notice note %}}
Посібники для платформ: [RustDesk для Linux](https://rustdesk.com/blog/rustdesk-for-linux) та [віддалене керування з Android та iOS](https://rustdesk.com/blog/rustdesk-remote-control-android-ios). Дивіться також [найкраще безкоштовне ПЗ для віддаленого робочого столу](https://rustdesk.com/blog/best-free-remote-desktop-software).
{{% /notice %}}

## Підтримувані платформи
- Microsoft Windows
- macOS
- Похідні Debian (Ubuntu ≥ 16, Linux Mint тощо)
- Похідні Red Hat (CentOS, Fedora ≥ 18, Rocky Linux тощо)
- Arch Linux/Manjaro
- openSUSE
- NixOS
- AppImage / Flatpak
- Android
- iOS (не може керуватися віддалено)
- Web

## Встановлення

### Windows
Завантажте exe-файл з GitHub і встановіть його.

Для тихого встановлення запустіть інсталятор exe з параметром `--silent-install`.

### macOS
Завантажте dmg-файл з GitHub. Докладнішу інформацію наведено на [сторінці macOS](https://rustdesk.com/docs/uk/client/mac/).

Відкрийте dmg-файл і перетягніть `RustDesk` до `Applications`.

Дозвольте запуск RustDesk.

Надайте запитані дозволи та виконайте підказки ліворуч у вікні RustDesk, щоб завершити налаштування.

### Linux
Нижче наведено інструкції зі встановлення для різних дистрибутивів Linux. Інсталятори доступні на GitHub або в репозиторіях відповідних дистрибутивів.

#### Похідні Debian

```sh
# проігноруйте некоректне повідомлення про використання диска
sudo apt install -fy ./rustdesk-<version>.deb
```

#### Похідні Red Hat

```sh
sudo yum localinstall ./rustdesk-<version>.rpm
```

#### Arch Linux/Manjaro

```sh
sudo pacman -U ./rustdesk-<version>.pkg.tar.zst
```

#### openSUSE (≥ Leap 15.0)

```sh
sudo zypper install --allow-unsigned-rpm ./rustdesk-<version>-suse.rpm
```

#### Nix / NixOS (≥ 22.05)

Тимчасово відкрийте shell, у якому `rustdesk` буде готовий до запуску:

```sh
nix shell nixpkgs#rustdesk
```

Встановіть у профіль поточного користувача:

```sh
nix profile install nixpkgs#rustdesk
```

Щоб встановити RustDesk системно в NixOS, після редагування `configuration.nix` виконайте `nixos-rebuild switch --flake /etc/nixos`:

```
  environment.systemPackages = with pkgs; [
    ...
    rustdesk
  ];
```

### Android
Встановіть apk з нашого GitHub. Докладнішу інформацію наведено на [сторінці Android](https://rustdesk.com/docs/uk/client/android/).

### iOS (iPhone, iPad)
Завантажте застосунок з [App Store](https://apps.apple.com/us/app/rustdesk-remote-desktop/id1581225015).

## Використання
Після встановлення або запуску як портативного виконуваного файла RustDesk підключиться до публічних серверів. Унизу з'явиться повідомлення (1) «Ready, For faster connection, please set up your own server». У верхньому лівому куті буде показано (2) ваш ID, (3) одноразовий пароль, а праворуч — (4) поле для підключення до іншого комп'ютера, якщо ви знаєте його ID.

![](/docs/en/client/images/client.png)

Щоб відкрити налаштування, натисніть кнопку меню (5) [ &#8942; ] праворуч від ID.

У розділі Settings доступні:
- General — керування службою, тема, апаратний кодек, аудіо, запис і мова
- Security — дозволи для користувача, який отримує керування, параметри пароля, можливість змінити ID та розширені налаштування безпеки
- Network — налаштування власного сервера та проксі
- Display — параметри відображення для віддалених сеансів та інші типові параметри, синхронізація буфера обміну тощо
- Account — використовується разом із Pro Server для входу в API
- About — інформація про програмне забезпечення

## Налаштування RustDesk
RustDesk можна налаштувати кількома способами.

Найпростіший спосіб — використати RustDesk Server Pro: у ньому можна отримати зашифрований рядок конфігурації та імпортувати налаштування за допомогою параметра `--config`. Для цього:
1. Відкрийте командний рядок у вашій ОС у каталозі, де встановлено RustDesk, наприклад `C:\Program Files\RustDesk` у Windows або `/usr/bin` у Linux.
2. Виконайте команду `rustdesk.exe --config your-encrypted-string`, наприклад `rustdesk.exe --config 9JSPSvJzNrBDasJjNSdXOVVBlERDlleoNWZzIHcOJiOikXZr8mcw5yazVGZ0NXdy5CdyciojI0N3boJye`.

Клієнт також можна налаштувати вручну:
1. Відкрийте Settings.
2. Виберіть Network.
3. Натисніть Unlock Network Settings.
4. Введіть ID, Relay, API (якщо використовується Pro Server) та ваш ключ.

![](/docs/en/client/images/network-settings.png)

Якщо клієнт налаштовано вручну, можна отримати файл `RustDesk2.toml` у каталозі користувача та імпортувати його за допомогою `--import-config` аналогічно до наведеного вище прикладу.

## Параметри командного рядка
- `--password` — встановлення постійного пароля.
- `--get-id` — отримання ID.
- `--set-id` — встановлення ID; зверніть увагу, що ID має починатися з літери.
- `--silent-install` — тихе встановлення RustDesk у Windows.

Додаткові розширені параметри можна знайти [тут](https://github.com/rustdesk/rustdesk/blob/bdc5cded221af9697eb29aa30babce75e987fcc9/src/core_main.rs#L242).

{{% children depth="3" showhidden="true" %}}
