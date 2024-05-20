---
title: "Как сбросить пароль администратора Windows Server"
description: "Из статьи вы узнаете, как сбросить пароль администратора на виртуальной машине Windows Server."
---

# Сбросить пароль администратора Windows Server

{% note warning %}

Если у вас нет агента сброса паролей, [установите](install.md) его.

{% endnote %}

При первом [подключении к ВМ по RDP](../vm-connect/rdp.md) нужно сбросить пароль администратора, установленный по умолчанию, и сгенерировать новый.

{% list tabs group=instructions %}

- Консоль управления {#console}

  1. В [консоли управления]({{link-console-main}}) выберите сервис **{{ compute-name }}**.
  1. Выберите нужную ВМ.
  1. Нажмите кнопку **Сбросить пароль**.
  1. В открывшемся окне нажмите кнопку **Сгенерировать пароль**.

{% endlist %}

{% note warning %}

Обязательно сохраните сгенерированный пароль. Он перестанет отображаться в консоли управления после того, как вы закроете окно.

{% endnote %}