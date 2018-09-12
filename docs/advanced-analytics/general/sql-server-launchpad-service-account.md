---
title: Konfiguration des SQL Server Launchpad-Dienstkontos | Microsoft-Dokumentation
description: So ändern Sie das SQL Server Launchpad-Dienstkonto für die Ausführung des externen Skripts für SQL Server verwendet werden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0afdb02c578de92bc91c5f47e973148136ebd919
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892879"
---
# <a name="sql-server-launchpad-service-configuration"></a>Konfiguration von SQL Server Launchpad-Diensts
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Eine Separate [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Dienst erstellt und für Datenbank-Engine-Instanz, die Sie haben auf die Integration von SQL Server Machine learning (R oder Python) hinzugefügt.

## <a name="service-account-configuration"></a>Konfiguration des Dienstkontos

Standardmäßig ist SQL Server Launchpad für die Ausführung unter konfiguriert **NT Service\MSSQLLaunchpad**, die mit allen erforderlichen Berechtigungen zum Ausführen externer Skripts bereitgestellt wird. Entfernen von Berechtigungen, die dieses Konto kann dazu führen Launchpad, die Fehler bei der starten oder für den Zugriff auf SQL Server-Instanz, in dem externe Skripts ausgeführt werden soll.

Berechtigung ist erforderlich, die für dieses Konto sind nachfolgend aufgeführt. Wenn Sie das Dienstkonto ändern, achten Sie darauf mit der **Local Security Policy** Anwendung diese Berechtigungen enthalten:

+ Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)
+ Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)
+ Anmelden als Dienst (SeServiceLogonRight)
+ Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)

Weitere Informationen zu erforderlichen Berechtigungen für das Ausführen von SQL Server-Diensten finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

<a name="bkmk_ChangingConfig"></a> 

## <a name="configuration-properties"></a>Konfigurationseigenschaften

1. Öffnen Sie den [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md). 

2. Mit der rechten Maustaste in SQL Server Launchpad, und wählen Sie **Eigenschaften**.

    + Um das Dienstkonto zu ändern, klicken Sie auf die **anmelden** Registerkarte.

    + Um die Anzahl von Benutzern zu erhöhen, klicken Sie auf die **erweitert** Registerkarte.

> [!Note]
> In frühen Versionen von SQL Server 2016 R Services, können Sie einige Eigenschaften des Diensts ändern, indem Sie die Bearbeitung der [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] Konfigurationsdatei. Diese Datei wird nicht mehr zum Ändern von Konfigurationen. SQL Server-Konfigurations-Manager ist der richtige Ansatz für Änderungen an der Dienstkonfiguration, wie z. B. das Dienstkonto und die Anzahl von Benutzern.

#### <a name="debug-settings"></a>Debug-Einstellungen

Einige Eigenschaften können nur geändert werden, mithilfe Launchpads-Konfigurationsdatei, die sich in selteneren Fällen, z. B. Debuggen hilfreich sein kann. Die Konfigurationsdatei wird erstellt, während der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einrichten und in der Standardeinstellung als nur-Text-Datei am folgenden Speicherort gespeichert: `<instance path>\binn\rlauncher.config`

Sie müssen Administrator auf dem Computer sein, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, um diese Datei ändern zu können. Für die Bearbeitung der Datei wird empfohlen, dass Sie eine Sicherungskopie erstellen, bevor Sie Änderungen speichern.

Die folgende Tabelle enthält die erweiterten Einstellungen für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], mit den zulässigen Werten. 

|**Einstellungsname**|**Typ**|**Beschreibung**|
|----|----|----|
|AUFTRAG\_BEREINIGUNG\_ON\_BEENDEN|Integer |Dies ist eine interne Einstellung – ändern Sie diesen Wert nicht. </br></br>Gibt an, ob es sich bei der temporären Arbeitsordner erstellt für jede externe Common Language Runtime-Sitzung bereinigt werden soll, nachdem die Sitzung abgeschlossen ist. Diese Einstellung ist beim Debuggen nützlich. </br></br>Unterstützte Werte sind **0** (deaktiviert) oder **1** (aktiviert). </br></br>Der Standardwert ist 1, die Bedeutung von Protokolldateien beim Beenden entfernt.|
|ABLAUFVERFOLGUNG\_EBENE|Integer |Konfiguriert den Ausführlichkeitsgrad der Ablaufverfolgung von MSSQLLAUNCHPAD zu Debugzwecken an. Dies wirkt sich die Ablaufverfolgungsdateien im Pfad durch die Einstellung LOG_DIRECTORY angegeben. </br></br>Unterstützte Werte sind: **1** (Fehler), **2** (Leistung), **3** (Warnung), **4** (Informationen). </br></br>Der Standardwert ist 1, d. h. nur Ausgabe von Warnungen.|

Alle Einstellungen haben die Form eines Schlüssel-Wert-Paars, bei dem jede Einstellung in einer separaten Zeile enthalten ist. Klicken Sie z. B., um das Level der Ablaufverfolgung zu ändern, hinzufügen die Zeile `Default: TRACE_LEVEL=4`.

## <a name="see-also"></a>Siehe auch

[Erweiterungsframework](../concepts/extensibility-framework.md)
