---
title: Angeben eines Mergeartikelkonfliktlösers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
- merge replication conflict resolution [SQL Server replication], merge article resolvers
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 388d400160e3fa7b3240c7a9c014bcf36ae25f3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68212093"
---
# <a name="specify-a-merge-article-resolver"></a>Angeben eines Mergeartikelkonfliktlösers
  In diesem Thema wird beschrieben, wie ein Konfliktlöser für Mergeartikel in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]angegeben wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
-   **So geben Sie einen mergeartikelresolver an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Die Mergereplikation unterstützt die folgenden Typen von Artikelkonfliktlösern:  
  
    -   Den Standardkonfliktlöser. Das Verhalten des Standardkonfliktlösers hängt davon ab, ob es sich um ein Clientabonnement oder ein Serverabonnement handelt. Informationen zum Angeben eines Abonnementtyps finden Sie unter [Angeben eines Mergerabonnementtyps und einer Konfliktlösungspriorität &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md).  
  
    -   Von Ihnen geschriebene benutzerdefinierte Konfliktlöser. Dabei kann es sich um einen Geschäftslogikhandler (in verwaltetem Code geschrieben) oder einen benutzerdefinierten COM-basierten Konfliktlöser handeln. Weitere Informationen finden Sie unter [Erweiterte Konflikterkennung und-Lösung bei der Mergereplikation](../merge/advanced-merge-replication-conflict-detection-and-resolution.md). Wenn Sie benutzerdefinierte Logik implementieren müssen, die für jede replizierte Zeile und nicht nur für Konfliktzeilen ausgeführt werden muss, finden Sie unter [Implementieren eines Geschäftslogikhandlers für einen Mergeartikel](../implement-a-business-logic-handler-for-a-merge-article.md)angegeben wird.  
  
    -   Ein COM-basierter Standard Konflikt Löser, der in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]enthalten ist.  
  
-   Wenn Sie einen anderen als den Standardkonfliktlöser verwenden möchten, müssen Sie den Konfliktlöser auf den Computer kopieren und dort registrieren, auf dem der Merge-Agent ausgeführt wird (ein Geschäftslogikhandler muss auch auf dem Verleger registriert werden). Der Merge-Agent wird auf folgenden Computern ausgeführt:  
  
    -   Dem Verteiler für ein Pushabonnement  
  
    -   Dem Abonnent für ein Pullabonnement  
  
    -   Dem Server mit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internetinformationsdienste (IIS) für ein Pullabonnement, das die Websynchronisierung verwendet.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Nach dem Registrieren des Konfliktlösers geben Sie dessen Verwendung durch einen Artikel im Dialogfeld **Artikeleigenschaften - **Artikel>** auf der Registerkarte \<Konfliktlöser** an. Dieses Dialogfeld ist im Assistenten für neue Veröffentlichung über das Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** verfügbar. Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-a-resolver"></a>So geben Sie einen Konfliktlöser an  
  
1.  Wählen Sie auf der Seite **Artikel** des Assistenten für neue Veröffentlichung bzw. des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** eine Tabelle aus.  
  
2.  Klicken Sie auf **Artikeleigenschaften**und anschließend auf **Eigenschaften des hervorgehobenen Artikels festlegen**.  
  
3.  Klicken Sie auf der Seite **Artikeleigenschaften - \<Artikel>** auf die Registerkarte **Konfliktlöser**.  
  
4.  Wählen Sie **Benutzerdefinierten Konfliktlöser verwenden (registriert auf dem Verteiler)** aus, und klicken Sie dann in der Liste auf den Konfliktlöser.  
  
5.  Sind für den Konfliktlöser Eingaben erforderlich (z. B. ein Spaltenname), geben Sie sie im Textfeld **Geben Sie die vom Konfliktlöser benötigten Informationen ein** an.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  Wiederholen Sie diesen Vorgang für jeden Artikel, der einen Konfliktlöser erfordert.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-register-a-custom-conflict-resolver"></a>So registrieren Sie einen benutzerdefinierten Konfliktlöser  
  
