---
title: Protokolle für MSSQLSERVER-Eigenschaften (Registerkarte „Erweitert“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/24/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: abd5ca68-825f-4c07-b27c-3b3a79d03d74
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: bc5ee796addb8c77170de2e3166aefb74d046ad1
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044616"
---
# <a name="protocols-for-mssqlserver-properties-advanced-tab"></a>Protokolle für MSSQLSERVER-Eigenschaften (Registerkarte "Erweitert")

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Mit der Registerkarte **Erweitert** im Dialogfeld **Protokolle für MSSQLSERVER-Eigenschaften** können Sie für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]**Erweiterter Schutz für die Authentifizierung** konfigurieren. **Erweiterter Schutz** ist eine Funktion der vom Betriebssystem implementierten Netzwerkkomponenten. **Erweiterter Schutz** ist in Windows 7 und Windows Server 2008 R2 verfügbar und in Service Packs für ältere Betriebssysteme enthalten. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist sicherer, wenn Verbindungen möglichst mithilfe des **erweiterten Schutzes**hergestellt werden. Einige Funktionen von **Erweiterter Schutz** setzen die Auswahl von **Verschlüsselung erzwingen** auf der Registerkarte **Flags** voraus.

> [!IMPORTANT]  
> **Erweiterter Schutz** ist in Windows standardmäßig nicht aktiviert. Informationen zum Aktivieren von **erweiterter Schutz**, finden Sie in der folgenden:
> - [Erweiterter Schutz von Windows \<ExtendedProtection\>](https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/windowsauthentication/extendedprotection/)
> - [Erweiterter Schutz für die Authentifizierung](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/extended-protection-for-authentication-overview)

Weitere Informationen zum Konfigurieren anderer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste und eine vollständige Beschreibung von **Erweiterter Schutz**finden Sie auf [Microsoft.com](https://go.microsoft.com/fwlink/?LinkId=177752).

**Erweiterter Schutz** wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ab [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]vollständig unterstützt. Für andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clientanbieter wird **Erweiterter Schutz** derzeit nicht unterstützt.

## <a name="options"></a>enthalten

### <a name="extended-protection"></a>wird von

Es gibt drei mögliche Werte:  

- **Off**: Bedeutet, dass **erweiterter Schutz** ist deaktiviert. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz akzeptiert Verbindungen von jedem beliebigen Client, unabhängig davon, ob er geschützt ist oder nicht. **Aus** ist mit älteren und nicht gepatchten Betriebssystemen kompatibel, bietet aber weniger Sicherheit. Verwenden Sie diese Einstellung nur, wenn Sie wissen, dass die Clientbetriebssysteme keinen erweiterten Schutz unterstützen.

- **Zulässig**: Bedeutet, dass **Erweiterter Schutz** für Verbindungen von Betriebssystemen vorausgesetzt wird, die die Funktion **Erweiterter Schutz** unterstützen. Verbindungen von ungeschützten Clientanwendungen, die auf geschützten Clientbetriebssystemen ausgeführt werden, werden abgelehnt. **Erweiterter Schutz** wird für Verbindungen von ungeschützten Betriebssystemen ignoriert. Diese Einstellung ist sicherer als **Aus**, bietet jedoch nicht die höchste Sicherheit. Verwenden Sie diese Einstellung in gemischten Umgebungen, in denen einige Betriebssysteme oder Anwendungen die Funktion **Erweiterter Schutz** unterstützen, andere jedoch nicht.

- **Erforderliche**: bedeutet, dass für eine Verbindung akzeptiert wird, sie aus einer geschützten Anwendung unter einem Betriebssystem geschützt werden muss. Diese Einstellung ist die sicherste der drei Optionen. Verbindungen von Betriebssystemen, die nicht unterstützen, aber **erweiterter Schutz** ist nicht möglich für die Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

### <a name="accepted-ntlm-spns"></a>Akzeptierte NTLM-SPNs

Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von mehr als eine NTLM Dienstprinzipalnamen (SPN) identifiziert werden können. Sie Liste der SPNs als eine Reihe von Zeichenfolgen, die durch Semikolons getrennt ein. Der Wert **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com**zeigt beispielsweise an, dass Clients, die versuchen, eine Verbindung mit SPNs mit dem Namen **MSSQLSvc/HOST1.Contoso.com** oder **MSSQLSvc/HOST2.Contoso.com** herzustellen, zulässig sind. Die maximale Länge der Variablen beträgt 2048 Zeichen.

## <a name="see-also"></a>Weitere Informationen

[Erweiterter Schutz für die Authentifizierung mit Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)

