---
title: Отзывы о телеметрии
description: Отправка отзыва о телеметрии в корпорацию Майкрософт для системы платформы аналитики.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 639eb4e9e5c531e154b9eb7f91165af365bc519f
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400363"
---
# <a name="send-telemetry-feedback-to-microsoft-for-analytics-platform-system"></a>Отправка отзывов телеметрии в корпорацию Майкрософт для платформы аналитики
В системе аналитики есть дополнительная функция телеметрии, которая отправляет данные консоли администрирования в корпорацию Майкрософт. 
  
> [!NOTE]  
> В этом выпуске Корпорация Майкрософт активно не отслеживает данные телеметрии. Данные собираются только в целях анализа.  
  
## <a name="privacy"></a><a name="privacy"></a>Конфиденциальность  
Чтобы обеспечить максимальную защиту конфиденциальности, ТД поставляется без включения телеметрии. Перед включением этой функции сначала ознакомьтесь с заявлением [о конфиденциальности Microsoft Analytics Platform System](https://go.microsoft.com/fwlink/?LinkId=400902). Чтобы принять участие в этой инструкции, выполните сценарий PowerShell, описанный ниже.  
  
## <a name="enable-telemetry"></a><a name="enable"></a>Включить телеметрию  
**Пересылка DNS:** Для отправки данных телеметрии в корпорацию Майкрософт требуется Системная платформа аналитики для подключения к Интернету через сервер пересылки DNS. Чтобы включить эту функцию, необходимо включить пересылку DNS на всех узлах и виртуальных машинах рабочей нагрузки. Вызовите `Enable-RemoteMonitoring` команду с `SetupDnsForwarder` параметром, чтобы правильно настроить пересылку DNS и включить телеметрию. Вызовите `Enable-RemoteMonitoring` команду без `SetupDnsForwarder` параметра, если пересылка DNS уже настроена и вы хотите включить только мониторинг пульса.  
  
> [!IMPORTANT]  
> При включении пересылки DNS подключение к Интернету открывается для всех виртуальных машин узлов и рабочих нагрузок.  
  
#### <a name="to-enable-feedback"></a>Включение обратной связи  
  
1.  Используя учетную запись администратора домена устройства, подключитесь к управляющему узлу (<strong>*appliance_domain*-CTL01</strong>) и откройте командную строку, используя учетные данные администратора Windows.  
  
2.  Перейдите в следующий каталог: `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100` .  
  
3.  Импорт модуля `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Для импорта необходимо использовать две точки в команде.  
  
    **Пример**.  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Вызовите `Enable-RemoteMonitoring` команду.  
  
    > [!NOTE]  
    > Сценарий предполагает, что подключение к Интернету работает правильно и не проверяет подключение к Интернету.  
  
    1.  При первом включении телеметрии используйте следующую команду, чтобы убедиться, что все серверы пересылки DNS настроены правильно. В этом примере замените IP-адрес перенаправления DNS на `xx.xx.xx.xx` IP-адрес сервера пересылки DNS в вашей среде.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring -SetupDnsForwarder -DnsForwarderIp xx.xx.xx.xx  
        ```  
  
    2.  Если серверы пересылки DNS уже настроены, например повторно включить ранее отключенную телеметрию, используйте следующую команду, чтобы включить телеметрию без настройки пересылки DNS.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring  
        ```  
  
5.  Вам будет предложено прочитать и подтвердить, что ТД будет получать сведения об устройстве. Появится ссылка на заявление о конфиденциальности APS, которое можно скопировать и вставить в любой браузер для просмотра.  
  
6.  Введите **Y** , чтобы принять участие в отзыве, или введите **N** , чтобы не принимать.  
  
7.  Если вы указали **Y** , будет выполнен ряд команд, которые будут включать данные телеметрии (и, при необходимости, DNS-сервер пересылки) на устройстве. Если вы видите ошибки или сведения, которые посчитают, что команда не прошла успешно, обратитесь в CSS за помощью.  
  
Если введено значение **N**, команды не будут выполняться, а функция не будет включена и больше ничего делать не нужно.  
  
Неважно, чтобы команда выполнялась `Enable-RemoteMonitoring` несколько раз. Если DNS-сервер пересылки уже настроен, вы получите предупреждающее сообщение, указывающее, что это так.  
  
## <a name="disable-telemetry"></a><a name="disable"></a>Отключить телеметрию  
При отключении телеметрии будут остановлены все операции, которые передают сведения о состоянии устройства в службу мониторинга APS в облаке.  
  
> [!IMPORTANT]  
> При выполнении этой операции не будет отключен сервер пересылки DNS или подключение к Интернету, которое может использоваться другими компонентами устройства.  
  
#### <a name="to-disable-telemetry"></a>Отключение телеметрии  
  
1.  Используя учетную запись администратора домена устройства, подключитесь к управляющему узлу (<strong>*appliance_domain*-CTL01</strong>) и откройте окно PowerShell с правами администратора.  
  
2.  Перейдите в следующий каталог: `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100` .  
  
3.  Импорт модуля `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Для импорта необходимо использовать две точки в команде.  
  
    **Пример**.  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Вызов `Disable-RemoteMonitoring` команды без параметров. Эта команда перестанет отправлять отзыв. (Это не повлияет на локальный мониторинг.) Однако команда не отключит сервер пересылки DNS и (или) отключает подключение к Интернету. Это необходимо сделать вручную после успешного отключения обратной связи.  
  
    **Пример**.  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Disable-RemoteMonitoring  
    ```  
  
Если вы видите ошибки или сведения, которые посчитают, что команда не прошла успешно, обратитесь в CSS за помощью.  
  
Неважно, чтобы команда выполнялась `Disable-RemoteMonitoring` несколько раз.  
  
## <a name="next-steps"></a>Дальнейшие действия
Дополнительные сведения см. в разделе:
- [Мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
- [Мониторинг устройства с помощью системных представлений &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
- [Мониторинг устройства с помощью системы System Center Operations Manager &#40;Analytics Platform&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
- [Используйте DNS-сервер пересылки для разрешения DNS-имен, не относящихся к устройствам, &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
  
