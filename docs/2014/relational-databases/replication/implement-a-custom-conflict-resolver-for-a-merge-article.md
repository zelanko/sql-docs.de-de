---
title: Implementieren eines benutzerdefinierten Konfliktlösers für einen Mergeartikel | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 47d0f7c4eb6c78b9e551fafdc1e018a27604086e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721226"
---
# <a name="implement-a-custom-conflict-resolver-for-a-merge-article"></a>Implementieren eines benutzerdefinierten Konfliktlösers für einen Mergeartikel
  In diesem Thema wird beschrieben, wie ein benutzerdefinierter Konfliktlöser für einen Mergeartikel [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]mit[!INCLUDE[tsql](../../includes/tsql-md.md)] oder einem [COM-basierten benutzerdefinierten Konfliktlöser](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md) in implementiert wird.  
  
 **In diesem Thema**  
  
-   **So implementieren Sie einen benutzerdefinierten Konfliktlöser für einen Mergeartikel mit:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [COM-basierter Konfliktlöser](#COM)  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können einen eigenen benutzerdefinierten Konfliktlöser als gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozedur in einem Verleger schreiben. Diese gespeicherte Prozedur wird während der Synchronisierung aufgerufen, wenn in einem Artikel, für den der Konfliktlöser registriert wurde, Konflikte erkannt werden. Die Informationen zur Konfliktzeile werden vom Merge-Agent an die erforderlichen Parameter der Prozedur übergeben. Auf gespeicherten Prozeduren basierende benutzerdefinierte Konfliktlöser werden immer auf dem Verleger erstellt.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfliktlöser für gespeicherte Prozeduren werden nur zur Behandlung änderungsbasierter Konflikte auf Zeilenebene aufgerufen. Sie können nicht zur Behandlung anderer Arten von Konflikten verwendet werden, z.&nbsp;B. von Einfügefehlern, die durch den Verstoß gegen eine PRIMARY&nbsp;KEY-Einschränkung oder einen eindeutigen Index verursacht werden.  
  
#### <a name="to-create-a-stored-procedure-based-custom-conflict-resolver"></a>So erstellen und registrieren Sie einen auf gespeicherten Prozeduren basierenden benutzerdefinierten Konfliktlöser  
  
1.  Erstellen Sie auf dem Verleger entweder in der Veröffentlichungs- oder der **msdb** -Datenbank eine neue gespeicherte Systemprozedur, welche die folgenden erforderlichen Parameter implementiert:  
  
    |Parameter|Datentyp|Description|  
    |---------------|---------------|-----------------|  
    |**@tableowner**|`sysname`|Name des Besitzers der Tabelle, für die ein Konflikt gelöst wird. Dies ist der Besitzer der Tabelle der Veröffentlichungsdatenbank.|  
    |**@tablename**|`sysname`|Name der Tabelle, für die ein Konflikt gelöst wird.|  
    |**@rowguid**|`uniqueidentifier`|Eindeutiger Bezeichner für die Zeile, die den Konflikt enthält.|  
    |**@subscriber**|`sysname`|Name des Servers, von dem eine konfliktverursachende Änderung weitergegeben wird.|  
    |**@subscriber_db**|`sysname`|Name der Datenbank, von der eine konfliktverursachende Änderung weitergegeben wird.|  
    |**@log_conflict AUSGABE**|`int`|Ob der Mergeprozess einen Konflikt für eine spätere Auflösung protokollieren soll:<br /><br /> **0** = Den Konflikt nicht protokollieren.<br /><br /> **1** = Der Abonnent verliert den Konflikt.<br /><br /> **2** = Der Verleger verliert den Konflikt.|  
    |**@conflict_message AUSGABE**|`nvarchar(512)`|Meldung, die über die Auflösung ausgegeben werden soll, wenn der Konflikt protokolliert wird.|  
    |**@destowner**|`sysname`|Der Besitzer der auf dem Abonnenten veröffentlichten Tabelle.|  
  
     Diese gespeicherte Prozedur verwendet die Werte, die vom Merge-Agent für diese Parameter übergeben werden, um die benutzerdefinierte Konfliktlöserlogik zu implementieren. Sie muss ein einzeiliges Resultset zurückgeben, dessen Struktur mit der Struktur der Basistabelle identisch ist, und das die Datenwerte für die gewinnende Version der Zeile enthält.  
  
2.  Gewähren Sie allen Anmeldungen, die von Abonnenten zum Verbindungsaufbau mit dem Verleger verwendet werden, EXECUTE-Berechtigungen für die gespeicherte Prozedur.  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a>So verwenden Sie einen benutzerdefinierten Konfliktlöser mit einem neuen Tabellenartikel  
  
1.  Führen Sie [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) zur Definition eines Artikels unter Angabe eines Werts des **MicrosoftSQL**-**Konfliktlösers für gespeicherte Prozeduren** für den **@article_resolver** -Parameter und den Namen der gespeicherten Prozedur, mit der die Konfliktlöserlogik implementiert wird, für den Parameter **@resolver_info** aus. Weitere Informationen finden Sie unter [Define an Article](publish/define-an-article.md).  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a>So verwenden Sie einen benutzerdefinierten Konfliktlöser mit einem vorhandenen Tabellenartikel  
  
1.  Führen Sie [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) aus, wobei Sie **@publication** , **@article** , den Wert **article_resolver** für **@property** und einen Wert des **MicrosoftSQL** **Konfliktlösers für gespeicherte Prozeduren** für **@value** angeben.  
  
2.  Führen Sie [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)aus, wobei Sie **@publication** , **@article** , den Wert **resolver_info** für **@property** und den Namen der gespeicherten Prozedur, mit der die Konfliktlöserlogik implementiert wird, für **@value** implementiert wird.  
  
##  <a name="COM"></a> Verwenden eines COM-basierten benutzerdefinierten Konfliktlösers  
 Der <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> -Namespace implementiert eine Schnittstelle, mit der Sie eine komplexe Geschäftslogik zum Verarbeiten von Ereignissen und zur Lösung von Konflikten schreiben können, die während der Synchronisierung der Mergereplikation eintreten. Weitere Informationen finden Sie unter [Implementieren eines Geschäftslogikhandlers für einen Mergeartikel](implement-a-business-logic-handler-for-a-merge-article.md). Sie können auch eine eigene, auf systemeigenem Code basierende benutzerdefinierte Geschäftslogik zur Lösung von Konflikten schreiben. Diese Logik wird mithilfe von Produkten wie [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++ als COM-Komponente konzipiert und in DLLs (Dynamic-Link Libraries) kompiliert. Ein solcher COM-basierter benutzerdefinierter Konfliktlöser muss die **ICustomResolver**-Schnittstelle implementieren, die speziell für die Konfliktlösung entworfen wurde.  
  
#### <a name="to-create-and-register-a-com-based-custom-conflict-resolver"></a>So erstellen und registrieren Sie einen COM-basierten benutzerdefinierten Konfliktlöser  
  
1.  Fügen Sie in einer COM-kompatiblen Erstellungsumgebung Verweise auf die benutzerdefinierte Konfliktlöserbibliothek hinzu.  
  
2.  Verwenden Sie für ein Visual&nbsp;C++-Projekt die #import-Direktive, um diese Bibliothek in Ihr Projekt zu importieren.  
  
3.  Fügen Sie eine Klasse hinzu, die die **ICustomResolver** -Schnittstelle implementiert.  
  
4.  Implementieren Sie bestimmte Methoden und Eigenschaften.  
  
5.  Erstellen Sie das Projekt, um die benutzerdefinierte Konfliktlöserbibliotheksdatei zu erstellen.  
  
6.  Stellen Sie die Bibliothek in dem Verzeichnis bereit, das die ausführbare Datei des Merge-Agents (normalerweise \Microsoft SQL Server\100\COM) enthält.  
  
    > [!NOTE]  
    >  Ein benutzerdefinierter Konfliktlöser muss bei einem Pullabonnement auf dem Abonnenten, bei einem Pushabonnement auf dem Verteiler oder auf dem mit der Websynchronisierung verwendeten Webserver bereitgestellt werden.  
  
7.  Registrieren Sie die benutzerdefinierte Konfliktlöserbibliothek folgendermaßen mit regsvr32.exe vom Bereitstellungsverzeichnis aus:  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  Führen Sie auf dem Verleger [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) aus, um zu prüfen, ob die Bibliothek noch nicht als benutzerdefinierter Konfliktlöser registriert wurde.  
  
9. Um die Bibliothek als benutzerdefinierten Konfliktlöser zu registrieren, führen Sie auf dem Verteiler [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql) aus. Geben Sie den Anzeigenamen des COM-Objekts für **@article_resolver** , die Bibliotheks ID (CLSID) für **@resolver_clsid** , und den Wert `false` für **@is_dotnet_assembly** .  
  
    > [!NOTE]  
    >  Wenn er nicht mehr benötigt wird, kann die Registrierung eines benutzerdefinierten Konfliktlösers mit [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) aufgehoben werden.  
  
10. (Optional) Wiederholen Sie bei einem Cluster die Schritte 5&nbsp;bis&nbsp;8, um den benutzerdefinierten Konfliktlöser auf allen Knoten des Clusters zu registrieren. Dies ist erforderlich, um sicherzustellen, dass der benutzerdefinierte Konfliktlöser nach einem Failover die Synchronisierung korrekt laden kann.  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a>So verwenden Sie einen benutzerdefinierten Konfliktlöser mit einem neuen Tabellenartikel  
  
1.  Führen Sie auf dem Verleger [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) aus, und achten Sie auf den Anzeigenamen des gewünschten Konfliktlösers.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) zur Definition eines Artikels aus. Geben Sie den Anzeigenamen des Artikelkonfliktlösers aus Schritt&nbsp;1 für **@article_resolver** implementiert wird. Weitere Informationen finden Sie unter [Definieren eines Artikels](publish/define-an-article.md).  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a>So verwenden Sie einen benutzerdefinierten Konfliktlöser mit einem vorhandenen Tabellenartikel  
  
1.  Führen Sie auf dem Verleger [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) aus, und achten Sie auf den Anzeigenamen des gewünschten Konfliktlösers.  
  
2.  Führen Sie [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) aus. Geben Sie dabei **@publication** , **@article** , den Wert **article_resolver** für **@property** und den Anzeigenamen des Artikelkonfliktlösers aus Schritt 1 für **@value** an.  
  
#### <a name="viewing-a-sample-custom-resolver"></a>Anzeigen eines Beispiels für einen benutzerdefinierten Konfliktlöser  
  
1.  Ein Beispiel ist in SQL Server 2000-Beispieldateien verfügbar. Herunterladen der [ **sql2000samples.zip**](https://github.com/Microsoft/sql-server-samples/blob/master/samples/tutorials/Miscellaneous/sql2000samples.zip). Dadurch wird die 3 Dateien mit einer Gesamtkapazität von 6,9 MB heruntergeladen.  
  
2.  Extrahieren Sie die Dateien aus der heruntergeladenen komprimierten CAB-Datei.  
  
3.  Führen Sie **setup.exe**aus.  
  
    > [!NOTE]  
    >  Bei der Auswahl der Installationsoptionen müssen Sie nur die Beispiele für die **Replikation** installieren. (Der Standardinstallationspfad lautet **C:\Program Files (x86) \Microsoft SQL Server 2000 Samples\1033\\** )  
  
4.  Wechseln Sie zum Installationsordner. (Der Standardordner ist **C:\Programme (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)  
  
5.  Führen Sie das Programm **unzip_sqlreplSP3.exe** aus.  
  
    > [!NOTE]  
    >  Der Beispielkonfliktlöser wird (standardmäßig) im Ordner **C:\Programme (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** installiert.  
  
6.  Suchen Sie im Ordner **subspres** alle Vorkommen von **#include sqlres.h** in allen Quelldateien, und ersetzen Sie sie durch **#import "replrec.dll" no_namespace, raw_interfaces_only**.  
  
## <a name="see-also"></a>Siehe auch  
 [Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [COM-Based Custom Resolvers](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md)   
 [Bewährte Methoden für die Replikationssicherheit](security/replication-security-best-practices.md)  
  
  
