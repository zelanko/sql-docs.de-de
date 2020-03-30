---
title: Launchpad-Kontokonfiguration
description: Ändern des SQL Server-Launchpad-Dienstkontos, das für die externe Skriptausführung in SQL Server verwendet wird.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1f05181e1a3069ec56f079751e43bd739424ce92
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "79285994"
---
# <a name="sql-server-launchpad-service-configuration"></a>Dienstkonfiguration von SQL Server-Launchpad
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] ist ein Dienst, der die Ausführung externer Skripts verwaltet und unterstützt, ganz ähnlich wie die Volltextindizierung und der Abfragedienst einen separaten Host für die Verarbeitung von Volltextabfragen starten.

Weitere Informationen finden Sie in den Launchpad-Abschnitten unter [Erweiterbarkeitsarchitektur in SQL Server-Machine Learning Services](../../advanced-analytics/concepts/extensibility-framework.md#launchpad) und [Sicherheitsübersicht für das Erweiterbarkeitsframework in SQL Server-Machine Learning Services](../../advanced-analytics/concepts/security.md#launchpad).

## <a name="account-permissions"></a>Kontoberechtigungen

SQL Server-Launchpad ist standardmäßig so konfiguriert, dass es unter dem Konto **NT Service\MSSQLLaunchpad** ausgeführt wird, das mit allen erforderlichen Berechtigungen für das Ausführen externer Skripts bereitgestellt wird. Das Entfernen von Berechtigungen aus diesem Konto kann dazu führen, dass Launchpad nicht gestartet wird oder nicht auf die SQL Server-Instanz zugreifen kann, auf der externe Skripts ausgeführt werden sollen.

Wenn Sie das Dienstkonto ändern, achten Sie darauf, dass Sie die [Konsole der lokalen Sicherheitsrichtlinie](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/how-to-configure-security-policy-settings) verwenden.

Die erforderlichen Berechtigungen für dieses Konto sind in der folgenden Tabelle aufgeführt.

| Gruppenrichtlinieneinstellung | Konstantenname |
|----------------------|---------------|
| [Anpassen von Speicherkontingenten für einen Prozess](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/adjust-memory-quotas-for-a-process) | SeIncreaseQuotaPrivilege | 
| [Umgehen der Traversierungsüberprüfung](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/bypass-traverse-checking) | SeChangeNotifyPrivilege | 
| [Anmelden als Dienst](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/log-on-as-a-service) | SeServiceLogonRight | 
| [Ersetzen eines Tokens auf Prozessebene](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/replace-a-process-level-token) | SeAssignPrimaryTokenPrivilege | 

Weitere Informationen zu erforderlichen Berechtigungen für das Ausführen von SQL Server-Diensten finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

<a name="bkmk_ChangingConfig"></a> 

## <a name="configuration-properties"></a>Konfigurationseigenschaften

In der Regel gibt es keinen Grund, die Dienstkonfiguration zu ändern. Zu den Eigenschaften, die geändert werden können, gehören das Dienstkonto, die Anzahl externer Prozesse (Standard: 20) oder die Richtlinie zum Zurücksetzen von Kennwörtern für Geschäftskonten.

1. Öffnen Sie den [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md).

2. Klicken Sie unter „SQL Server-Dienste“ mit der rechten Maustaste auf „SQL Server-Launchpad“, und wählen Sie **Eigenschaften** aus.
  + Klicken Sie auf die Registerkarte **Anmelden**, um das Dienstkonto zu ändern.
  + Wenn Sie die Anzahl von Benutzern erhöhen möchten, klicken Sie auf die Registerkarte **Erweitert**, und ändern Sie die **Anzahl von Sicherheitskontexten**.

> [!Note]
> In frühen Versionen von SQL Server 2016 R Services können Sie einige Eigenschaften des Diensts ändern, indem Sie die [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]-Konfigurationsdatei bearbeiten. Diese Datei wird nicht mehr zum Ändern von Konfigurationen verwendet. SQL Server-Konfigurations-Manager ist der richtige Ansatz für Änderungen an der Dienstkonfiguration, z. B. am Dienstkonto und der Anzahl von Benutzern.

## <a name="debug-settings"></a>Debug-Einstellungen

Einige Eigenschaften können nur mithilfe der Launchpad-Konfigurationsdatei geändert werden. Dies kann in begrenzten Fällen nützlich sein, z. B. beim Debuggen. Die Konfigurationsdatei wird während des Setups von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingerichtet und standardmäßig als Nur-Text-Datei in `<instance path>\binn\rlauncher.config` gespeichert.

Sie müssen Administrator auf dem Computer sein, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, um diese Datei ändern zu können. Für die Bearbeitung der Datei wird empfohlen, dass Sie eine Sicherungskopie erstellen, bevor Sie Änderungen speichern.

Die folgende Tabelle führt die erweiterten Einstellungen für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit den zulässigen Werten auf.

|**Einstellungsname**|**Typ**|**Beschreibung**|
|----|----|----|
|JOB\_CLEANUP\_ON\_EXIT|Integer |Dies ist eine interne Einstellung – ändern Sie diesen Wert nicht. </br></br>Dieser gibt an, ob der für jede externe Runtime-Sitzung erstellte temporäre Arbeitsordner nach Abschluss der Sitzung bereinigt werden soll. Diese Einstellung ist beim Debuggen nützlich. </br></br>Unterstützte Werte sind **0** (Deaktiviert) oder **1** (Aktiviert). </br></br>Der Standardwert ist 1. Das bedeutet, dass Protokolldateien beim Beenden entfernt werden.|
|TRACE\_LEVEL|Integer |Konfiguriert den Ausführlichkeitsgrad von MSSQLLAUNCHPAD zu Debugzwecken. Dies wirkt sich auf Ablaufverfolgungsdateien in dem Pfad aus, der in der „LOG_DIRECTORY“-Einstellung angegeben ist. </br></br>Diese Werte werden unterstützt: **1** (Fehler), **2** (Leistung), **3** (Warnung), **4** (Information). </br></br>Der Standardwert ist 1, d. h. nur Ausgabefehler.|

Alle Einstellungen haben die Form eines Schlüssel-Wert-Paars, bei dem jede Einstellung in einer separaten Zeile enthalten ist. Wenn Sie z. B. die Ablaufverfolgungsebene ändern möchten, fügen Sie die Zeile `Default: TRACE_LEVEL=4` hinzu.

<a name="bkmk_EnforcePolicy"></a>

## <a name="enforcing-password-policy"></a>Erzwingen der Kennwortrichtlinie

Wenn Ihre Organisation eine Richtlinie hat, die das regelmäßige Ändern von Kennwörtern erfordert, müssen Sie möglicherweise den Launchpad-Dienst zwingen, die verschlüsselten Kennwörter erneut zu generieren, die Launchpad für seine Workerkonten verwaltet.

Öffnen Sie den Bereich **Eigenschaften** für den Launchpad-Dienst in SQL Server Configuration Manager, klicken Sie auf **Erweitert**, und ändern Sie **Reset External Users Password** (Kennwörter externer Benutzer zurücksetzen) in **Yes** (Ja). Wenn Sie diese Änderung übernehmen, werden die Kennwörter sofort für alle Benutzerkonten erneut generiert. Sie müssen den Launchpad-Dienst neu starten, um nach dieser Änderung ein externes Skript verwenden zu können; dann werden auch die neu generierten Kennwörter gelesen.

Sie können dieses Flag entweder manuell festlegen oder dazu ein Skript verwenden.

## <a name="next-steps"></a>Nächste Schritte

+ [Erweiterbarkeitsframework](../concepts/extensibility-framework.md)
+ [Sicherheitsübersicht](../concepts/security.md)
