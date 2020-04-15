---
title: CREATE TABLE - SQL-Befehl | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298690"
---
# <a name="create-table---sql-command"></a>CREATE TABLE (SQL-Befehl)
Erstellt eine Tabelle mit den angegebenen Feldern.  
  
 Der Visual FoxPro ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie unter **Treiberhinweise**.  
  
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
 CREATE TABLE &#124; *DBF-Tabellenname1*  
 Gibt den Namen der zu erstellenden Tabelle an. Die Optionen TABLE und DBF sind identisch.  
  
 NAME *LongTableName*  
 Gibt einen langen Namen für die Tabelle an. Ein langer Tabellenname kann nur angegeben werden, wenn eine Datenbank geöffnet ist, da lange Tabellennamen in Datenbanken gespeichert werden.  
  
 Lange Namen können bis zu 128 Zeichen enthalten und können anstelle kurzer Dateinamen in der Datenbank verwendet werden.  
  
 FREE  
 Gibt an, dass die Tabelle nicht zu einer geöffneten Datenbank hinzugefügt wird. KOSTENLOS ist nicht erforderlich, wenn eine Datenbank nicht geöffnet ist.  
  
 *(FieldName1 FieldType* [( *nFieldWidth* [, *nPrecision*])]  
 Gibt den Feldnamen, den Feldtyp, die Feldbreite und die Feldgenauigkeit (Anzahl der Dezimalstellen) an.  
  
 *FieldType* ist ein einzelner Buchstabe, der den [Datentyp](../../odbc/microsoft/visual-foxpro-field-data-types.md)des Felds angibt. Einige Felddatentypen erfordern, dass Sie *nFieldWidth* oder *nPrecision* oder beides angeben.  
  
 *nFieldWidth* und *nPrecision* werden für die Typen D, G, I, L, M, P, T und Y ignoriert. *nPrecision* ist standardmäßig Null (keine Dezimalstellen), wenn *nPrecision* für die Typen B, F oder N nicht enthalten ist.  
  
 NULL  
 Erlaubt NULL-Werte im Feld.  
  
 NOT NULL  
 Verhindert NULL-Werte im Feld.  
  
 Wenn Sie NULL und NOT NULL weglassen, bestimmt die aktuelle Einstellung von SET NULL, ob NULL-Werte im Feld zulässig sind. Wenn Sie jedoch NULL und NOT NULL weglassen und die PRIMARY KEY- oder UNIQUE-Klausel einschließen, wird die aktuelle Einstellung von SET NULL ignoriert, und das Feld wird standardmäßig auf NOT NULL festgelegt.  
  
 CHECK *lExpression1*  
 Gibt eine Validierungsregel für das Feld an. *lExpression1* kann eine benutzerdefinierte Funktion sein. Wenn ein leerer Datensatz angehängt wird, wird die Validierungsregel überprüft. Ein Fehler wird generiert, wenn die Validierungsregel keinen leeren Feldwert in einem angehängten Datensatz zulässt.  
  
 ERROR *cMessageText1*  
 Gibt die Fehlermeldung an, die Visual FoxPro anzeigt, wenn die Feldregel einen Fehler generiert. Die Meldung wird nur angezeigt, wenn Daten in einem Browse-Fenster oder einem Bearbeitungsfenster geändert werden.  
  
 DEFAULT *eExpression1*  
 Gibt einen Standardwert für das Feld an. Der Datentyp von *eExpression1* muss mit dem Datentyp des Felds übereinstimmen.  
  
 PRIMARY KEY  
 Erstellt einen primären Index für das Feld. Das primäre Index-Tag hat denselben Namen wie das Feld.  
  
 UNIQUE  
 Erstellt einen Kandidatenindex für das Feld. Das Kandidatenindex-Tag hat denselben Namen wie das Feld.  
  
> [!NOTE]  
>  Kandidatenindizes (erstellt durch Einschließen der UNIQUE-Option in CREATE TABLE oder ALTER TABLE - SQL) sind nicht identisch mit Indizes, die mit der Option UNIQUE im Befehl INDEX erstellt wurden. Ein Index, der mit der Unique-Option im Index-Befehl erstellt wurde, ermöglicht doppelte Indexschlüssel. Kandidatenindizes lassen keine doppelten Indexschlüssel zu. Weitere Informationen zu der UNIQUE-Option finden Sie unter [INDEX.](../../odbc/microsoft/index-command.md)  
  
 Nullwerte und doppelte Datensätze sind in einem Feld, das für einen Primär- oder Kandidatenindex verwendet wird, nicht zulässig. Visual FoxPro generiert jedoch keinen Fehler, wenn Sie einen Primär- oder Kandidatenindex für ein Feld erstellen, das NULL-Werte unterstützt. Visual FoxPro generiert einen Fehler, wenn Sie versuchen, einen Null- oder doppelten Wert in ein Feld einzugeben, das für einen Primär- oder Kandidatenindex verwendet wird.  
  
 VERWEISE *TableName2*[TAG *TagName1*]  
 Gibt die übergeordnete Tabelle an, zu der eine persistente Beziehung eingerichtet wird. Wenn Sie TAG *TagName1*weglassen, wird die Beziehung mithilfe des primären Indexschlüssels der übergeordneten Tabelle eingerichtet. Wenn die übergeordnete Tabelle keinen primären Index hat, generiert Visual FoxPro einen Fehler.  
  
 Schließen Sie TAG *TagName1* ein, um eine Beziehung basierend auf einem vorhandenen Index-Tag für die übergeordnete Tabelle einzurichten. Index-Tag-Namen können bis zu 10 Zeichen enthalten.  
  
 Die übergeordnete Tabelle kann keine freie Tabelle sein.  
  
 NOCPTRANS  
 Verhindert die Übersetzung in eine andere Codepage für Zeichen- und Memofelder. Wenn die Tabelle in eine andere Codepage konvertiert wird, werden die Felder, für die NOCPTRANS angegeben wurde, nicht übersetzt. NOCPTRANS kann nur für Zeichen- und Memofelder angegeben werden.  
  
 Im folgenden Beispiel wird eine Tabelle mit dem Namen mytable erstellt, die zwei Zeichenfelder und zwei Memofelder enthält. Das zweite Zeichenfeld, char2, und das zweite Memofeld, memo2, enthalten NOCPTRANS, um eine Übersetzung zu verhindern.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 PRIMARY KEY *eExpression2* TAG *TagName2*  
 Gibt einen primären Index an, der erstellt werden soll. *eExpression2* gibt ein beliebiges Feld oder eine Kombination von Feldern in der Tabelle an. TAG *TagName2* gibt den Namen für das erstellte primäre Index-Tag an. Index-Tag-Namen können bis zu 10 Zeichen enthalten.  
  
 Da eine Tabelle nur einen primären Index haben kann, können Sie diese Klausel nicht einschließen, wenn Sie bereits einen primären Index für ein Feld erstellt haben. Visual FoxPro generiert einen Fehler, wenn Sie mehr als eine PRIMARY KEY-Klausel in CREATE TABLE aufnehmen.  
  
 UNIQUE *eExpression3*TAG *TagName3*  
 Erstellt einen Kandidatenindex. *eExpression3* gibt ein beliebiges Feld oder eine Kombination von Feldern in der Tabelle an. Wenn Sie jedoch einen primären Index mit einer der PRIMARY KEY-Optionen erstellt haben, können Sie das Feld, das für den primären Index angegeben wurde, nicht einschließen. TAG *TagName3* gibt einen Tagnamen für das erstellte Kandidatenindex-Tag an. Index-Tag-Namen können bis zu 10 Zeichen enthalten.  
  
 Eine Tabelle kann mehrere Kandidatenindizes haben.  
  
 FOREIGN KEY *eExpression4*TAG *TagName4*[NODUP]  
 Erstellt einen fremden (nicht primären) Index und stellt eine Beziehung zu einer übergeordneten Tabelle her. *eExpression4* gibt den Fremdindexschlüsselausdruck an, und *TagName4* gibt den Namen des erstellten Fremdindexschlüssel-Tags an. Index-Tag-Namen können bis zu 10 Zeichen enthalten. Schließen Sie NODUP ein, um einen Kandidaten-Auslandsindex zu erstellen.  
  
 Sie können mehrere Fremdindizes für die Tabelle erstellen, aber die Fremdindexausdrücke müssen unterschiedliche Felder in der Tabelle angeben.  
  
 Verweise *TableName3*[TAG *TagName5*]  
 Gibt die übergeordnete Tabelle an, zu der eine persistente Beziehung eingerichtet wird. Schließen Sie TAG *TagName5* ein, um eine Beziehung basierend auf einem Index-Tag für die übergeordnete Tabelle einzurichten. Index-Tag-Namen können bis zu 10 Zeichen enthalten. Wenn Sie TAG *TagName5 weglassen,* wird die Beziehung standardmäßig mit dem primären Indexschlüssel der übergeordneten Tabelle hergestellt.  
  
 CHECK *eExpression2*[ERROR *cMessageText2*]  
 Gibt die Tabellenvalidierungsregel an. ERROR *cMessageText2* gibt die Fehlermeldung an, die Visual FoxPro anzeigt, wenn die Tabellenvalidierungsregel ausgeführt wird. Die Meldung wird nur angezeigt, wenn Daten in einem Such- oder Bearbeitungsfenster geändert werden.  
  
 VON ARRAY *ArrayName*  
 Gibt den Namen eines vorhandenen Arrays an, dessen Inhalt der Name, der Typ, die Genauigkeit und der Maßstab für jedes Feld in der Tabelle sind. Der Inhalt des Arrays kann mit der Funktion **AFIELDS**( ) definiert werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Die neue Tabelle wird im untersten verfügbaren Arbeitsbereich geöffnet und kann über ihren Alias aufgerufen werden. Die neue Tabelle wird exklusiv geöffnet, unabhängig von der aktuellen Einstellung von SET EXCLUSIVE.  
  
 Wenn eine Datenbank geöffnet ist und Sie die FREE-Klausel nicht enthalten, wird die neue Tabelle der Datenbank hinzugefügt. Sie können keine neue Tabelle mit demselben Namen wie eine Tabelle in der Datenbank erstellen.  
  
 Wenn eine Datenbank geöffnet ist, erfordert CREATE TABLE - SQL die ausschließliche Verwendung der Datenbank. Um eine Datenbank exklusiv zu öffnen, schließen Sie EXKLUSIV in OPEN DATABASE ein.  
  
 Wenn eine Datenbank beim Erstellen der neuen Tabelle nicht geöffnet ist, wird ein Fehler generiert, einschließlich der Klauseln NAME, CHECK, DEFAULT, FOREIGN KEY, PRIMARY KEY oder REFERENCES.  
  
> [!NOTE]  
>  Die CREATE TABLE-Syntax verwendet Kommas, um bestimmte CREATE TABLE-Optionen zu trennen. Außerdem müssen die Klauseln NULL, NOT NULL, CHECK, DEFAULT, PRIMARY KEY und UNIQUE in den Klammern platziert werden, die die Spaltendefinitionen enthalten.  
  
## <a name="driver-remarks"></a>Driver-Bemerkungen  
 Wenn Ihre Anwendung die ODBC SQL-Anweisung CREATE TABLE an die Datenquelle sendet, übersetzt der Visual FoxPro ODBC-Treiber den Befehl mithilfe der in der folgenden Tabelle gezeigten Syntax in den Befehl Visual FoxProCREATE TABLE.  
  
|ODBC-Syntax|Visuelle FoxPro-Syntax|  
|-----------------|--------------------------|  
|CREATE TABLE *Basistabellenname*<br /><br /> (*Spaltenbezeichnerdatentyp*<br /><br /> [NICHT NULL]<br /><br /> [,*Spaltenbezeichnerdatentyp*<br /><br /> [NICHT NULL] ...)|CREATE *TABELLEName1* [NAME *LongTableName*]<br /><br /> (*FieldName1* *FieldType*<br /><br /> [(*nFieldWidth* [, *nPrecision*])]<br /><br /> [NICHT NULL])|  
  
 Wenn Sie eine Tabelle mit dem Treiber erstellen, schließt der Treiber die Tabelle unmittelbar nach der Erstellung, um anderen Benutzern den Zugriff auf die Tabelle zu ermöglichen. Dies unterscheidet sich von Visual FoxPro, das die Tabelle ausschließlich bei der Erstellung offen lässt. Wenn jedoch eine gespeicherte Prozedur in der Datenquelle ausgeführt wird, die eine CREATE TABLE-Anweisung enthält, bleibt die Tabelle geöffnet.  
  
 Wenn es sich bei der Datenquelle um eine Datenbank (.dbc-Datei) handelt, erstellt der Visual FoxPro ODBC-Treiber eine Tabelle mit dem Namen *LongTableName* mit demselben Namen wie der *Basistabellenname*.  
  
### <a name="using-data-definition-language-ddl"></a>Verwenden der Datendefinitionssprache (DDL)  
 DDL kann nicht an den folgenden Stellen eingeschlossen werden:  
  
-   In einer Batch-SQL-Anweisung, die eine Transaktion erfordert  
  
-   Im manuellen Commit-Modus nach einer Anweisung, die eine Transaktion erforderte, es sei denn, Ihre Anwendung ruft **SQLTransact**zuerst auf.  
  
 Wenn Sie z. B. eine temporäre Tabelle erstellen möchten, sollten Sie die Tabelle erstellen, bevor Sie mit der Anweisung beginnen, die eine Transaktion erfordert. Wenn Sie die CREATE TABLE-Anweisung in eine SQL-Batch-Anweisung aufnehmen, die eine Transaktion erfordert, gibt der Treiber eine Fehlermeldung zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER TABLE - SQL-Befehl](../../odbc/microsoft/alter-table-sql-command.md)   
 [Unterstützte Datentypen (Visual FoxPro ODBC-Treiber)](../../odbc/microsoft/supported-data-types-visual-foxpro-odbc-driver.md)   
 [INSERT - SQL-Befehl](../../odbc/microsoft/insert-sql-command.md)   
 [SELECT (SQL-Befehl)](../../odbc/microsoft/select-sql-command.md)
