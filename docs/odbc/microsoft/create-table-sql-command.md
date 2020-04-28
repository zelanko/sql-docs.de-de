---
title: CREATE TABLE-SQL-Befehl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE TABLE [ODBC]
ms.assetid: be2143ba-fc16-42c9-84f7-8985cd924860
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dfc80a56a021b1bfeda38115e79f7086632900c8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298690"
---
# <a name="create-table---sql-command"></a>CREATE TABLE (SQL-Befehl)
Erstellt eine Tabelle mit den angegebenen Feldern.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiber spezifische Informationen finden Sie unter **Treiber Hinweise**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CREATE TABLE | DBF TableName1 [NAME LongTableName] [FREE]  
   (FieldName1FieldType [(nFieldWidth [, nPrecision])]  
      [NULL | NOT NULL]   
      [CHECK lExpression1 [ERROR cMessageText1]]  
      [DEFAULT eExpression1]  
      [PRIMARY KEY | UNIQUE]  
      [REFERENCES TableName2 [TAG TagName1]]  
      [NOCPTRANS]  
   [, FieldName2 ...]  
      [, PRIMARY KEY eExpression2 TAG TagName2  
      |, UNIQUE eExpression3 TAG TagName3]  
      [, FOREIGN KEY eExpression4 TAG TagName4 [NODUP]  
            REFERENCES TableName3 [TAG TagName5]]  
      [, CHECK lExpression2 [ERROR cMessageText2]])  
