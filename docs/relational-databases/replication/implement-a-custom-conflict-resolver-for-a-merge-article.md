---
title: Implementieren eines benutzerdefinierten Konfliktlösers (Merge)
description: Hier erfahren Sie, wie Sie einen benutzerdefinierten Konfliktlöser für eine Mergeveröffentlichung in SQL Server implementieren.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], stored procedure-based resolvers
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a71c7c83afe2fcb8b0192f6dfd12c8072ccdc392
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "75322157"
---
# <a name="implement-a-custom-conflict-resolver-for-a-merge-article"></a>Implementieren eines benutzerdefinierten Konfliktlösers für einen Mergeartikel
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie ein benutzerdefinierter Konfliktlöser für einen Mergeartikel mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder einem [!INCLUDE[tsql](../../includes/tsql-md.md)]COM-basierten benutzerdefinierten Konfliktlöser[ in ](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md) implementiert wird.  
  
 **In diesem Thema**  
  
-   **Implementieren eines benutzerdefinierten Konfliktlösers für einen Mergeartikel mit:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Ein COM-basierter Konfliktlöser](#COM)  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können einen eigenen benutzerdefinierten Konfliktlöser als gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozedur in einem Verleger schreiben. Während der Synchronisierung wird diese gespeicherte Prozedur aufgerufen, wenn in einem Artikel, bei dem der Konfliktlöser registriert wurde, Konflikte auftreten. Informationen zur Konfliktzeile werden vom Merge-Agent an die erforderlichen Parameter der Prozedur übermittelt. Auf gespeicherten Prozeduren basierende benutzerdefinierte Konfliktlöser werden immer auf dem Verleger erstellt.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfliktlöser für gespeicherte Prozeduren werden nur zur Behandlung änderungsbasierter Konflikte auf Zeilenebene aufgerufen. Sie können nicht zur Behandlung anderer Arten von Konflikten verwendet werden, z. B. von Einfügefehlern, die durch den Verstoß gegen eine PRIMARY KEY-Einschränkung oder einen eindeutigen Index ausgelöst werden.
  
#### <a name="to-create-a-stored-procedure-based-custom-conflict-resolver"></a>So erstellen und registrieren Sie einen auf gespeicherten Prozeduren basierenden benutzerdefinierten Konfliktlöser  
  
1.  Erstellen Sie auf dem Verleger entweder in der Veröffentlichungs- oder der **msdb** -Datenbank eine neue gespeicherte Systemprozedur, welche die folgenden erforderlichen Parameter implementiert:  
  
    |Parameter|Datentyp|BESCHREIBUNG|  
    |---------------|---------------|-----------------|  
    |**\@tableowner**|**sysname**|Name des Besitzers der Tabelle, für die ein Konflikt gelöst wird. Dies ist der Besitzer der Tabelle der Veröffentlichungsdatenbank.|  
    |**\@tablename**|**sysname**|Name der Tabelle, für die ein Konflikt gelöst wird.|  
    |**\@rowguid**|**uniqueidentifier**|Eindeutiger Bezeichner für die Zeile, in der der Konflikt auftritt.|  
    |**\@subscriber**|**sysname**|Name des Servers, von dem eine konfliktverursachende Änderung weitergegeben wird.|  
    |**\@subscriber_db**|**sysname**|Name der Datenbank, von der eine konfliktverursachende Änderung weitergegeben wird.|  
    |**\@log_conflict OUTPUT**|**int**|Legt fest, ob der Mergeprozess einen Konflikt für eine spätere Auflösung protokollieren soll:<br /><br /> **0** = Den Konflikt nicht protokollieren.<br /><br /> **1** = Der Abonnent verliert den Konflikt.<br /><br /> **2** = Der Verleger verliert den Konflikt.|  
    |**\@conflict_message OUTPUT**|**nvarchar(512)**|Meldung, die über die Auflösung ausgegeben werden soll, wenn der Konflikt protokolliert wird.|  
    |**\@destowner**|**sysname**|Der Besitzer der auf dem Abonnenten veröffentlichten Tabelle.|  
  
     Diese gespeicherte Prozedur verwendet die Werte, die vom Merge-Agent an diese Parameter übermittelt werden, um die benutzerdefinierte Konfliktlösungslogik zu implementieren. Sie muss ein einzelnes Zeilenresultset zurückgeben, das in der Struktur mit der Basistabelle identisch ist und die Datenwerte für die gewinnende Version der Zeile enthält.  
  
2.  Gewähren Sie allen Anmeldungen, die von Abonnenten zum Verbindungsaufbau mit dem Verleger verwendet werden, EXECUTE-Berechtigungen für die gespeicherte Prozedur.  

#### <a name="use-a-custom-conflict-resolver-with-a-new-table-article"></a>Verwenden eines benutzerdefinierten Konfliktlösers mit einem neuen Tabellenartikel  
  
1. Führen Sie [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) aus, um einen Artikel zu definieren. 
1. Geben Sie den Wert **MicrosoftSQL** **Server Stored Procedure Resolver** für den Parameter **\@article_resolver** an. 
1. Geben Sie den Namen der gespeicherten Prozedur an, mit der die Konfliktlöserlogik für den **\@resolver_info**-Parameter implementiert wird. 

   Weitere Informationen finden Sie unter [Definieren eines Artikels](../../relational-databases/replication/publish/define-an-article.md).
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a>So verwenden Sie einen benutzerdefinierten Konfliktlöser mit einem vorhandenen Tabellenartikel  
  
1.  Führen Sie [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) aus, wobei Sie **\@publication**, **\@article**, den Wert **article_resolver** für **\@property** und den Wert **MicrosoftSQL** **Server Stored ProcedureResolver** für **\@value** angeben.  
  
2.  Führen Sie [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) aus, wobei Sie **\@publication**, **\@article**, den Wert **resolver_info** für **\@property** und den Namen der gespeicherten Prozedur, mit der die Konfliktlöserlogik implementiert wird, für **\@value** angeben.  
  
##  <a name="COM"></a> Verwenden eines COM-basierten benutzerdefinierten Konfliktlösers  
 Der <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> -Namespace implementiert eine Schnittstelle, mit der Sie eine komplexe Geschäftslogik zum Verarbeiten von Ereignissen und zur Lösung von Konflikten schreiben können, die während der Synchronisierung der Mergereplikation eintreten. Weitere Informationen finden Sie unter [Implementieren eines Geschäftslogikhandlers für einen Mergeartikel](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md). Sie können auch eine eigene, auf systemeigenem Code basierende benutzerdefinierte Geschäftslogik zur Lösung von Konflikten schreiben. Diese Logik wird mithilfe von Produkten wie [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++ als COM-Komponente konzipiert und in DLLs (Dynamic-Link Libraries) kompiliert. Ein solcher COM-basierter benutzerdefinierter Konfliktlöser muss die **ICustomResolver**-Schnittstelle implementieren, die speziell für die Konfliktlösung entworfen wurde.  
  
#### <a name="to-create-and-register-a-com-based-custom-conflict-resolver"></a>So erstellen und registrieren Sie einen COM-basierten benutzerdefinierten Konfliktlöser  
  
1.  Fügen Sie in einer COM-kompatiblen Erstellungsumgebung Verweise auf die benutzerdefinierte Konfliktlöserbibliothek hinzu.  
  
2.  Verwenden Sie für ein Visual&nbsp;C++-Projekt die #import-Direktive, um diese Bibliothek in Ihr Projekt zu importieren.  
  
3.  Fügen Sie eine Klasse hinzu, die die **ICustomResolver** -Schnittstelle implementiert.  
  
4.  Implementieren Sie bestimmte Methoden und Eigenschaften.  
  
5.  Erstellen Sie das Projekt, um die benutzerdefinierte Konfliktlöserbibliotheksdatei zu erstellen.  
  
6.  Stellen Sie die Bibliothek in dem Verzeichnis bereit, das die ausführbare Datei des Merge-Agent (normalerweise \Microsoft SQL Server\100\COM) enthält.  
  
    > [!NOTE]  
    >  Ein benutzerdefinierter Konfliktlöser muss bei einem Pullabonnement auf dem Abonnenten, bei einem Pushabonnement auf dem Verteiler oder auf dem mit der Websynchronisierung verwendeten Webserver bereitgestellt werden.  
  
7.  Registrieren Sie die benutzerdefinierte Konfliktlöserbibliothek folgendermaßen mit „regsvr32.exe“ vom Bereitstellungsverzeichnis aus:  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  Führen Sie auf dem Herausgeber [sp_enumcustomresolvers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) aus, um zu prüfen, ob die Bibliothek noch nicht als benutzerdefinierter Konfliktlöser registriert wurde.  
  
9. Um die Bibliothek als benutzerdefinierten Konfliktlöser zu registrieren, führen Sie auf dem Verteiler [sp_registercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md) aus. Geben Sie den Anzeigenamen des COM-Objekts für **\@article_resolver**, die Bibliotheks-ID (CLSID) für **\@resolver_clsid** und den Wert **FALSE** für **\@is_dotnet_assembly** an.  
  
    > [!NOTE]  
    >  Wenn er nicht mehr benötigt wird, können Sie die Registrierung eines benutzerdefinierten Konfliktlösers mit [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md) aufheben.  
  
10. (Optional) Wiederholen Sie bei einem Cluster die Schritte 6-9, um den benutzerdefinierten Konfliktlöser auf allen Knoten des Clusters zu registrieren. Diese Schritte sind erforderlich, um sicherzustellen, dass der benutzerdefinierte Konfliktlöser nach einem Failover die Synchronisierung korrekt laden kann.
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a>So verwenden Sie einen benutzerdefinierten Konfliktlöser mit einem neuen Tabellenartikel  
  
1.  Führen Sie auf dem Herausgeber [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) aus, und achten Sie auf den Anzeigenamen des gewünschten Konfliktlösers.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) zur Definition eines Artikels aus. Geben Sie den Anzeigenamen des Artikelkonfliktlösers aus Schritt 1 für **\@article_resolver** an. Weitere Informationen finden Sie unter [Definieren eines Artikels](../../relational-databases/replication/publish/define-an-article.md).  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a>So verwenden Sie einen benutzerdefinierten Konfliktlöser mit einem vorhandenen Tabellenartikel  
  
1.  Führen Sie auf dem Herausgeber [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) aus, und achten Sie auf den Anzeigenamen des gewünschten Konfliktlösers.  
  
2.  Führen Sie [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) aus. Geben Sie dabei **\@publication** , **\@article**, den Wert **article_resolver** für **\@property** und den Anzeigenamen des Artikelkonfliktlösers aus Schritt 1 für **\@value** an.  
  

## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Konflikterkennung und -lösung der Mergereplikation](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [COM-basierte, benutzerdefinierte Konfliktlöser](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md)   
 [Bewährte Methoden für die Replikationssicherheit](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
