---
title: Datenbanklesemodi | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], read/write
- databases [Analysis Services], read-only
ms.assetid: 03d7cb5c-7ff0-4e15-bcd2-7075d1b0dd69
author: minewiskan
ms.author: owend
ms.openlocfilehash: 723eb7c1c0e8547ee411fc54ecd4aca613011b38
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547112"
---
# <a name="database-readwritemodes"></a>Datenbank-ReadWriteModes
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankadministratoren (DBA) müssen oftmals eine Datenbank mit Lese-/Schreibzugriff in eine schreibgeschützte Datenbank ändern oder umgekehrt. Diese Situationen hängen in der Regel von Unternehmensanforderungen ab, z.&nbsp;B. der Freigabe des Datenbankordners für mehrere Server zum dezentralen Skalieren einer Projektmappe und zur Verbesserung der Leistung. Für diese Situationen ermöglicht die `ReadWriteMode`-Datenbankeigenschaft dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbankadministrator, den Betriebsmodus der Datenbank problemlos zu ändern.  
  
## <a name="readwritemode-database-property"></a>ReadWriteMode-Datenbankeigenschaft  
 Die `ReadWriteMode`-Datenbankeigenschaft gibt an, ob sich die Datenbank im Lese/Schreibmodus oder im schreibgeschützten Modus befindet. Hierbei handelt es sich um die beiden einzigen möglichen Werte der Eigenschaft. Wenn sich die Datenbank im schreibgeschützten Modus befindet, können keine Änderungen oder Updates für die Datenbank übernommen werden. Im Lese-/Schreibmodus können hingegen Änderungen und Updates vorgenommen werden. Die `ReadWriteMode`-Datenbankeigenschaft wird als schreibgeschützte Eigenschaft definiert. Sie kann nur über einen `Attach`-Befehl festgelegt werden.  
  
 Wenn sich eine Datenbank im schreibgeschützten Modus befindet, gelten einige Beschränkungen, die sich auf die herkömmlichen für die Datenbank zulässigen Vorgänge auswirken können. Die eingeschränkten Vorgänge finden Sie in der folgenden Tabelle.  
  
|Schreibgeschützter Modus|Eingeschränkte Vorgänge|  
|-------------------|---------------------------|  
|XML/A-Befehle<br /><br /> <br /><br /> Hinweis: Beim Ausführen eines dieser Befehle wird ein Fehler ausgegeben.|`Create`<br /><br /> `Alter`<br /><br /> `Delete`<br /><br /> `Process`<br /><br /> `MergePartitions`<br /><br /> `DesignAggregations`<br /><br /> `CommitTransaction`<br /><br /> `Restore`<br /><br /> `Synchronize`<br /><br /> `Insert`<br /><br /> `Update`<br /><br /> `Drop`<br /><br /> <br /><br /> Hinweis: Das Zellenrückschreiben ist in schreibgeschützten Datenbanken zulässig. Für die Änderungen kann jedoch kein Commit ausgeführt werden.|  
|MDX-Anweisungen<br /><br /> <br /><br /> Hinweis: Beim Ausführen einer dieser Anweisungen wird ein Fehler ausgegeben.|`COMMIT TRAN`<br /><br /> `CREATE SESSION CUBE`<br /><br /> `ALTER CUBE`<br /><br /> `ALTER DIMENSION`<br /><br /> `CREATE DIMENSION MEMBER`<br /><br /> `DROP DIMENSION MEMBER`<br /><br /> `ALTER DIMENSION`<br /><br /> <br /><br /> Hinweis: Excel-Benutzer können die Gruppenfunktion in Pivottabellen nicht verwenden, da diese Funktion intern mit den `CREATE SESSION CUBE`-Befehlen implementiert wird.|  
|DMX-Anweisungen<br /><br /> <br /><br /> Hinweis: Beim Ausführen einer dieser Anweisungen wird ein Fehler ausgegeben.|`CREATE [SESSION] MINING STRUCTURE`<br /><br /> `ALTER MINING STRUCTURE`<br /><br /> `DROP MINING STRUCTURE`<br /><br /> `CREATE [SESSION] MINING MODEL`<br /><br /> `DROP MINING MODEL`<br /><br /> `IMPORT`<br /><br /> `SELECT INTO`<br /><br /> `INSERT`<br /><br /> `UPDATE`<br /><br /> `DELETE`|  
|Vorgänge im Hintergrund|Alle Hintergrundoperationen, die die Datenbank ändern würden, werden deaktiviert. Dies schließt die verzögerte Verarbeitung und proaktives Zwischenspeichern ein.|  
  
## <a name="readwritemode-usage"></a>Verwendung von ReadWriteMode  
 Die `ReadWriteMode`-Datenbankeigenschaft sollte im Rahmen eines `Attach`-Datenbankbefehls verwendet werden. Mit dem `Attach`-Befehl kann die Datenbankeigenschaft entweder auf `ReadWrite` oder auf `ReadOnly` festgelegt werden. Der `ReadWriteMode`-Datenbankeigenschaftswert kann nicht direkt aktualisiert werden, da die Eigenschaft als schreibgeschützt definiert ist. Datenbanken werden mit einer auf `ReadWriteMode` festgelegten `ReadWrite`-Eigenschaft erstellt. Eine Datenbank kann nicht im schreibgeschützten Modus erstellt werden.  
  
 Wenn Sie die `ReadWriteMode` -Daten Bank Eigenschaft zwischen und wechseln möchten `ReadWrite` `ReadOnly` , müssen Sie eine Sequenz von `Detach/Attach` Befehlen ausgeben.  
  
 Mit allen Datenbankvorgängen, mit Ausnahme von `Attach`, wird der aktuelle Status der `ReadWriteMode`-Datenbankeigenschaft beibehalten. Mit Vorgängen wie `Alter`, `Backup`, `Restore` und `Synchronize` wird beispielsweise der `ReadWriteMode`-Wert beibehalten.  
  
> [!NOTE]  
>  Lokale Cubes können aus einer schreibgeschützten Datenbank erstellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Anfügen und trennen von Analysis Services Datenbanken](attach-and-detach-analysis-services-databases.md)   
 [Verschieben einer Analysis Services Datenbank](move-an-analysis-services-database.md)   
 [Detach-Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [Attach-Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)  
  
  
