---
title: Angeben von Datenformaten für die Kompatibilität bei Verwendung von bcp (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], compatibility
- bulk importing [SQL Server], compatibility
- compatibility [SQL Server], data formats
- data formats [SQL Server], compatibility
- bcp utility [SQL Server], compatibility
ms.assetid: cd5fc8c8-eab1-4165-9468-384f31e53f0a
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 42266e1f4ab136045c16d1e0f41d6ae802c3f1c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37154541"
---
# <a name="specify-data-formats-for-compatibility-when-using-bcp-sql-server"></a>Angeben von Datenformaten für die Kompatibilität bei Verwendung von bcp (SQL Server)
  In diesem Thema wird beschrieben, die datenformatattribute, feldspezifischen eingabeaufforderungen und das Speichern von Feld-nach-Feld-Daten in einer nicht-XML-Formatdatei, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `bcp` Befehl. Das Verständnis dieser Konzepte kann für Sie nützlich sein, wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten für den Massenimport in ein anderes Programm, z. B. ein anderes Datenbankprogramm, mit einem Massenexportvorgang exportieren. Die Standarddatenformate in (systemeigen, Zeichen oder Unicode) der Quelltabelle können mit dem vom anderen Programm erwarteten Datenlayout inkompatibel sein. Falls eine Inkompatibilität vorliegt, müssen Sie beim Exportieren von Daten das Datenlayout beschreiben.  
  
> [!NOTE]  
>  Wenn Sie keine Erfahrung mit Datenformaten zum Importieren oder Exportieren von Daten haben, finden Sie Informationen unter [Datenformate für Massenimport oder Massenexport &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md).  
  
 **In diesem Thema:**  
  
