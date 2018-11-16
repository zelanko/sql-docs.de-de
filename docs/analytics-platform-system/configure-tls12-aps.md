---
title: 'Konfigurieren von TLS 1.2 in Analytics Platform System | Microsoft-Dokumentation '
description: Empfehlung zur Konfiguration von TLS 1.2 in APS
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/29/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 15bee3f68bf922ec9220c9ac570e5bd372f47483
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51697858"
---
# <a name="configure-tls-12-in-aps"></a>Konfigurieren von TLS 1.2 in APS

Zum Sichern von installiert wird, um nur TLS 1.2 zu verwenden, müssen Sie andere Protokoll auf allen physischen und virtuellen Hosts explizit zu deaktivieren. Deaktivieren der Protokolle erfordern registrierungsänderungen für die Einstellung.

> [!WARNING]
> Dieser Abschnitt bzw. diese Methode oder Aufgabe enthält Schritte, in denen erläutert wird, wie die Registrierung geändert wird. Allerdings können schwerwiegende Probleme auftreten, wenn Sie die Registrierung ändern, nicht ordnungsgemäß, die dazu führen, dass Daten verloren gehen können, und benötigen die Neuinstallation des Betriebssystems. Wir empfehlen dringend sichern Sie die Registrierung, bevor Sie sie ändern. Auf diese Weise können Sie die Registrierung wiederherstellen, falls ein Problem auftritt. Weitere Informationen zum Sichern und Wiederherstellen der Registrierung klicken Sie auf die folgende Artikelnummer klicken, um den entsprechenden Artikel in der Microsoft Knowledge Base anzeigen:<br>
[322756](https://support.microsoft.com/help/322756) wie Sichern und Wiederherstellen der Registrierung in Windows

**Deaktivieren:**
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

Auch legen Sie die folgenden Schlüssel auf dem Client Computer, in dem Tools wie APS SSIS-Zieladapter installiert werden.
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001 
```