| FROM ARRAY ArrayName  
```  
  
## <a name="arguments"></a>Argumente  
 CREATE TABLE &#124; DBF- *TableName1*  
 Gibt den Namen der zu erstellenden Tabelle an. Die Tabellen-und DBF-Optionen sind identisch.  
  
 Name *LongTableName*  
 Gibt einen langen Namen für die Tabelle an. Ein Long-Tabellenname kann nur angegeben werden, wenn eine Datenbank geöffnet ist, da lange Tabellennamen in-Datenbanken gespeichert werden.  
  
 Lange Namen können bis zu 128 Zeichen enthalten und können anstelle von kurzen Dateinamen in der Datenbank verwendet werden.  
  
 FREE  
 Gibt an, dass die Tabelle nicht zu einer geöffneten Datenbank hinzugefügt wird. "Free" ist nicht erforderlich, wenn eine Datenbank nicht geöffnet ist.  
  
 *(FieldName1 FieldType* [( *nfieldwidth* [, *nprecision*])]  
 Gibt den Feldnamen, den Feldtyp, die Feldbreite und die Feld Genauigkeit (Anzahl der Dezimalstellen) an.  
  
 *FieldType* ist ein einzelner Buchstabe, der den [Datentyp](../../odbc/microsoft/visual-foxpro-field-data-types.md)des Felds angibt. Einige Feld Datentypen erfordern, dass Sie *nfieldwidth* oder *nprecision* oder beides angeben.  
  
 *nfieldwidth* und *nprecision* werden für die Typen D, G, I, L, M, P, T und Y ignoriert. *nprecision* ist standardmäßig auf 0 (keine Dezimalstellen) festgelegt, wenn *nprecision* für die Typen B, F oder N nicht eingeschlossen ist.  
  
 NULL  
 Lässt NULL-Werte im-Feld zu.  
  
 NOT NULL  
 Verhindert NULL-Werte im-Feld.  
  
 Wenn Sie NULL und NOT NULL weglassen, bestimmt die aktuelle Einstellung von SET NULL, ob NULL-Werte im Feld zulässig sind. Wenn Sie jedoch NULL und NOT NULL weglassen und die PRIMARY KEY-oder Unique-Klausel einschließen, wird die aktuelle Einstellung von SET NULL ignoriert, und das Feld ist standardmäßig auf NOT NULL festgelegt.  
  
 *LExpression1* überprüfen  
 Gibt eine Validierungs Regel für das Feld an. *lExpression1* kann eine benutzerdefinierte Funktion sein. Wenn ein leerer Datensatz angehängt wird, wird die Validierungs Regel überprüft. Ein Fehler wird generiert, wenn die Validierungs Regel keinen leeren Feldwert in einem angefügten Datensatz zulässt.  
  
 Fehler *cMessageText1*  
 Gibt die Fehlermeldung an, die Visual FoxPro anzeigt, wenn die Feldregel einen Fehler generiert. Die Meldung wird nur angezeigt, wenn Daten in einem Fenster zum Durchsuchen oder einem Bearbeitungsfenster geändert werden.  
  
 Standard *eExpression1*  
 Gibt einen Standardwert für das Feld an. Der Datentyp von *eExpression1* muss mit dem Datentyp des Felds identisch sein.  
  
 PRIMARY KEY  
 Erstellt einen primären Index für das Feld. Das primäre Indextag hat denselben Namen wie das Feld.  
  
 UNIQUE  
 Erstellt einen Kandidaten Index für das Feld. Das Kandidaten Indextag hat denselben Namen wie das Feld.  
  
> [!NOTE]  
>  Kandidaten Indizes (erstellt durch einschließen der UNIQUE-Option in CREATE TABLE oder ALTER TABLE-SQL) sind nicht identisch mit Indizes, die mit der UNIQUE-Option im Index-Befehl erstellt wurden. Ein mit der UNIQUE-Option im Index-Befehl erstellter Index ermöglicht doppelte Index Schlüssel. Kandidaten Indizes lassen keine doppelten Index Schlüssel zu. Weitere Informationen zur eindeutigen Option finden Sie unter [Index](../../odbc/microsoft/index-command.md) .  
  
 NULL-Werte und doppelte Datensätze sind in einem Feld, das für einen primären Index oder einen Kandidaten Index verwendet wird, nicht zulässig. Visual FoxPro generiert jedoch keinen Fehler, wenn Sie einen primären Index oder einen Kandidaten Index für ein Feld erstellen, das NULL-Werte unterstützt. Visual FoxPro generiert einen Fehler, wenn Sie versuchen, einen NULL-oder einen doppelten Wert in ein Feld einzugeben, das für einen primären oder einen Kandidaten Index verwendet wird.  
  
 Verweise *TableName2*[Tag *TagName1*]  
 Gibt die übergeordnete Tabelle an, mit der eine persistente Beziehung hergestellt wird. Wenn Sie Tag *TagName1*weglassen, wird die Beziehung mit dem primär Index Schlüssel der übergeordneten Tabelle hergestellt. Wenn die übergeordnete Tabelle keinen primären Index hat, generiert Visual FoxPro einen Fehler.  
  
 TagTagName1 *TagName1* einschließen, um eine Beziehung basierend auf einem vorhandenen Indextag für die übergeordnete Tabelle herzustellen. Indextagnamen können bis zu 10 Zeichen enthalten.  
  
 Die übergeordnete Tabelle darf keine freie Tabelle sein.  
  
 Nocptrans  
 Verhindert die Übersetzung in eine andere Codepage für Zeichen-und Memo Felder. Wenn die Tabelle in eine andere Codepage konvertiert wird, werden die Felder, für die "nocptrans" angegeben wurde, nicht übersetzt. "Nocptrans" kann nur für Zeichen-und Memo Felder angegeben werden.  
  
 Im folgenden Beispiel wird eine Tabelle mit dem Namen MyTable erstellt, die zwei Zeichenfelder und zwei Memo Felder enthält. Das zweite Zeichenfeld, char2 und das zweite Memo Feld memo2, enthalten "nocptrans", um die Übersetzung zu verhindern.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 Primärschlüssel *eExpression2* Tag *TagName2*  
 Gibt einen primär Index an, der erstellt werden soll. *eExpression2* gibt ein beliebiges Feld oder eine Kombination von Feldern in der Tabelle an. Tag *TagName2* gibt den Namen für das primäre Indextag an, das erstellt wird. Indextagnamen können bis zu 10 Zeichen enthalten.  
  
 Da eine Tabelle nur einen primären Index aufweisen kann, können Sie diese Klausel nicht einschließen, wenn Sie bereits einen primären Index für ein Feld erstellt haben. Visual FoxPro generiert einen Fehler, wenn Sie mehr als eine PRIMARY KEY-Klausel in CREATE TABLE einschließen.  
  
 Eindeutiges *eExpression3*-Tag *TagName3*  
 Erstellt einen Kandidaten Index. *eExpression3* gibt ein beliebiges Feld oder eine Kombination von Feldern in der Tabelle an. Wenn Sie jedoch einen primären Index mit einer der Primärschlüssel Optionen erstellt haben, können Sie nicht das Feld einschließen, das für den primären Index angegeben wurde. Tag *TagName3* gibt einen Tagnamen für das Kandidaten Indextag an, das erstellt wird. Indextagnamen können bis zu 10 Zeichen enthalten.  
  
 Eine Tabelle kann über mehrere Kandidaten Indizes verfügen.  
  
 Fremdschlüssel *eExpression4*Tag *TagName4*[nodup]  
 Erstellt einen fremd Index (nonprimary) und richtet eine Beziehung zu einer übergeordneten Tabelle ein. *eExpression4* gibt den Fremdschlüssel Ausdruck des Indexes an, und *TagName4* gibt den Namen des zu erstellenden Fremdschlüssel Tags an. Indextagnamen können bis zu 10 Zeichen enthalten. Fügen Sie nodup ein, um einen Kandidaten fremden Index zu erstellen.  
  
 Sie können mehrere fremd Indizes für die Tabelle erstellen, aber die Foreign Index-Ausdrücke müssen andere Felder in der Tabelle angeben.  
  
 Verweise *TableName3*[Tag *TagName5*]  
 Gibt die übergeordnete Tabelle an, mit der eine persistente Beziehung hergestellt wird. Include Tag *TagName5* , um eine Beziehung auf Grundlage eines Indextags für die übergeordnete Tabelle einzurichten. Indextagnamen können bis zu 10 Zeichen enthalten. Wenn Sie *tagTagName5* weglassen, wird die Beziehung standardmäßig mit dem primär Index Schlüssel der übergeordneten Tabelle hergestellt.  
  
 Überprüfen *eExpression2*[Error *cMessageText2*]  
 Gibt die Tabellen Validierungs Regel an. Fehler *cMessageText2* gibt die Fehlermeldung an, die von Visual FoxPro beim Ausführen der Tabellen Validierungs Regel angezeigt wird. Die Meldung wird nur angezeigt, wenn Daten in einem durchsuchen-oder Bearbeitungsfenster geändert werden.  
  
 Aus Array *Arrayname*  
 Gibt den Namen eines vorhandenen Arrays an, dessen Inhalt der Name, der Typ, die Genauigkeit und die Skala für jedes Feld in der Tabelle ist. Der Inhalt des Arrays kann mit der Funktion " **aFields**()" definiert werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Die neue Tabelle wird im niedrigsten verfügbaren Arbeitsbereich geöffnet, und der Zugriff darauf ist über den Alias möglich. Die neue Tabelle wird exklusiv geöffnet, unabhängig von der aktuellen Einstellung von Set Exclusive.  
  
 Wenn eine Datenbank geöffnet ist und Sie die Free-Klausel nicht einschließen, wird die neue Tabelle der Datenbank hinzugefügt. Sie können keine neue Tabelle mit dem gleichen Namen wie eine Tabelle in der Datenbank erstellen.  
  
 Wenn eine Datenbank geöffnet ist, ist für CREATE TABLE-SQL eine ausschließliche Verwendung der Datenbank erforderlich. Wenn Sie eine Datenbank für die exklusive Verwendung öffnen möchten, schließen Sie exklusive in Open Database ein.  
  
 Wenn eine Datenbank nicht geöffnet ist, wenn Sie die neue Tabelle erstellen, einschließlich der Klauseln Name, Check, Default, Foreign Key, PRIMARY KEY oder References, wird ein Fehler generiert.  
  
> [!NOTE]  
>  CREATE TABLE Syntax verwendet Kommas, um bestimmte CREATE TABLE Optionen voneinander zu trennen. Außerdem müssen die NULL-, not NULL-, Check-, Default-, Primary Key-und Unique-Klauseln in den Klammern abgelegt werden, die die Spaltendefinitionen enthalten.  
  
## <a name="driver-remarks"></a>Hinweise zu Treibern  
 Wenn Ihre Anwendung die ODBC-SQL-Anweisung CREATE TABLE an die Datenquelle sendet, übersetzt der Visual FoxPro-ODBC-Treiber den Befehl mithilfe der in der folgenden Tabelle gezeigten Syntax in den Befehl "Visual foxprocreate Table".  
  
|ODBC-Syntax|Syntax von Visual FoxPro|  
|-----------------|--------------------------|  
|Create Table *Basistabellen Name*<br /><br /> (*Column-Identifier-Datentyp*<br /><br /> [nicht NULL]<br /><br /> [,*Column-Identifier-Datentyp*<br /><br /> [nicht NULL]...)|Create Table *TableName1* [Name *LongTableName*]<br /><br /> (*FieldName1* *FieldType*<br /><br /> [(*nfieldwidth* [, *nprecision*])]<br /><br /> [nicht NULL])|  
  
 Wenn Sie mithilfe des Treibers eine Tabelle erstellen, schließt der Treiber die Tabelle sofort nach der Erstellung, damit andere Benutzer den Zugriff auf die Tabelle zulassen. Dies unterscheidet sich von Visual FoxPro, wodurch die Tabelle bei der Erstellung exklusiv geöffnet bleibt. Wenn jedoch eine gespeicherte Prozedur in der Datenquelle, die eine CREATE TABLE-Anweisung enthält, ausgeführt wird, bleibt die Tabelle offen.  
  
 Wenn es sich bei der Datenquelle um eine Datenbank (DBC-Datei) handelt, erstellt der Visual FoxPro-ODBC-Treiber eine Tabelle mit dem Namen *LongTableName* mit demselben Namen wie der Name der *Basistabelle*.  
  
### <a name="using-data-definition-language-ddl"></a>Verwenden der Datendefinitionssprache (DDL)  
 Sie können DDL an den folgenden Stellen nicht einschließen:  
  
-   In einer Batch-SQL-Anweisung, die eine Transaktion erfordert  
  
-   Im manuellen Commitmodus, nach einer-Anweisung, die eine Transaktion erforderte, es sei denn, die Anwendung ruft **SQLTransact**zuerst auf.  
  
 Wenn Sie z. b. eine temporäre Tabelle erstellen möchten, sollten Sie die Tabelle erstellen, bevor Sie mit der Anweisung beginnen, die eine Transaktion erfordert. Wenn Sie die CREATE TABLE-Anweisung in eine Batch-SQL-Anweisung einschließen, die eine Transaktion erfordert, gibt der Treiber eine Fehlermeldung zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER TABLE-SQL-Befehl](../../odbc/microsoft/alter-table-sql-command.md)   
 [Unterstützte Datentypen (Visual FoxPro-ODBC-Treiber)](../../odbc/microsoft/supported-data-types-visual-foxpro-odbc-driver.md)   
 [INSERT-SQL-Befehl](../../odbc/microsoft/insert-sql-command.md)   
 [SELECT (SQL-Befehl)](../../odbc/microsoft/select-sql-command.md)