-   [Bcp-Datenformatattribute](#bcpDataFormatAttr)  
  
-   [Übersicht über die feldspezifischen Eingabeaufforderungen](#FieldSpecificPrompts)  
  
-   [Das Speichern von Feld-nach-Feld-Daten in einer nicht-XML-Formatdatei](#FieldByFieldNonXmlFF)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="bcpDataFormatAttr"></a> bcp-Datenformatattribute  
 Mit dem Befehl `bcp` können Sie die Struktur jedes Felds in einer Datendatei im Hinblick auf die folgenden Datenformatattribute angeben:  
  
-   Dateispeichertyp  
  
     Der *Dateispeichertyp* beschreibt, wie Daten in der Datendatei gespeichert werden. Daten können in eine Datendatei als Typ der Datenbanktabelle (systemeigenes Format) exportiert werden, als zeichendarstellung (Zeichenformat) oder als beliebiger Datentyp, in dem implizite Konvertierung unterstützt wird; Kopieren Sie z. B. eine `smallint` als ein `int`. Benutzerdefinierte Datentypen werden als Basistypen exportiert. Weitere Informationen finden Sie unter [Angeben des Dateispeichertyps mithilfe von bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md).  
  
-   Präfixlänge  
  
     Als kompakteste Form der Dateispeicherung beim Massenexportieren von Daten im systemeigenen Format in eine Datendatei setzt der Befehl `bcp` mindestens ein Zeichen, das auf die Länge des Felds hinweist, vor jedes Feld. Diese Zeichen werden als *Längenpräfixzeichen* bezeichnet. Weitere Informationen finden Sie unter [Angeben der Präfixlänge in Datendateien mittels bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md).  
  
-   Feldlänge  
  
     Die Feldlänge weist auf die maximale Anzahl von Zeichen hin, die zum Darstellen der Daten im Zeichenformat benötigt werden. Die Feldlänge ist bereits bekannt, wenn die Daten im systemeigenen Format gespeichert werden. Weitere Informationen finden Sie unter [Angeben der Feldlänge mithilfe von bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md).  
  
-   Feldabschlusszeichen  
  
     Für Zeichendatenfelder kann mit optionalen abschließenden Zeichen das Ende jedes Felds in einer Datendatei (mithilfe eines *Feldabschlusszeichens*) und das Ende jeder Zeile (mithilfe eines *Zeilenabschlusszeichens*) markiert werden. Abschließende Zeichen sind eine Möglichkeit, um Programme, die die Datendatei lesen, darauf hinzuweisen, an welcher Stelle ein Feld oder eine Zeile endet und ein anderes Feld bzw. eine andere Zeile beginnt. Weitere Informationen finden Sie unter [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).  
  
##  <a name="FieldSpecificPrompts"></a> Übersicht über die feldspezifischen Eingabeaufforderungen  
 Wenn ein interaktiver `bcp` -Befehl enthält die **in** oder **out** option enthält jedoch auch keine entweder den formatdateischalter (**-f**) oder ein Datenformat wechseln () **- n**, **- C**, **-w**, oder **-N**), jede Spalte in der Quelle oder Ziel-Tabelle, die eingabeaufforderungen für jedes der vorangehenden Attribute, wiederum. Jede Eingabeaufforderung die `bcp` Befehl stellt einen Standardwert, der auf der Grundlage der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Datentyp der Spalte der Tabelle. Wenn Sie den Standardwert für alle Eingabeaufforderungen übernehmen, erhalten Sie dieselben Ergebnisse wie beim Angeben des systemeigenen Formats (**-n**) in der Befehlszeile. Für jede Eingabeaufforderung wird ein Standardwert in eckigen Klammern angezeigt: [*Standard*]. Durch Drücken der EINGABETASTE wird der angezeigte Standardwert übernommen. Wenn Sie einen Wert angeben möchten, der vom Standardwert abweicht, geben Sie den neuen Wert an der Eingabeaufforderung ein.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `bcp` Befehl für das Exportieren von Daten aus der `HumanResources.myTeam` -Tabelle interaktiv in die `myTeam.txt` Datei. Bevor Sie das Beispiel ausführen können, müssen Sie diese Tabelle erstellen. Informationen zu dieser Tabelle und zum Erstellen der Tabelle finden Sie unter [HumanResources.myTeam-Beispieltabelle &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md).  
  
 Der Befehl gibt weder eine Formatdatei noch einen Datentyp verursacht `bcp` zur Eingabe von Datenformatinformationen auffordert. Geben Sie an der Eingabeaufforderung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Folgendes ein:  
  
```  
bcp AdventureWorks.HumanResources.myTeam out myTeam.txt -T  
```  
  
 bcp fordert für jede Spalte zur Eingabe feldspezifischer Werte auf. Das folgende Beispiel zeigt die feldspezifischen Eingabeaufforderungen für die Spalten `EmployeeID` und `Name` der Tabelle und schlägt den Standard-Dateispeichertyp (systemeigenes Format) für jede Spalte vor. Die Präfixlängen der Spalten `EmployeeID` und `Name` betragen 0 bzw. 2. Der Benutzer gibt ein Komma (`,`) als Feldabschlusszeichen für jedes Feld an.  
  
 `Enter the file storage type of field EmployeeID [smallint]:`  
  
 `Enter prefix-length of field EmployeeID [0]:`  
  
 `Enter field terminator [none]:,`  
  
 `Enter the file storage type of field Name [nvarchar]:`  
  
 `Enter prefix length of field Name [2]:`  
  
 `Enter field terminator [none]:,`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 Gleichwertige Eingabeaufforderungen (soweit erforderlich) werden für jede Tabellenspalte angezeigt.  
  
##  <a name="FieldByFieldNonXmlFF"></a> Speichern von feldspezifischen Daten in einer Nicht-XML-Formatdatei  
 Nachdem alle der Tabelle Spalten angegeben wurden, die `bcp` Befehl fordert Sie auf das optional eine nicht-XML-Formatdatei generiert werden soll, in dem die Feld-nach-Feld Informationen gerade eingegebenen (siehe vorheriges Beispiel) gespeichert. Wenn Sie eine Formatdatei generieren, können Sie diese beim Exportieren von Daten aus dieser Tabelle oder Importieren identisch strukturierter Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwenden.  
  
> [!NOTE]  
>  Mithilfe der Formatdatei können Sie Daten aus der Datendatei in eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] massenimportieren oder Daten aus der Tabelle massenexportieren, ohne das Format erneut angeben zu müssen. Weitere Informationen finden Sie unter [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
 Das folgende Beispiel erstellt die Nicht-XML-Formatdatei `myFormatFile.fmt`:  
  
 `Do you want to save this format information in a file? [Y/n] y`  
  
 `Host filename: [bcp.fmt]myFormatFile.fmt`  
  
 Der Standardname der Formatdatei ist bcp.fmt, Sie können aber einen anderen Dateinamen angeben.  
  
> [!NOTE]  
>  Für eine Datendatei, die ein einziges Datenformat für den Dateispeichertyp verwendet, wie z.B. das Zeichenformat oder das native Format, können Sie mit der Option **format** schnell eine Formatdatei erstellen, ohne Daten zu exportieren oder zu importieren. Diese Vorgehensweise hat den Vorteil, dass sie einfach ist und die Möglichkeit bietet, eine XML-Formatdatei oder eine Nicht-XML-Formatdatei zu erstellen. Weitere Informationen finden Sie unter [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Angeben des Dateispeichertyps mithilfe von bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
-   [Angeben der Präfixlänge in Datendateien mittels bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [Angeben der Feldlänge mithilfe von bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)  
  
-   [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Keine.  
  
## <a name="see-also"></a>Siehe auch  
 [Massenimport und -export von Daten &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)   
 [Datenformate für Massenimport oder Massenexport &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
