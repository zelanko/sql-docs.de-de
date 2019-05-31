---
title: Identität und Zugriffssteuerung (Replikation) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- access controls [SQL Server replication]
- security [SQL Server replication], identity and access control
- authentication [SQL Server replication]
- identity [Replication]
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c43cd13760808822b2c0332584799383eab5e39
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64776258"
---
# <a name="identity-and-access-control-replication"></a>Identität und Zugriffssteuerung (Replikation)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Als Authentifizierung wird der Vorgang bezeichnet, bei dem eine Entität (in diesem Kontext normalerweise ein Computer) überprüft, dass eine andere Entität, die auch als *Prinzipal*bezeichnet wird (normalerweise ein anderer Computer oder Benutzer), tatsächlich das ist, was sie vorgibt. Als Autorisierung wird der Vorgang bezeichnet, bei dem einem authentifizierten Prinzipal Zugriff auf Ressourcen gewährt wird, beispielsweise auf eine Datei in einem Dateisystem oder eine Tabelle in einer Datenbank.  
  
 Für die Replikationssicherheit wird mithilfe von Authentifizierung und Autorisierung der Zugriff auf replizierte Datenbankobjekte sowie auf die Computer und Agents gesteuert, die in die Replikationsverarbeitung involviert sind. Hierzu werden drei Mechanismen herangezogen:  
  
-   Agentsicherheit  
  
     Das Sicherheitsmodell des Replikations-Agents ermöglicht die präzise Steuerung der Konten, unter denen Replikations-Agents ausgeführt werden und Verbindungen herstellen. Ausführliche Informationen zum agentbezogenen Sicherheitsmodell finden Sie unter [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md). 
  
-   Verwaltungsrollen  
  
     Stellen Sie sicher, dass für Replikationsinstallation, -wartung und -verarbeitung die richtigen Server- und Datenbankrollen verwendet werden. Weitere Informationen finden Sie unter [Security Role Requirements for Replication](../../../relational-databases/replication/security/security-role-requirements-for-replication.md).  
  
-   Veröffentlichungszugriffsliste (Publication Access List, PAL)  
  
     Gewähren Sie den Zugriff auf Veröffentlichungen über die PAL. Die PAL funktioniert ähnlich wie eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Zugriffssteuerungsliste. Wenn ein Abonnent eine Verbindung mit dem Verleger oder Verteiler herstellt und den Zugriff auf eine Veröffentlichung anfordert, werden die vom Agent übermittelten Authentifizierungsinformationen anhand der PAL überprüft. Weitere Informationen und bewährte Methoden hinsichtlich der PAL finden Sie unter [Sichern des Verlegers](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
## <a name="filtering-published-data"></a>Filtern von veröffentlichten Daten  
 Neben der Verwendung von Authentifizierung und Autorisierung zur Steuerung des Zugriffs auf replizierte Daten und Objekte bietet die Replikation zwei Optionen, mit denen gesteuert werden kann, welche Daten auf einem Abonnenten zur Verfügung stehen: die Filterung von Spalten und die Filterung von Zeilen. Weitere Informationen zur Filterung finden Sie unter [Filtern von veröffentlichten Daten](../../../relational-databases/replication/publish/filter-published-data.md).  
  
 Bei der Definition eines Artikels können Sie lediglich die Spalten veröffentlichen, die für die Veröffentlichung relevant sind, und diejenigen auslassen, die nicht relevant sind oder vertrauliche Daten enthalten. Wenn Sie beispielsweise die **Customer** -Tabelle aus der Adventure Works-Datenbank für Vertriebsmitarbeiter im Außendienst veröffentlichen, können Sie die **AnnualSales** -Spalte auslassen, die möglicherweise nur für leitende Mitarbeiter im Unternehmen relevant ist.  
  
 Durch das Filtern von veröffentlichten Daten können Sie den Zugriff auf Daten einschränken und die Daten angeben, die auf dem Abonnenten zur Verfügung stehen. Sie können beispielsweise die **Customer** -Tabelle so filtern, dass Geschäftspartner nur die Informationen zu den Kunden erhalten, deren **ShareInfo** -Spalte den Wert "yes" aufweist. Im Fall von Mergereplikationen gelten besondere Sicherheitsüberlegungen, wenn Sie einen parametrisierten Filter verwenden, der HOST_NAME() einschließt. Weitere Informationen finden Sie im Abschnitt über das Filtern mit HOST_NAME() unter [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  

## <a name="manage-logins-and-passwords-in-replication"></a>Verwalten von Anmeldeinformationen und Kennwörtern bei der Replikation
Geben Sie bei der Replikationskonfiguration Anmeldeinformationen und Kennwörter für Replikations-Agents an. Nach der Replikationskonfiguration können Sie die Anmeldenamen und -kennwörter ändern. Weitere Informationen finden Sie unter [View and Modify Replication Security Settings](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md). Wenn Sie das Kennwort für ein von einem Replikations-Agent verwendetes Konto ändern, führen Sie [sp_changereplicationserverpasswords &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changereplicationserverpasswords-transact-sql.md) aus.  

Die Verwendung gruppenverwalteter Dienstkonten (group Managed Service Accounts, gMSA) wird ab SQL Server 2014 unterstützt. Weitere Informationen finden Sie im Blogartikel [Replication and group Managed Service Accounts (Replikation und gruppenverwaltete Dienstkonten)](https://repltalk.com/2019/03/26/replication-and-group-managed-service-accounts/).
  
## <a name="see-also"></a>Weitere Informationen  
 [Mindern von Bedrohungen und Sicherheitsrisiken &#40;Replikation&#41;](../../../relational-databases/replication/security/threat-and-vulnerability-mitigation-replication.md) [Sicherheitsmodell des Replikations-Agents](../../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Bewährte Methoden für die Replikationssicherheit](../../../relational-databases/replication/security/replication-security-best-practices.md)   

  
  