1.  Wenn Sie einen eigenen benutzerdefinierten Konfliktlöser registrieren möchten, erstellen Sie einen der folgenden Typen:  
  
    -   Einen auf verwaltetem Code basierenden Konfliktlöser als Geschäftslogikhandler. Weitere Informationen finden Sie unter [Implementieren eines Geschäftslogik Handlers für einen Mergeartikel](../implement-a-business-logic-handler-for-a-merge-article.md).  
  
    -   Konfliktlöser, der auf einer gespeicherten Prozedur und COM basiert. Weitere Informationen finden Sie unter [Implementieren eines benutzerdefinierten Konfliktlösers für einen Mergeartikel
](../implement-a-custom-conflict-resolver-for-a-merge-article.md).  
  
2.  Um zu bestimmen, ob der gewünschte Konfliktlöser bereits registriert ist, führen Sie auf dem Verleger für eine beliebige Datenbank [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) aus. Daraufhin werden eine Beschreibung des benutzerdefinierten Konfliktlösers sowie der Klassenbezeichner (CLSID) für jeden auf dem Verteiler registrierten COM-basierten Konfliktlöser bzw. Informationen zur verwalteten Assembly für jeden auf dem Verteiler registrierten Geschäftslogikhandler angezeigt.  
  
3.  Wenn der gewünschte benutzerdefinierte Konfliktlöser noch nicht registriert ist, führen Sie auf dem Verteiler [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql) aus. Geben Sie einen Namen für den Konflikt Löser **@article_resolver**für an. für einen Geschäftslogik Handler ist dies der Anzeige Name der Assembly. Geben Sie für **@resolver_clsid**com-basierte Konflikt Löser die CLSID der DLL für an, und geben Sie für einen Geschäftslogik Handler den Wert `true` für **@is_dotnet_assembly**, den Namen der Assembly für **@dotnet_assembly_name**und den voll qualifizierten Namen der Klasse an, die für <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> **@dotnet_class_name**überschreibt.  
  
    > [!NOTE]  
    >  Wenn eine Geschäftslogik Handler-Assembly nicht im gleichen Verzeichnis wie die Merge-Agent ausführbare Datei, im gleichen Verzeichnis wie die Anwendung, die die Merge-Agent synchron startet, oder im globalen Assemblycache (GAC) bereitgestellt wird, müssen Sie den vollständigen Pfad mit dem Assemblynamen für **@dotnet_assembly_name**angeben.  
  
4.  Wenn der Konfliktlöser ein COM-basierter Konfliktlöser ist, gehen Sie wie folgt vor:  
  
    -   Kopieren Sie die DLL für den benutzerdefinierten Konfliktlöser auf den Verteiler für Pushabonnements oder auf den Abonnenten von Pullabonnements.  
  
        > [!NOTE]  
        >  Benutzerdefinierte Konfliktlöser von[!INCLUDE[msCoName](../../../includes/msconame-md.md)] sind im [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM-Verzeichnis enthalten.  
  
    -   Verwenden Sie regsvr32.exe, um die benutzerdefinierte Konfliktlöser-DLL im Betriebssystem zu registrieren. Führen Sie beispielsweise folgenden Befehl an der Eingabeaufforderung aus, um den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Konfliktlöser Zusatz zu registrieren:  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  Wenn es sich bei dem Konflikt Löser um einen Geschäftslogik Handler handelt, stellen Sie die Assembly im gleichen Ordner wie die Merge-Agent ausführbare Datei (replmerg. exe), im gleichen Ordner wie eine Anwendung, die die Merge-Agent aufruft, oder **@dotnet_assembly_name** in dem Ordner bereit, der für den-Parameter in Schritt 3 angegeben wurde.  
  
    > [!NOTE]  
    >  Der Standardinstallationspfad der ausführbaren Merge-Agent-Datei lautet [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.  
  
#### <a name="to-specify-a-custom-resolver-when-defining-a-merge-article"></a>So geben Sie in der Definition eines Mergeartikels einen benutzerdefinierten Konfliktlöser an  
  
1.  Wenn Sie einen eigenen benutzerdefinierten Konfliktlöser verwenden möchten, erstellen und registrieren Sie den Konfliktlöser wie oben beschrieben.  
  
2.  Führen Sie auf dem Verleger [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)aus, und notieren Sie den Namen des gewünschten benutzerdefinierten Konfliktlösers im **value**-Feld des Resultsets.  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) aus. Geben Sie den Namen des Konflikt Lösers aus Schritt 2 **@article_resolver** für und alle erforderlichen Eingaben für den benutzerdefinierten Konflikt Löser **@resolver_info** mit dem-Parameter an. Für auf gespeicherten Prozeduren basierende benutzerdefinierte **@resolver_info** Konflikt Löser ist der Name der gespeicherten Prozedur. Weitere Informationen zu den für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] erforderlichen Eingaben für Konfliktlöser finden Sie unter [Microsoft COM-Based Resolvers (Microsoft COM-basierte Konfliktlöser)](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).  
  
