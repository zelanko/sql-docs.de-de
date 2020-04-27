---
title: Konfigurieren der Serverkonfigurationsoption Speicher für Indexerstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- index create memory option
ms.assetid: 3d722d9b-bada-4bf5-a9d7-bfc556bb4915
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 280d4edef062429304d5c6e1d6c65ea63fac2eee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62786940"
---
# <a name="configure-the-index-create-memory-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Speicher für Indexerstellung
  In diesem Thema wird beschrieben, wie die Serverkonfigurationsoption **Speicher für Indexerstellung** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert wird. Mit der Option **Speicher für Indexerstellung** wird der maximale Umfang des für die Erstellung von Indizes zugeordneten Arbeitsspeichers gesteuert. Der Standardwert für diese Option beträgt 0 (Selbstkonfiguration). Wenn später für die Indexerstellung mehr Speicherplatz benötigt wird und noch Speicherplatz verfügbar ist, wird dieser vom Server verwendet, und der für die Option festgelegte Wert wird überschritten. Wenn kein Speicherplatz mehr verfügbar ist, wird die Indexerstellung so lange fortgesetzt, wie der bereits zugeordnete Speicherplatz gestattet.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option Speicher für Indexerstellung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option „Speicher für Indexerstellung“](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Die Einstellung der Option **Min. Arbeitsspeicher pro Abfrage** hat Vorrang vor der Option **Speicher für Indexerstellung**. Wenn Sie beide Optionen ändern und der Wert von **index create memory** (Speicher für Indexerstellung) den Wert von **min memory per query**(Min. Arbeitsspeicher pro Abfrage) unterschreitet, werden die Werte zwar festgelegt, es wird jedoch eine Warnmeldung ausgegeben. Eine ähnliche Warnmeldung erhalten Sie auch während der Ausführung.  
  
-   Bei der Verwendung von partitionierten Tabellen und Indizes können sich die Mindestanforderungen für den zur Indexerstellung benötigten Speicherplatz bei nicht ausgerichteten partitionierten Indizes und einem hohen Parallelitätsgrad erheblich erhöhen. Mit dieser Option wird gesteuert, wie viel Arbeitsspeicher den Indexpartitionen eines einzelnen Indexerstellungsvorgangs insgesamt zugeordnet wird. Wenn der durch die Option festgelegte Wert das zur Ausführung der Abfrage erforderliche Minimum unterschreitet, wird die Abfrage mit einem Fehler beendet.  
  
-   Die tatsächliche Speicherkapazität, die für das Betriebssystem und die Hardwareplattform, auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, verwendet werden kann, wird durch den Ausführungswert dieser Option nicht überschritten. Bei 32-Bit-Betriebssystemen beträgt der Ausführungswert weniger als 3 Gigabytes (GB).  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   Die Option **Speicher für Indexerstellung** ist eine selbstkonfigurierende Option, die im Normalfall nicht angepasst werden muss. Wenn Sie jedoch Schwierigkeiten beim Erstellen von Indizes feststellen, sollten Sie den Wert dieser Option abweichend vom Ausführungswert erhöhen.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-index-create-memory-option"></a>So konfigurieren Sie die Option "Speicher für Indexerstellung"  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Speicher** -Knoten.  
  
3.  Geben Sie unter **Speicher für Indexerstellung**den gewünschten Wert für die Option „Speicher für Indexerstellung“ ein, oder wählen Sie einen Wert aus.  
  
     Sie können mit der Option **Speicher für Indexerstellung** den Umfang an Speicherplatz steuern, der für Sortiervorgänge bei der Indexerstellung verwendet wird. Bei der Option **Speicher für Indexerstellung** handelt es sich um eine selbstkonfigurierende Option, die in den meisten Fällen ohne weitere Anpassung funktionieren sollte. Wenn Sie jedoch Schwierigkeiten beim Erstellen von Indizes feststellen, sollten Sie den Wert dieser Option abweichend vom Ausführungswert erhöhen. Das Sortieren von Abfragen wird über die Option **Min. Arbeitsspeicher pro Abfrage** gesteuert.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-index-create-memory-option"></a>So konfigurieren Sie die Option "Speicher für Indexerstellung"  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `index create memory` auf `4096`festzulegen.  
  
```sql  
USE AdventureWorks2012 ;  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
EXEC sp_configure 'index create memory', 4096  
GO  
RECONFIGURE;  
GO  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="follow-up-after-you-configure-the-index-create-memory-option"></a><a name="FollowUp"></a> Nachverfolgung: Nach dem Konfigurieren der Option Speicher für Indexerstellung  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. Konfigurationen &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Server Konfigurationsoptionen für den Server Arbeitsspeicher](server-memory-server-configuration-options.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
