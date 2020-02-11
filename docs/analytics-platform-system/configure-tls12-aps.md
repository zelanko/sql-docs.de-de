---
title: Konfigurieren von TLS 1,2
description: Empfehlung zum Konfigurieren von TLS 1,2 in APS
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/29/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 988cac765a596b541d128b0b6190f6f228d95ee7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401254"
---
# <a name="configure-tls-12-in-aps"></a>Konfigurieren von TLS 1,2 in APS

Um APS so zu sichern, dass nur TLS 1,2 verwendet wird, müssen Sie das andere Protokoll auf allen physischen und virtuellen Hosts explizit deaktivieren. Das Deaktivieren von Protokollen erfordert Änderungen an der Registrierungs Einstellung. Registrierungs Änderungen erfordern einen Neustart der virtuellen und physischen Hosts.

> [!WARNING]
> Dieser Abschnitt bzw. diese Methode oder Aufgabe enthält Schritte, in denen erläutert wird, wie die Registrierung geändert wird. Schwerwiegende Probleme können jedoch auftreten, wenn Sie die Registrierung falsch ändern, was zu Datenverlusten führen kann und eine Neuinstallation des Betriebssystems erforderlich ist. Es wird dringend empfohlen, die Registrierung zu sichern, bevor Sie Sie ändern. Auf diese Weise können Sie die Registrierung wiederherstellen, falls ein Problem auftritt. Weitere Informationen zum Sichern und Wiederherstellen der Registrierung erhalten Sie, indem Sie auf die folgende Artikelnummer klicken, um den Artikel in der Microsoft Knowledge Base anzuzeigen:<br>
[322756](https://support.microsoft.com/help/322756) sichern und Wiederherstellen der Registrierung in Windows

**Ier**
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
```

Legen Sie außerdem die folgenden Schlüssel auf den Client Computern fest, auf denen Tools wie APS SSIS-Ziel Adapter installiert sind.
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001 
```



