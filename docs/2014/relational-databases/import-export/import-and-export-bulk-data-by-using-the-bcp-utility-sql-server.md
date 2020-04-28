---
title: Importieren und Exportieren von Massendaten mithilfe des Hilfsprogramms bcp (SQL Server) | Microsoft-Dokumentation
ms.prod: sql-server-2014
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], bcp utility
- bulk importing [SQL Server], bcp utility
- bcp utility [SQL Server], about bcp utility
ms.assetid: 73e949de-67a3-4c84-9735-7da1ad4ba34a
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: ''
ms.custom: ''
ms.date: 06/14/2017
ms.openlocfilehash: 7075bf87ed64686750bc4a267af431268987ff35
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "71708212"
---
# <a name="import-and-export-bulk-data-by-using-the-bcp-utility-sql-server"></a>Importieren und Exportieren von Massendaten mithilfe des Hilfsprogramms bcp (SQL Server)

In diesem Thema erhalten Sie einen Überblick zum Verwenden des Hilfsprogramms [bcp](../../tools/bcp-utility.md) zum Exportieren von Daten von jeder Stelle innerhalb einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank, an der eine SELECT-Anweisung verwendet werden kann, einschließlich partitionierter Sichten.  
  
 Das Hilfsprogramm bcp (Bcp.exe) ist ein Befehlszeilentool, das die BCP-API (Bulk Copy Program) verwendet. Mit dem Hilfsprogramm bcp werden die folgenden Tasks ausgeführt:  
  
-   Massenexport von Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle in eine Datendatei.  
  
-   Massenexport von Daten aus einer Abfrage.  
  
-   Massenimport von Daten aus einer Datendatei in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle.  
  
-   Generieren von Formatdateien.  
  
 Auf das Hilfsprogramm „bcp“ wird über den Befehl **bcp** zugegriffen. Für den Massenimport von Daten mithilfe des Befehls **bcp** ist es erforderlich, das Schema der Tabelle und die Datentypen der Spalten zu verstehen, es sei denn, Sie verwenden eine bereits vorhandene Formatdatei.  
  
 Mit dem Hilfsprogramm "bcp" können Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle in eine Datendatei exportiert und dann in anderen Programmen verwendet werden. Das Hilfsprogramm kann auch dazu verwendet werden, Daten aus einem anderen Programm, meist einem anderen Datenbank-Managementsystem (DBMS, Database Management System), in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle zu importieren. Die Daten werden zuerst aus dem Quellprogramm in eine Datendatei exportiert und dann, in einem getrennten Vorgang, aus der Datendatei in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle kopiert.  
  
 Der Befehl **bcp** stellt Schalter bereit, mit denen Sie den Datentyp der Datendatei und andere Informationen angeben. Wenn diese Schalter nicht angegeben werden, werden vom Befehl Formatierungsinformationen (z. B. der Typ der Datenfelder in einer Datendatei) abgefragt. Anschließend müssen Sie festlegen, ob Sie eine Formatdatei mit Ihren interaktiven Antworten erstellen möchten. Eine Formatdatei ist oft hilfreich, wenn Sie für zukünftige Massenimport- oder Massenexportvorgänge flexibel sein müssen. Sie können die Formatdatei bei späteren **bcp** -Befehlen für äquivalente Datendateien angeben. Weitere Informationen finden Sie unter [Angeben von Datenformaten für die Kompatibilität bei Verwendung von „bcp“ &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).  
  
> [!NOTE]  
>  Das bcp-Hilfsprogramm wird mithilfe der ODBC-Massenkopierung geschrieben.  
  
 Eine Beschreibung der **bcp** -Befehlssyntax finden Sie unter [bcp (Hilfsprogramm)](../../tools/bcp-utility.md).  
  
## <a name="examples"></a>Beispiele

 **bcp**-Beispiele finden Sie unter:  
  
-   [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)  
  
-   [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Beispiele für den Massenimport und -export von XML-Dokumenten &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Beibehalten von Identitätswerten beim Massenimport von Daten &#40;SQL Server&#41;](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Beibehalten von NULL-Werten oder Verwenden von Standardwerten während des Massenimports &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
-   [Massenimport von Daten mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  

## <a name="see-also"></a>Weitere Informationen

[INSERT &#40;Transact-SQL-&#41;](/sql/t-sql/statements/insert-transact-sql) 
 [SELECT-Klausel &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) 
 [bcp-Hilfsprogramm](../../tools/bcp-utility.md)   
[Vorbereiten des Massen Imports von Daten &#40;SQL Server&#41;](prepare-to-bulk-import-data-sql-server.md) 
 [Bulk Insert &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 
 [Massen Import und-Export von Daten #b4 ](bulk-import-and-export-of-data-sql-server.md) 
SQL Server&#41;&#40;&#41;&#40;SQL Server von [Transact-SQL ](/sql/t-sql/functions/openrowset-transact-sql) 
 [&#41;](create-a-format-file-sql-server.md)