---
title: Konfiguration des SQL Server-Launchpad-Dienst Kontos
description: Vorgehensweise beim Ändern des SQL Server-Launchpad Dienst Kontos, das für die Ausführung externer Skripts auf SQL Server verwendet wird.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 5d01004fb54c0410acc372c5c66930f33bbd8856
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469998"
---
# <a name="sql-server-launchpad-service-configuration"></a>SQL Server-Launchpad Dienst Konfiguration
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Bei [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] handelt es sich um einen Dienst, der externe Skripts verwaltet und ausführt, ähnlich der Art, in der die Volltextindizierung und der Abfragedienst einen separaten Host zum Verarbeiten von voll Text Abfragen starten.

Weitere Informationen finden Sie in den Launchpad-Abschnitten unter [Erweiterbarkeits Architektur in SQL Server Machine Learning Services](../../advanced-analytics/concepts/extensibility-framework.md#launchpad) und [Sicherheitsübersicht für das Erweiterbarkeit Framework in SQL Server Machine Learning Services](../../advanced-analytics/concepts/security.md#launchpad).

## <a name="account-permissions"></a>Konto Berechtigungen

Standardmäßig ist SQL Server-Launchpad für die unter Verwendung von **NT service\mssqllaunchpad**konfiguriert, das mit allen erforderlichen Berechtigungen zum Ausführen externer Skripts bereitgestellt wird. Das Entfernen von Berechtigungen aus diesem Konto kann dazu führen, dass Launchpad nicht gestartet wird oder auf die SQL Server Instanz, auf der externe Skripts ausgeführt werden sollen, zugreifen kann.

Wenn Sie das Dienst Konto ändern, stellen Sie sicher, dass Sie die [Konsole "lokale Sicherheitsrichtlinie](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/how-to-configure-security-policy-settings)" verwenden.

Die erforderlichen Berechtigungen für dieses Konto sind in der folgenden Tabelle aufgeführt.

| Gruppenrichtlinien Einstellung | Konstanter Name |
|----------------------|---------------|
| [Anpassen von Speicher Kontingenten für einen Prozess](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/adjust-memory-quotas-for-a-process) | SeIncreaseQuotaPrivilege | 
| [Durchlauf Überprüfung umgehen](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/bypass-traverse-checking) | SeChangeNotifyPrivilege | 
| [Anmelden als Dienst](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/log-on-as-a-service) | SeServiceLogonRight | 
| [Ersetzen eines Tokens auf Prozessebene](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/replace-a-process-level-token) | SeAssignPrimaryTokenPrivilege | 

Weitere Informationen zu erforderlichen Berechtigungen für das Ausführen von SQL Server-Diensten finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

<a name="bkmk_ChangingConfig"></a> 

## <a name="configuration-properties"></a>Konfigurations Eigenschaften

In der Regel gibt es keinen Grund, die Dienst Konfiguration zu ändern. Zu den Eigenschaften, die geändert werden können, gehören das Dienst Konto, die Anzahl externer Prozesse (standardmäßig 20) oder die Richtlinie zum Zurücksetzen von Kenn Wörtern für workerkonten.

1. Öffnen Sie den [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md).

2. Klicken Sie unter SQL Server Dienste mit der rechten Maustaste auf SQL Server-Launchpad, und wählen Sie **Eigenschaften**aus.
  + Um das Dienst Konto zu ändern, klicken Sie auf die Registerkarte **Anmelden** .
  + Um die Anzahl der Benutzer zu erhöhen, klicken Sie auf die Registerkarte **erweitert** , und ändern Sie die Anzahl der **Sicherheits Kontexte**.

> [!Note]
> In frühen Versionen von SQL Server 2016 R-Diensten können Sie einige Eigenschaften des Diensts ändern, indem Sie [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] die Konfigurationsdatei bearbeiten. Diese Datei wird nicht mehr zum Ändern von Konfigurationen verwendet. SQL Server-Konfigurations-Manager ist der richtige Ansatz für Änderungen an der Dienst Konfiguration, wie z. b. das Dienst Konto und die Anzahl der Benutzer.

## <a name="debug-settings"></a>Debugeinstellungen

Einige Eigenschaften können nur mithilfe der Launchpad-Konfigurationsdatei geändert werden. Dies kann in begrenzten Fällen nützlich sein, z. b. beim Debuggen. Die Konfigurationsdatei wird während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setups erstellt und standardmäßig als einfache Textdatei in `<instance path>\binn\rlauncher.config`gespeichert.

Sie müssen Administrator auf dem Computer sein, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, um diese Datei ändern zu können. Für die Bearbeitung der Datei wird empfohlen, dass Sie eine Sicherungskopie erstellen, bevor Sie Änderungen speichern.

In der folgenden Tabelle werden die erweiterten Einstellungen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]für mit den zulässigen Werten aufgelistet.

|**Einstellungsname**|**Typ**|**Beschreibung**|
|----|----|----|
|AUFTRAGS\_BEREINIGUNG\_BEIM\_BEENDEN|Integer |Dies ist nur eine interne Einstellung. ändern Sie diesen Wert nicht. </br></br>Gibt an, ob der für jede externe Lauf Zeit Sitzung erstellte temporäre Arbeitsordner nach Abschluss der Sitzung bereinigt werden soll. Diese Einstellung ist beim Debuggen nützlich. </br></br>Unterstützte Werte sind **0** (deaktiviert) oder **1** (aktiviert). </br></br>Der Standardwert ist 1, was bedeutet, dass Protokolldateien beim Beenden entfernt werden.|
|ABLAUF\_VERFOLGUNGS EBENE|Integer |Konfiguriert den ausführlichkeits Grad der Ablauf Verfolgung von mssqllaunchpad zu Debuggingzwecken. Dies betrifft Ablauf Verfolgungs Dateien in dem Pfad, der durch die LOG_DIRECTORY-Einstellung angegeben wird. </br></br>Diese Werte werden unterstützt: **1** (Fehler), **2** (Leistung), **3** (Warnung), **4** (Informationen). </br></br>Der Standardwert ist 1, d. h. nur Ausgabefehler.|

Alle Einstellungen haben die Form eines Schlüssel-Wert-Paars, bei dem jede Einstellung in einer separaten Zeile enthalten ist. Wenn Sie z. b. die Ablauf Verfolgungs Ebene ändern möchten, fügen `Default: TRACE_LEVEL=4`Sie die Zeile hinzu.

<a name="bkmk_EnforcePolicy"></a>

## <a name="enforcing-password-policy"></a>Erzwingen der Kenn Wort Richtlinie

Wenn Ihre Organisation eine Richtlinie hat, die das regelmäßige Ändern von Kennwörtern erfordert, müssen Sie möglicherweise den Launchpad-Dienst zwingen, die verschlüsselten Kennwörter erneut zu generieren, die Launchpad für seine Workerkonten verwaltet.

Öffnen Sie den Bereich **Eigenschaften** für den Launchpad-Dienst in SQL Server Configuration Manager, klicken Sie auf **Erweitert**, und ändern Sie **Reset External Users Password** (Kennwörter externer Benutzer zurücksetzen) in **Yes** (Ja). Wenn Sie diese Änderung übernehmen, werden die Kennwörter sofort für alle Benutzerkonten erneut generiert. Zum Ausführen eines externen Skripts nach dieser Änderung müssen Sie den Launchpad-Dienst neu starten. zu diesem Zeitpunkt werden die neu generierten Kenn Wörter gelesen.

Sie können dieses Flag entweder manuell festlegen oder dazu ein Skript verwenden.

## <a name="next-steps"></a>Nächste Schritte

+ [Erweiterbarkeits Framework](../concepts/extensibility-framework.md)
+ [Sicherheitsübersicht](../concepts/security.md)
