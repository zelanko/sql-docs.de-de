---
description: Verwalten von Ereignissen
title: Verwalten von Ereignissen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- event-triggered jobs [SQL Server]
- forwarding events [SQL Server]
- alerts [SQL Server], forwarded events
- alerts [SQL Server], management servers
- SQL Server Agent alerts, management servers
ms.assetid: 8f4ee7f5-80df-49fd-b2b8-d020e04b6e1b
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 28b554a05c8ffae76d643b3da3bf6a178691a53c
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97466441"
---
# <a name="manage-events"></a>Verwalten von Ereignissen
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Sie können an eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle Ereignismeldungen weiterleiten, die einen bestimmten Fehlerschweregrad aufweisen oder überschreiten. Dies wird als *Ereignisweiterleitung* bezeichnet. Der Weiterleitungsserver ist ein dedizierter Server, bei dem es sich auch um einen Masterserver handeln kann. Durch die Ereignisweiterleitung können Sie die Warnungsverwaltung für eine Gruppe von Servern zentralisieren und so die Arbeitsauslastung stark belasteter Server reduzieren.  
  
Wenn ein Server Ereignisse für eine Gruppe anderer Server empfängt, wird dieser Server als *Warnungsverwaltungsserver* bezeichnet. In einer Multiserverumgebung bestimmen Sie den Masterserver zum Warnungsverwaltungsserver.  
  
## <a name="advantages-of-using-an-alerts-management-server"></a>Vorteile der Verwendung eines Warnungsverwaltungsservers  
Das Einrichten eines Warnungsverwaltungsservers hat u. a. folgende Vorteile:  
  
-   **Zentralisierung**. Die zentralisierte Steuerung und eine zusammenfassende Ansicht der Ereignisse mehrerer Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind von einem einzigen Server aus möglich.  
  
-   **Skalierbarkeit** Viele physische Server können als ein einziger logischer Server verwaltet werden. Sie können nach Bedarf Server zur Gruppe der physischen Server hinzufügen oder Server aus dieser Gruppe entfernen.  
  
-   **Effizienz**. Der Konfigurationsaufwand wird reduziert, da Warnungen und Operatoren nur einmal definiert werden müssen.  
  
## <a name="disadvantages-of-using-an-alerts-management-server"></a>Nachteile der Verwendung eines Warnungsverwaltungsservers  
Das Einrichten eines Warnungsverwaltungsservers hat u. a. folgende Nachteile:  
  
-   **Erhöhter Datenverkehr**. Das Weiterleiten von Ereignissen an einen Warnungsverwaltungsserver kann den Netzwerkverkehr erhöhen. Diese Erhöhung kann durch Beschränken der Ereignisweiterleitung auf Ereignisse, die einen bestimmten Schweregrad überschreiten, verringert werden.  
  
-   **Einzelne Fehlerquelle**. Wenn der Warnungsverwaltungsserver offline geschaltet wird, werden keine Warnungen für Ereignisse auf der verwalteten Servergruppe ausgegeben.  
  
-   **Serverauslastung**. Das Behandeln von Warnungen für die weitergeleiteten Ereignisse verursacht eine erhöhte Verarbeitungsauslastung des Warnungsverwaltungsservers.  
  
## <a name="guidelines-for-using-an-alerts-management-server"></a>Richtlinien für das Verwenden eines Warnungsverwaltungsservers  
Beachten Sie beim Konfigurieren eines Warnungsverwaltungsservers folgende Richtlinien:  
  
-   Zum Empfangen weitergeleiteter Ereignisse muss der Warnungsverwaltungsserver eine Standardinstanz von SQL Server sein.  
  
-   Vermeiden Sie es, auf dem Warnungsverwaltungsserver Anwendungen auszuführen, die störanfällig sind oder das System stark beanspruchen.  
  
-   Ziehen Sie den Netzwerkverkehr in Betracht, der entsteht, wenn Sie mehrere Server für die Verwendung desselben Warnungsverwaltungsservers konfigurieren. Reduzieren Sie bei Überlastung die Anzahl der Server, die einen bestimmten Warnungsverwaltungsserver verwenden.  
  
    Die Server, die in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] registriert sind, stellen die Liste der verfügbaren Server dar, die von diesem Server als Warnungsweiterleitungsserver ausgewählt werden können.  
  
-   Definieren Sie Warnungen, die eine serverspezifische Antwort erfordern, auf der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , statt sie an den Warnungsverwaltungsserver weiterzuleiten.  
  
    Für den Warnungsverwaltungsserver bilden alle an ihn weiterleitenden Server eine logische Einheit. So antwortet ein Warnungsverwaltungsserver auf dieselbe Art auf ein 605-Ereignis von Server A wie auf ein 605-Ereignis von Server B.  
  
-   Nach dem Konfigurieren des Warnungssystems sollten Sie das Microsoft Windows-Anwendungsprotokoll auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Ereignisse hin überprüfen.  
  
    Fehlerbedingungen, die von der Warnungs-Engine erkannt werden, werden mit dem Quellnamen "SQL Server-Agent" in das lokale Windows-Anwendungsprotokoll geschrieben. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent beispielsweise eine E-Mail-Benachrichtigung nicht wie definiert senden kann, wird ein Ereignis im Anwendungsprotokoll protokolliert.  
  
Tritt nach dem Deaktivieren einer lokal definierten Warnung ein Ereignis auf, das diese Warnung ausgelöst hätte, wird dieses Ereignis an den Warnungsverwaltungsserver weitergeleitet (sofern die Bedingung für die Warnungsweiterleitung erfüllt wird). Die Weiterleitung ermöglicht es, dass lokale Überschreibungen (lokal definierte Warnungen, die auch auf dem Warnungsverwaltungsserver definiert sind) nach Bedarf des Benutzers am lokalen Standort aktiviert und deaktiviert werden können. Sie können auch anfordern, dass Ereignisse immer weitergeleitet werden, selbst wenn sie auch von lokalen Warnungen behandelt werden.  
  
Beim Verwalten von Ereignissen in einer Multiserverumgebung fallen die folgenden allgemeinen Aufgaben an:  
  
**So bestimmen Sie einen Server zum Warnungsverwaltungsserver**  
  
-   [SQL Server Management Studio](../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md)  
  
**So definieren Sie die Antwort auf eine Warnung**  
  
-   [SQL Server Management Studio](../../ssms/agent/define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)  
  
## <a name="running-event-triggered-jobs"></a>Ausführen von ereignisgesteuerten Aufträgen  
Sie können einen Auftrag so definieren, dass er als Antwort auf eine Warnung ausgeführt werden soll. Sie können beispielsweise einen Auftrag ausführen, der ein von einer Warnung erkanntes Problem behebt oder weiter diagnostiziert.  
  
> [!NOTE]  
> Da ein Auftrag ein Ereignis auslösen kann, sollten Sie darauf achten, keine rekursive Schleife aus Warnungen und Aufträgen zu erstellen.  
  
## <a name="see-also"></a>Weitere Informationen  
[sp_add_notification (Transact-SQL)](../../relational-databases/system-compatibility-views/sys-sysmessages-transact-sql.md)  
