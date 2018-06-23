---
title: Angeben des Dateispeichertyps mithilfe von bcp (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bcp utility [SQL Server], file storage types
- importing data, file storage types
- native data format [SQL Server]
- file storage types [SQL Server]
- data formats [SQL Server], file storage types
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 68630ac6e4a2ffad9079ed620e8d7d9660bf6381
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050308"
---
# <a name="specify-file-storage-type-by-using-bcp-sql-server"></a>Angeben des Dateispeichertyps mithilfe von bcp (SQL Server)
  Der *Dateispeichertyp* beschreibt, wie Daten in der Datendatei gespeichert werden. Daten können in eine Datendatei als Typ der Datenbanktabelle (systemeigenes Format) exportiert werden, in die zeichendarstellung (Zeichenformat) oder als beliebiger Datentyp, in dem implizite Konvertierung unterstützt wird; Kopieren Sie z. B. eine `smallint` als ein `int`. Benutzerdefinierte Datentypen werden als Basistypen exportiert.  
  
## <a name="the-bcp-prompt-for-file-storage-type"></a>Die bcp-Eingabeaufforderung für den Dateispeichertyp  
 Wenn ein interaktiver **bcp** -Befehl die Option **in** oder **out** , jedoch keinen Formatdateischalter (**-f**) bzw. keinen Datenformatschalter (**-n**, **-c**, **-w**oder **-N**) enthält, fordert der Befehl wie folgt zur Eingabe des Dateispeichertyps für jedes Datenfeld auf:  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 Ihre Eingabe hängt dann von der Aufgabe ab, die Sie ausführen möchten (siehe folgende Liste).  
  
-   Wenn Sie Daten von einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in eine Datendatei der kompaktesten Speicherform, die möglich ist (systemeigenes Datenformat), massenexportieren möchten, nehmen Sie die Standard-Dateispeichertypen an, die von **bcp**bereitgestellt werden. Eine Liste der systemeigenen Dateispeichertypen finden Sie unter "Systemeigene Dateispeichertypen" weiter unten in diesem Thema.  
  
-   Zum massenexportieren von Daten aus einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in eine Datendatei im Zeichenformat geben `char` als Dateispeichertyp für alle Spalten in der Tabelle.  
  
-   Massenimport von Daten mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus einer Datendatei Geben Sie den Dateispeichertyp als `char` für Typen, die im Zeichenformat gespeichert formatieren und für im systemeigenen Datentypformat gespeicherte Daten, geben Sie einen der Dateitypen Speicher nach Bedarf:  
  
    |Dateispeichertyp|Eingabe an der Eingabeaufforderung|  
    |-----------------------|-----------------------------|  
    |`char` <sup>1</sup>|`c`[`har`]|  
    |`varchar`|`c[har]`|  
    |`nchar`|`w`|  
    |`nvarchar`|`w`|  
    |`text` <sup>2</sup>|`T`[`ext`]|  
    |`ntext2`|`W`|  
    |`binary`|`x`|  
    |`varbinary`|`x`|  
    |`image` <sup>2</sup>|`I`[`mage`]|  
    |`datetime`|**d[ate]**|  
    |`smalldatetime`|`D`|  
    |`time`|`te`|  
    |`date`|`de`|  
    |`datetime2`|`d2`|  
    |`datetimeoffset`|`do`|  
    |`decimal`|`n`|  
    |`numeric`|`n`|  
    |`float`|**f[loat]**|  
    |`real`|`r`|  
    |`Int`|**i[nt]**|  
    |`bigint`|`B[igint]`|  
    |`smallint`|**s[mallint]**|  
    |`tinyint`|**t[inyint]**|  
    |`money`|**m[oney]**|  
    |`smallmoney`|`M`|  
    |`bit`|`b[it]`|  
    |`uniqueidentifier`|`u`|  
    |`sql_variant`|`V[ariant]`|  
    |`timestamp`|`x`|  
    |`UDT` (ein benutzerdefinierter Datentyp)|`U`|  
    |`XML`|`X`|  
  
     <sup>1</sup> die Interaktion für Feldlänge, Präfixlänge und Abschlusszeichen bestimmt die Menge des Speicherplatzes, der in einer Datendatei für nicht auf Zeichen basierende Daten zugeordnet ist, der als exportiert wird die `char` -Dateispeichertyp.  
  
     <sup>2</sup> der `ntext`, `text`, und `image` Datentypen werden in einer zukünftigen Version von entfernt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vermeiden Sie den Gebrauch dieser Datentypen bei neuen Entwicklungen, und richten Sie sich auf die Änderung von Anwendungen ein, in denen sie zurzeit verwendet werden. Verwendung `nvarchar(max)`, `varchar(max)`, und `varbinary(max)` stattdessen.  
  
## <a name="native-file-storage-types"></a>Systemeigene Dateispeichertypen  
 Jeder systemeigene Speichertyp wird in der Formatdatei als entsprechender Datentyp der Hostdatei aufgezeichnet.  
  
|Dateispeichertyp|Datentyp in der Hostdatei|  
|-----------------------|-------------------------|  
|`char` <sup>1</sup>|SQLCHAR|  
|`varchar`|SQLCHAR|  
|`nchar`|SQLNCHAR|  
|`nvarchar`|SQLNCHAR|  
|`text` <sup>2</sup>|SQLCHAR|  
|`ntext` <sup>2</sup>|SQLNCHAR|  
|`binary`|SQLBINARY|  
|`varbinary`|SQLBINARY|  
|`image` <sup>2</sup>|SQLBINARY|  
|`datetime`|SQLDATETIME|  
|`smalldatetime`|SQLDATETIM4|  
|`decimal`|SQLDECIMAL|  
|`numeric`|SQLNUMERIC|  
|`float`|SQLFLT8|  
|`real`|SQLFLT4|  
|`int`|SQLINT|  
|`bigint`|SQLBIGINT|  
|`smallint`|SQLSMALLINT|  
|`tinyint`|SQLTINYINT|  
|`money`|SQLMONEY|  
|`smallmoney`|SQLMONEY4|  
|`bit`|SQLBIT|  
|`uniqueidentifier`|SQLUNIQUEID|  
|`sql_variant`|SQLVARIANT|  
|`timestamp`|SQLBINARY|  
|UDT (ein benutzerdefinierter Datentyp)|SQLUDT|  
  
 <sup>1</sup> -Datendateien, die im Zeichenformat gespeichert sind, formatieren verwenden `char` als Dateispeichertyp. SQLCHAR ist deshalb für Zeichendatendateien der einzige Datentyp, der in einer Formatdatei aufgeführt ist.  
  
 <sup>2</sup> kann nicht beim Massenimport von Daten in `text`, `ntext`, und `image` Spalten, die über Standardwerte verfügen.  
  
## <a name="additional-considerations-for-file-storage-types"></a>Zusätzliche Aspekte von Dateispeichertypen  
 Beachten Sie beim Massenexport von Daten aus einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in eine Datendatei Folgendes:  
  
-   Sie können jederzeit `char` als Dateispeichertyp angeben.  
  
-   Wenn Sie einen Dateispeichertyp eingeben, der eine ungültige implizite Konvertierung darstellt **Bcp** ein Fehler auftritt; z. B., aber Sie können angeben `int` für `smallint` Daten, wenn Sie angeben, `smallint` für `int` Daten Überlauffehlern.  
  
-   Wenn nicht auf Zeichen basierende Datentypen wie `float`, `money`, `datetime`, oder `int` gespeichert werden als entsprechende Datenbanktypen bezieht sich die Daten in die Datendatei in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] systemeigenen Format.  
  
    > [!NOTE]  
    >  Nachdem Sie interaktiv alle Felder in einem **bcp**-Befehl angegeben haben, werden Sie vom Befehl dazu aufgefordert, Ihre Antworten für die einzelnen Felder in einer Nicht-XML-Formatdatei zu speichern. Weitere Informationen zu Nicht-XML-Formatdateien finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Angeben der Feldlänge mithilfe von bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)   
 [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)   
 [Angeben der Präfixlänge in Datendateien mittels bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  