#### <a name="to-specify-or-change-a-custom-resolver-for-an-existing-merge-article"></a>So geben Sie einen benutzerdefinierten Konfliktlöser für einen vorhandenen Mergeartikel an oder ändern diesen  
  
1.  Um zu bestimmen, ob ein benutzerdefinierter Konfliktlöser für einen Artikel definiert wurde, oder um den Namen des Konfliktlösers abzurufen, führen Sie [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) aus. Wenn ein benutzerdefinierter Konfliktlöser für einen Artikel definiert wurde, wird dessen Namen im Feld **article_resolver** angezeigt. Alle dem Konfliktlöser übergegebene Eingaben werden im Feld **resolver_info** des Resultsets angezeigt.  
  
2.  Führen Sie auf dem Verleger [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) aus, und notieren Sie den Namen des gewünschten benutzerdefinierten Konfliktlösers im **value**-Feld des Resultsets.  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) aus. Geben Sie den Wert **article_resolver**, einschließlich der vollständigen Pfadangabe für Geschäftslogikhandler, für **@property**und den Namen des gewünschten benutzerdefinierten Konfliktslösers aus Schritt 2 für **@value**angegeben wird.  
  
4.  Führen Sie nochmals [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) aus, um irgendwelche erforderlichen Eingaben für den benutzerdefinierten Konfliktlöser zu ändern. Geben Sie den Wert **resolver_info** für **@property** und alle erforderlichen Eingaben für den benutzerdefinierten Konfliktlöser für **@value**angegeben wird. Für auf gespeicherten Prozeduren basierende benutzerdefinierte **@resolver_info** Konflikt Löser ist der Name der gespeicherten Prozedur. Weitere Informationen zu den erforderlichen Eingaben finden Sie unter [Microsoft COM-Based Resolvers (Microsoft COM-basierte Konfliktlöser)](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).  
  
#### <a name="to-unregister-a-custom-conflict-resolver"></a>So heben Sie die Registrierung eines benutzerdefinierten Konfliktlösers auf  
  
1.  Führen Sie auf dem Verleger [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) aus, und notieren Sie den Namen des zu entfernenden benutzerdefinierten Konfliktlösers im **value**-Feld des Resultsets.  
  
2.  Führen Sie [Sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) auf dem Verteiler aus. Geben Sie den vollständigen Namen des benutzerdefinierten Konflikt Lösers aus **@article_resolver**Schritt 1 für an.  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 In diesem Beispiel wird ein neuer Artikel erstellt und angegeben, dass der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Konfliktlöser "Mittelwerterstellung" zur Berechnung des Mittelwerts der Spalte **UnitPrice** verwendet werden soll, wenn Konflikte auftreten.  
  
 [!code-sql[HowTo#sp_addmerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_addmerge_resolver)]  
  
 In diesem Beispiel wird ein Artikel dahingehend geändert, dass der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Konfliktlöser "Zusatz" zur Berechnung der Summe der Spalte **UnitsOnOrder** verwendet werden soll, wenn Konflikte auftreten.  
  
 [!code-sql[HowTo#sp_changemerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_changemerge_resolver)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Konflikterkennung und-Lösung bei der Mergereplikation](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Implementieren eines Geschäftslogikhandlers für einen Mergeartikel](../implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
