---
title: Tabelleneigenschaften | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.tableproperties.storage.f1
- sql12.SWB.SELECTCOLUMNS.F1
- sql12.swb.tableproperties.filetable.f1
- sql12.swb.tableproperties.general.f1
- sql12.swb.tableproperties.changetracking.f1
ms.assetid: ad8a2fd4-f092-4c0f-be85-54ce8b9d725a
caps.latest.revision: 43
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e5b9ecfeafbb989f5baae832225475e65137a9ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150752"
---
# <a name="table-properties"></a>Tabelleneigenschaften
  In diesem Thema werden die Tabelleneigenschaften beschrieben, die im Dialogfeld "Tabelleneigenschaften" in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]angezeigt werden. Weitere Informationen zum Anzeigen dieser Eigenschaften finden Sie unter [Anzeigen der Tabellendefinition](view-the-table-definition.md).  
  
 **In diesem Thema**  
  
1.  [Seite Allgemein](#GeneralPage)  
  
2.  [Seite "Änderungsnachverfolgung"](#ChangeTracking)  
  
3.  [FileTable-Seite](#FileTable)  
  
4.  [Seite "Speicher"](#Storage)  
  
##  <a name="GeneralPage"></a> Seite Allgemein  
 **Datenbank**  
 Name der Datenbank, die diese Tabelle enthält.  
  
 **Server**  
 Name der aktuellen Serverinstanz.  
  
 **Benutzer**  
 Name des Benutzers dieser Verbindung.  
  
 **Erstellt am**  
 Datum und Uhrzeit der Erstellung der Tabelle.  
  
 **Name**  
 Der Name der Tabelle.  
  
 **Schema**  
 Schema, das Besitzer der Tabelle ist.  
  
 **Systemobjekt**  
 Gibt an, dass diese Tabelle eine Systemtabelle ist, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Speichern interner Informationen verwendet wird. Benutzer dürfen Systemtabellen nicht direkt ändern bzw. auf sie verweisen.  
  
 **ANSI NULLS**  
 Gibt an, ob das Objekt mit der Option ANSI NULLS auf ON erstellt wurde. Weitere Informationen finden Sie unter [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)  
  
 **Bezeichner in Anführungszeichen**  
 Gibt an, ob das Objekt mit der Option „Bezeichner in Anführungszeichen“ auf ON erstellt wurde. Weitere Informationen finden Sie unter [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)  
  
 **Sperrenausweitung**  
 Gibt die Granularität der Sperrenausweitung der Tabelle an. Weitere Informationen zum Sperren in der Datenbank-Engine finden Sie im [Handbuch zu Transaktionssperren und Zeilenversionsverwaltung in SQL Server](http://msdn.microsoft.com/library/jj856598.aspx). Folgende Werte sind möglich:  
  
 AUTO  
 Mit dieser Option kann von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die für das Tabellenschema geeignete Granularität der Sperrenausweitung ausgewählt werden.  
  
-   Wenn die Tabelle partitioniert ist, ist die Sperrenausweitung bis zur Heap- oder B-Struktur (HoBT)-Granularität zulässig. Nach der Ausweitung der Sperre auf die HoBT-Ebene wird die Sperrenausweitung nicht bis zur TABLE-Granularität fortgeführt.  
  
-   Wenn die Tabelle nicht partitioniert ist, wird die Sperre bis zur TABLE-Granularität ausgeweitet.  
  
 TABLE  
 Die Sperrenausweitung wird immer mit der Granularität der Tabellenebene ausgeführt, unabhängig davon, ob die Tabelle partitioniert ist. TABLE ist der Standardwert.  
  
 DISABLE  
 Verhindert die Sperrenausweitung in den meisten Fällen. Sperren auf Tabellenebene sind jedoch nicht völlig ausgeschlossen. Wenn Sie z. B. eine Tabelle scannen, die unter der serialisierbaren Isolationsstufe keinen gruppierten Index aufweist, muss [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine Tabellensperre zulassen, damit die Datenintegrität gewahrt wird.  
  
 **Die Tabelle ist repliziert**  
 Gibt an, ob die Tabelle mit der Replikationsfunktion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in eine andere Datenbank repliziert wurde. Mögliche Werte sind `True` oder `False`.  
  
##  <a name="ChangeTracking"></a> Seite "Änderungsnachverfolgung"  
 **Änderungsnachverfolgung**  
 Gibt an, ob die Änderungsnachverfolgung für die Tabelle aktiviert ist. Der Standardwert lautet `False`.  
  
 Diese Option ist nur dann verfügbar, wenn die Änderungsnachverfolgung für die Datenbank aktiviert ist.  
  
 Zur Aktivierung der Änderungsnachverfolgung muss die Tabelle einen Primärschlüssel enthalten, und Sie müssen über die Berechtigung zur Änderung der Tabelle verfügen. Sie können die Änderungsnachverfolgung mithilfe von [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)konfigurieren.  
  
 **Aktualisierte Spalten nachverfolgen**  
 Gibt an, ob [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verfolgt, welche Spalten aktualisiert wurden.  
  
 Weitere Informationen zur Änderungsnachverfolgung finden Sie unter [Informationen zur Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).  
  
##  <a name="FileTable"></a> FileTable-Seite  
 Zeigt die auf FileTables bezogenen Eigenschaften der Tabelle an. Weitere Informationen finden Sie unter [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).  
  
 **Sortierung der FileTable-Namensspalte**  
 Die Sortierung, die in einer FileTable auf die Spalte **Name** angewendet wird. Die Spalte **Name** enthält Datei- und Verzeichnisnamen.  
  
 **Name des FileTable-Verzeichnisses**  
 Der Stammordner für die FileTable.  
  
 **Aktivierter FileTable-Namespace**  
 Wenn `True`, gibt dieser Wert an, dass die Tabelle eine FileTable ist. Wenn Sie diesen Wert in `False` ändern, ändern Sie die FileTable in eine gewöhnliche Benutzertabelle. Wenn Sie die Tabelle später wieder in eine FileTable ändern möchten, muss die Tabelle eine FileTable-Konsistenzprüfung bestehen, damit die Konvertierung erfolgreich ist.  
  
##  <a name="Storage"></a> Seite "Speicher"  
 Zeigt die speicherbezogenen Eigenschaften der ausgewählten Tabelle an.  
  
### <a name="compression"></a>Komprimierung  
 **Komprimierungstyp**  
 Der Komprimierungstyp der Tabelle. Diese Eigenschaft ist nur für nicht partitionierte Tabellen verfügbar. Weitere Informationen finden Sie unter [Data Compression](../data-compression/data-compression.md).  
  
 **Partitionen mit Seitenkomprimierung**  
 Die Nummern der Partitionen, für die die Seitenkomprimierung verwendet wird. Diese Eigenschaft ist nur für partitionierte Tabellen verfügbar.  
  
 **Nicht komprimierte Partitionen**  
 Die Nummern der nicht komprimierten Partitionen. Diese Eigenschaft ist nur für partitionierte Tabellen verfügbar.  
  
 **Partitionen mit Zeilenkomprimierung**  
 Die Nummern der Partitionen, für die die Zeilenkomprimierung verwendet wird. Diese Eigenschaft ist nur für partitionierte Tabellen verfügbar.  
  
### <a name="filegroup"></a>Dateigruppe  
 **Textdateigruppe**  
 Name der Dateigruppe, die die Textdaten für die Tabelle enthält.  
  
 **Dateigruppe**  
 Der Name der Dateigruppe, die die Tabelle enthält.  
  
 **Die Tabelle ist partitioniert**  
 Mögliche Werte sind `True` und `False`.  
  
 **FILESTREAM-Dateigruppe**  
 Geben Sie den Namen der FILESTREAM-Datendateigruppe, wenn die Tabelle besitzt eine `varbinary(max)` Spalte, die FILESTREAM-Attribut aufweist. Der Standardwert entspricht der standardmäßigen FILESTREAM-Datendateigruppe.  
  
 Wenn die Tabelle keine FILESTREAM-Daten enthält, ist das Feld leer.  
  
### <a name="general"></a>Allgemein  
 **Das VarDecimal-Speicherformat ist aktiviert.**  
 Wenn `True`, dieser schreibgeschützte Wert gibt an, dass `decimal` und `numeric` Datentypen mithilfe des vardecimal-Speicherformats gespeichert werden. Um diese Option zu ändern, verwenden die `vardecimal storage format` Option [Sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql). Das Vardecimal-Speicherformat ist veraltet. Verwenden Sie stattdessen die ROW-Komprimierung.  
  
 **Indexspeicher**  
 Der Speicherplatz in Megabytes, der von den Indizes in der Tabelle belegt wird. Dieser Wert schließt die Speicherverwendung für den XML-Index der Tabelle nicht mit ein. Verwenden Sie stattdessen [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) , wenn XML-Indizes zur Tabelle gehören.  
  
 **Zeilenanzahl**  
 Anzahl der Zeilen in der Tabelle.  
  
 **Datenspeicher**  
 Der Speicherplatz in Megabytes, der von den Daten in der Tabelle belegt wird.  
  
### <a name="partitioning"></a>Partitionierung  
 Dieser Abschnitt ist nur verfügbar, wenn die Tabelle partitioniert ist. Weitere Informationen finden Sie unter [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).  
  
 **Partitionsspalte**  
 Der Name der Spalte, nach der die Tabelle partitioniert ist.  
  
 **Partitionsschema**  
 Der Name des Partitionsschemas, sofern die Tabelle partitioniert ist. Wenn die Tabelle nicht partitioniert ist, ist das Feld leer.  
  
 **Anzahl Partitionen**  
 Die Anzahl von Partitionen in der Tabelle.  
  
 **FILESTREAM-Partitionsschema**  
 Der Name des FILESTREAM-Partitionsschemas, sofern die Tabelle partitioniert ist. Wenn die Tabelle nicht partitioniert ist, ist das Feld leer.  
  
 Das FILESTREAM-Partitionsschema muss mit dem Schema symmetrisch sein, das in der Option **Partitionsschema** angegeben ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen der Tabellendefinition](view-the-table-definition.md)   
 
  [Ändern von Spalten &amp;#40;Datenbank-Engine&amp;#41;](../tables/modify-columns-database-engine.md)  
  
  
