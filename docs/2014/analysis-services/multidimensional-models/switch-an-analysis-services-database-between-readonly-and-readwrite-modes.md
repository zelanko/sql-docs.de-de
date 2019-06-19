---
title: Umschalten einer Analysis Services-Datenbank zwischen Schreib-und Lesemodus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 790e509dd29e388dfb697ba577958395a4a046ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66072888"
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a>Umschalten einer Analysis Services-Datenbank zwischen schreibgeschütztem Modus und Lese-/Schreibmodus
  In vielen Situationen muss vom [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbankadministrator (DBA) der Lese-/Schreibmodus einer tabellarischen oder mehrdimensionalen Datenbank geändert werden. Diese Situationen hängen in der Regel von Geschäftsforderungen ab, z. B. der Freigabe der Datenbank für einen Pool von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Servern zur Vereinfachung der Nutzung.  
  
 Es stehen zahlreiche Möglichkeiten zum Umschalten des Datenbankmodus zur Verfügung. In diesem Dokument werden die folgenden gängigen Szenarien erläutert:  
  
-   Interaktiv mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   Programmgesteuert mithilfe von AMO  
  
-   Mit einem Skript mithilfe von XMLA  
  
## <a name="procedures"></a>Vorgehensweisen  
  
#### <a name="to-switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a>So schalten Sie den Lese-/Schreibmodus einer Datenbank interaktiv mithilfe von Management Studio um  
  
1.  Suchen Sie im linken oder rechten Bereich von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] nach der umzuschaltenden Datenbank.  
  
2.  Mit der rechten Maustaste in der Datenbank, und wählen Sie **Eigenschaften**. Suchen Sie den Datenbankordner, und notieren Sie sich den Speicherort. Ein leerer Datenbankspeicherort weist darauf hin, dass sich der Datenbankordner im Datenordner des Servers befindet.  
  
    > [!IMPORTANT]  
    >  Sobald die Datenbank getrennt ist, kann [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Ihnen nicht mehr dabei helfen, den Datenbankspeicherort abzurufen.  
  
3.  Mit der rechten Maustaste in der Datenbank, und wählen Sie **trennen...**  
  
4.  Weisen Sie der Datenbank, die getrennt werden soll, ein Kennwort zu, und klicken Sie anschließend auf **OK** , um den Befehl zum Trennen auszuführen.  
  
5.  Suchen Sie die **Datenbanken** Ordner im linken oder rechten Bereich des [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
6.  Mit der rechten Maustaste die **Datenbanken** Ordner, und wählen **anfügen...**  
  
7.  Geben Sie im Textfeld **Ordner** den ursprünglichen Speicherort des Datenbankordners ein. Alternativ können Sie die Schaltfläche zum Durchsuchen ( **...** ) nach dem Datenbankordner suchen.  
  
8.  Wählen Sie den Lese-/Schreibmodus für die Datenbank aus.  
  
9. Geben Sie das Kennwort, das verwendet wurde, in Schritt 3, und klicken Sie auf **OK** zum Ausführen des Attach-Befehls.  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a>So schalten Sie den Lese-/Schreibmodus einer Datenbank programmgesteuert mithilfe von AMO um  
  
1.  Passen Sie in der C#-Anwendung den folgenden Beispielcode an, und führen Sie die angegebenen Aufgaben aus.  
  
 `private void SwitchReadWrite(Server server, string dbName,`  
  
 `ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `string databaseLocation;`  
  
 `db = server.Databases[dbName];`  
  
 `databaseLocation = db.DbStorageLocation;`  
  
 `if (databaseLocation == null)`  
  
 `{`  
  
 `string dataDir = server.ServerProperties["DataDir"].Value;`  
  
 `String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);`  
  
 `if (possibleFolders.Length > 1)`  
  
 `{`  
  
 `List<String> sortedFolders = new List<string>(possibleFolders.Length);`  
  
 `sortedFolders.AddRange(possibleFolders);`  
  
 `sortedFolders.Sort();`  
  
 `databaseLocation = sortedFolders[sortedFolders.Count - 1];`  
  
 `}`  
  
 `else`  
  
 `{`  
  
 `databaseLocation = possibleFolders[0];`  
  
 `}`  
  
 `}`  
  
 `db.Detach();`  
  
 `server.Attach(databaseLocation, dbReadWriteMode);`  
  
 `}`  
  
 `}`  
  
1.  Rufen Sie in der C#-Anwendung `SwitchReadWrite()` mit den erforderlichen Parametern auf.  
  
2.  Kompilieren Sie den Code, und führen Sie ihn zum Verschieben der Datenbank aus.  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a>So schalten Sie den Lese-/Schreibmodus einer Datenbank mit einem Skript mithilfe von XMLA um  
  
1.  Suchen Sie im linken oder rechten Bereich von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] nach der umzuschaltenden Datenbank.  
  
2.  Mit der rechten Maustaste in der Datenbank, und wählen Sie **Eigenschaften**. Suchen Sie den Datenbankordner, und notieren Sie sich den Speicherort. Ein leerer Datenbankspeicherort weist darauf hin, dass sich der Datenbankordner im Datenordner des Servers befindet.  
  
    > [!IMPORTANT]  
    >  Sobald die Datenbank getrennt ist, kann [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Ihnen nicht mehr dabei helfen, den Datenbankspeicherort abzurufen.  
  
3.  Öffnen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine neue XMLA-Registerkarte.  
  
4.  Kopieren Sie die folgende Skriptvorlage für XMLA:  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  Ersetzen Sie `%dbName%` durch den Namen der Datenbank und `%password%` durch das Kennwort. Die %-Zeichen sind Teil der Vorlage und müssen entfernt werden.  
  
2.  Führen Sie den XMLA-Befehl aus.  
  
3.  Kopieren Sie die folgende Skriptvorlage für XMLA in eine neue XMLA-Registerkarte:  
  
 `<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  Ersetzen Sie `%dbFolder%` durch den vollständigen UNC-Pfad des Datenbankordners, `%ReadOnlyMode%` durch den entsprechenden Wert `ReadOnly` oder `ReadWrite` und `%password%` durch das Kennwort. Die %-Zeichen sind Teil der Vorlage und müssen entfernt werden.  
  
2.  Führen Sie den XMLA-Befehl aus.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Anfügen und Trennen von Analysis Services-Datenbanken](attach-and-detach-analysis-services-databases.md)   
 [Datenbankspeicherort](database-storage-location.md)   
 [Datenbank-ReadWriteModes](database-readwritemodes.md)   
 [Attach-Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Detach-Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [ReadWriteMode-Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element)   
 [DbStorageLocation-Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
