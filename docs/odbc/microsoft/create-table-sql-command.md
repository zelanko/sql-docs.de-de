---
title: Erstellen der Tabelle – SQL-Befehl | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62d13bdc9d1a0fc030dc33bf982f6561b454c4ea
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53213499"
---
# <a name="create-table---sql-command"></a>CREATE TABLE (SQL-Befehl)
Erstellt eine Tabelle mit den angegebenen Feldern.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die systemeigene Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie **Treiber "Hinweise"**.  
  
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
 Erstellen der Tabelle &#124; DBF *TableName1*  
 Gibt den Namen der Tabelle zu erstellen. Die Tabelle und die DBF-Optionen sind identisch.  
  
 Namen *LongTableName*  
 Gibt einen langen Namen für die Tabelle an. Ein lange Tabellennamen kann angegeben werden, nur, wenn eine Datenbank geöffnet ist, da lange Tabellennamen in Datenbanken gespeichert werden.  
  
 Lange Namen können bis zu 128 Zeichen enthalten und können anstelle von kurzen Dateinamen in der Datenbank verwendet werden.  
  
 KOSTENLOS  
 Gibt an, dass die Tabelle wird eine geöffnete Datenbank nicht hinzugefügt werden. FREE ist nicht erforderlich, wenn eine Datenbank nicht geöffnet ist.  
  
 *(FieldName1 FieldType* [( *nFieldWidth* [, *nPrecision*])]  
 Die Feldnamen, Feldtyp, Feldbreite und Feld-Genauigkeit (Anzahl von Dezimalstellen an), gibt bzw.  
  
 *Feldtyp* ist ein einzelner Buchstabe verwendet, der angibt, in des Felds des [Datentyp](../../odbc/microsoft/visual-foxpro-field-data-types.md). Einige Felddatentypen erfordern die Angabe *nFieldWidth* oder *nPrecision* oder beides.  
  
 *nFieldWidth* und *nPrecision* D, G, ich, L, M, P, T und Y werden ignoriert Typen. *nPrecision* standardmäßig auf 0 (null) (ohne Dezimalstellen), wenn *nPrecision* ist nicht für die B, F oder N-Typen enthalten.  
  
 NULL  
 Ermöglicht null-Werte in das Feld an.  
  
 NOT NULL  
 Verhindert, dass null-Werte in das Feld.  
  
 Wenn Sie NULL weglassen und NOT NULL, bestimmt die aktuelle Einstellung von SET NULL an, ob null-Werte, in das Feld zulässig sind. Wenn Sie NULL lassen und nicht NULL und die PRIMARY KEY- oder UNIQUE-Klausel, die aktuelle Einstellung von SET NULL wird ignoriert, und im Feld standardmäßig nicht NULL.  
  
 Überprüfen Sie *lExpression1*  
 Gibt eine Überprüfungsregel für das Feld. *lExpression1* kann eine benutzerdefinierte Funktion sein. Wenn Sie ein leerer Datensatz angefügt wird, wird die Validierungsregel überprüft. Ein Fehler wird generiert, wenn die Überprüfungsregel für ein leeres Feld-Wert in eine angefügte Datensatz nicht zugelassen wird.  
  
 Fehler *cMessageText1*  
 Gibt die Fehlermeldung, die Visual FoxPro angezeigt, wenn die Feldregel Fehler generiert. Die Nachricht wird nur angezeigt, wenn Daten in einem Durchsuchen-Fenster oder eine Editor-Fenster geändert werden.  
  
 Standard *eExpression1*  
 Gibt einen Standardwert für das Feld an. Der Datentyp des *eExpression1* muss den Datentyp des Felds identisch sein.  
  
 PRIMARY KEY  
 Erstellt einen primären Index für das Feld an. Der Primärindex-Tag enthält den gleichen Namen wie das Feld an.  
  
 UNIQUE  
 Erstellt einen Index Kandidat für das Feld. Der Indexname Candidate hat den gleichen Namen wie das Feld an.  
  
> [!NOTE]  
>  Kandidat Indizes (erstellt durch Einschließen der EINDEUTIGEN Option in CREATE TABLE- oder ALTER TABLE - SQL) sind nicht identisch mit Indizes, die mit der EINDEUTIGEN Option in den INDEX-Befehl erstellt. Ein Index erstellt, mit der EINDEUTIGEN Option in den INDEX-Befehl können doppelte Indexschlüssel; Doppelte Indexschlüssel zulassen kandidatenindizes nicht. Finden Sie unter [INDEX](../../odbc/microsoft/index-command.md) für Weitere Informationen zu der Möglichkeit.  
  
 NULL-Werte und doppelter Datensätze dürfen nicht in einem Feld für einen primären oder Kandidatenschlüssel Index verwendet. Allerdings generiert Visual FoxPro keinen Fehler, wenn Sie einen primären oder Kandidatenschlüssel Index für ein Feld erstellen, die null-Werte unterstützt. Visual FoxPro, wird ein Fehler generiert, wenn Sie versuchen, einen Nullwerte oder doppelten Wert in ein Feld verwendet, die für einen primären oder Kandidatenschlüssel Index eingeben.  
  
 Verweise *TableName2*[TAG *TagName1*]  
 Gibt die übergeordnete Tabelle mit der eine persistente Beziehung hergestellt wird. Wenn Sie Tags weglassen *TagName1*, wird die Beziehung hergestellt, über die Schlüssel des primären Indexes der übergeordneten Tabelle. Wenn die übergeordneten Tabelle nicht über einen primären Index verfügt, generiert Visual FoxPro einen Fehler aus.  
  
 Include (TAG) *TagName1* zu, um eine Beziehung, die basierend auf einem vorhandenen Index enthalten, für die übergeordnete Tabelle herzustellen. Tag-Namen des Index können bis zu 10 Zeichen enthalten.  
  
 Die übergeordneten Tabelle darf nicht mit einer kostenlosen Tabelle sein.  
  
 NOCPTRANS  
 Verhindert die Übersetzung in eine andere Codepage für Zeichen und Memo Felder. Wenn die Tabelle in einer anderen Codepage konvertiert wird, werden die Felder für die NOCPTRANS angegeben wurde nicht übersetzt. NOCPTRANS können nur für Zeichen- und Memo Felder angegeben werden.  
  
 Das folgende Beispiel erstellt eine Tabelle namens Mytable, die zwei Zeichenfelder und zwei Memofelder enthält. Das zweite Zeichenfeld char2 und das zweite Feld der Gutschrift, memo2, enthalten NOCPTRANS, um zu verhindern, dass bei der Übersetzung an.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 PRIMÄRSCHLÜSSEL *eExpression2* TAG *TagName2*  
 Gibt an, einen primären Index zu erstellen. *eExpression2* gibt jede Feld oder eine Kombination der Felder in der Tabelle. TAG *TagName2* gibt den Namen für den primären Index-Tag, das erstellt wird. Tag-Namen des Index können bis zu 10 Zeichen enthalten.  
  
 Da eine Tabelle nur ein primären Index verfügen kann, können nicht Sie diese Klausel einschließen, wenn Sie bereits einen primären Index für ein Feld erstellt haben. Visual FoxPro generiert einen Fehler auf, wenn Sie mehr als eine PRIMARY KEY-Klausel im Artikel CREATE TABLE.  
  
 EINDEUTIGE *eExpression3*TAG *TagName3*  
 Erstellt einen Index Kandidat. *eExpression3* gibt jede Feld oder eine Kombination der Felder in der Tabelle. Wenn Sie einen primären Index mit einem der PRIMARY KEY-Optionen erstellt haben, können nicht Sie allerdings das Feld enthalten, das für den primären Index angegeben wurde. TAG *TagName3* gibt einen Tagnamen für die Candidate-Indexname, der erstellt wird. Tag-Namen des Index können bis zu 10 Zeichen enthalten.  
  
 Eine Tabelle kann mehrere Kandidaten Indizes aufweisen.  
  
 FREMDSCHLÜSSEL *eExpression4*TAG *TagName4*[NODUP]  
 Erstellt einen Fremdschlüssel (nicht primäre) Index, und stellt eine Beziehung zu einer übergeordneten Tabelle her. *eExpression4* gibt an, die foreign Key Indexausdruck, und *TagName4* gibt den Namen der foreign Key Indexname, der erstellt wird *.* Tag-Namen des Index können bis zu 10 Zeichen enthalten. Umfassen Sie NODUP, um einen Fremdschlüssel Kandidaten-Index erstellen.  
  
 Sie können mehrere Fremdschlüssel Indizes für die Tabelle erstellen, aber die Fremdschlüssel Indexausdrücke müssen verschiedene Felder in der Tabelle angeben.  
  
 Verweise *TableName3*[TAG *TagName5*]  
 Gibt die übergeordnete Tabelle mit der eine persistente Beziehung hergestellt wird. Include (TAG) *TagName5* zu, um eine Beziehung, die basierend auf einem Index enthalten, für die übergeordnete Tabelle herzustellen. Tag-Namen des Index können bis zu 10 Zeichen enthalten. Standardmäßig, wenn Sie, TAG weglassen *TagName5,* die Beziehung mit der übergeordneten Tabelle Primärindex Schlüssel eingerichtet.  
  
 Überprüfen Sie *eExpression2*[Fehler *cMessageText2*]  
 Gibt die Validierungsregel für die Tabelle an. Fehler *cMessageText2* gibt die Fehlermeldung an, die Visual FoxPro angezeigt wird, wenn die Validierungsregel für die Tabelle ausgeführt wird. Die Nachricht wird nur angezeigt, wenn Daten in einem Durchsuchen-Fenster geändert werden oder Fenster "Bearbeiten".  
  
 AUS ARRAY *ArrayName*  
 Gibt den Namen eines vorhandenen Arrays, dessen Inhalt den Namen, Datentyp, Genauigkeit und Dezimalstellen, für jedes Feld in der Tabelle ist. Der Inhalt des Arrays können definiert werden, mit der **AFIELDS**()-Funktion.  
  
## <a name="remarks"></a>Hinweise  
 Die neue Tabelle in der niedrigsten verfügbaren Arbeitsbereich geöffnet, und über den Alias zugegriffen werden kann. Die neue Tabelle wird unabhängig von der aktuellen Einstellung des EXKLUSIVEN festgelegt ausschließlich geöffnet.  
  
 Wenn eine Datenbank geöffnet ist, und Sie die kostenlose-Klausel nicht einschließen, wird die neue Tabelle in der Datenbank hinzugefügt. Sie können nicht mit dem gleichen Namen wie eine Tabelle in der Datenbank eine neue Tabelle erstellen.  
  
 Wenn eine Datenbank geöffnet ist, erfordert die CREATE TABLE - SQL exklusive Verwendung der Datenbank. Schließen Sie zum Öffnen einer Datenbank für die ausschließliche Verwendung exklusiver, in Datenbank öffnen.  
  
 Wenn eine Datenbank geöffnet ist, wenn Sie die neue Tabelle erstellen, generiert das einschließlich der Namen, CHECK, DEFAULT, FOREIGN KEY, PRIMARY KEY- oder Verweise Klauseln einen Fehler aus.  
  
> [!NOTE]  
>  CREATE TABLE-Syntax verwendet Kommas zum Trennen von bestimmte Optionen für die CREATE TABLE. Darüber hinaus müssen die NULL, nicht NULL, überprüfen, Default-, PRIMARY KEY- und UNIQUE-Klausel innerhalb der Klammern, enthält die Definitionen der platziert werden.  
  
## <a name="driver-remarks"></a>Treiber "Hinweise".  
 Wenn Ihre Anwendung die ODBC-SQL-Anweisung sendet übersetzt CREATE TABLE mit der Datenquelle, die der Visual FoxPro-ODBC-Treiber den Befehl in der Visual FoxProCREATE TABLE-Befehl mit der Syntax in der folgenden Tabelle gezeigt.  
  
|ODBC-syntax|Visual FoxPro-syntax|  
|-----------------|--------------------------|  
|CREATE TABLE *Basis-Table-Name*<br /><br /> (*Spaltenbezeichner Datentyp*<br /><br /> [NICHT-NULL]<br /><br /> [,*Spaltenbezeichner Datentyp*<br /><br /> [NOT NULL]...)|Erstellen der Tabelle *TableName1* [NAME *LongTableName*]<br /><br /> (*FieldName1* *Feldtyp*<br /><br /> [(*nFieldWidth* [, *nPrecision*])]<br /><br /> [NICHT NULL])|  
  
 Wenn Sie eine Tabelle mit dem Treiber erstellen, schließt der Treiber in der Tabelle direkt nach dem Erstellen der Tabelle von anderen Benutzern erlauben. Dies unterscheidet sich von Visual FoxPro, die in der Tabelle ausschließlich bei der Erstellung offen. Allerdings liegt an der Datenquelle, die mit einer CREATE TABLE-Anweisung eine gespeicherte Prozedur ausgeführt wird, in der Tabelle geöffnet bleibt.  
  
 Wenn die Datenquelle einer Datenbank (DBC-Datei) ist, wird der Visual FoxPro-ODBC-Treiber erstellt eine Tabelle namens *LongTableName* mit dem gleichen Namen wie die *Basis-Tabellenname*.  
  
### <a name="using-data-definition-language-ddl"></a>Mithilfe der Datendefinitionssprache (DDL)  
 DDL können nicht in den folgenden Orten einbezogen werden:  
  
-   In einem Batch-SQL-Anweisung erfordert, dass eine Transaktion  
  
-   Im Manualcommit-Modus nach einer Anweisung, die eine Transaktion erforderlich, es sei denn, Ihre Anwendung zuerst ruft **SQLTransact**.  
  
 Z. B. Wenn Sie eine temporäre Tabelle erstellen möchten, sollten Sie in der Tabelle erstellen, vor dem Beginn der Anweisung, die eine Transaktion erfordern. Wenn Sie die CREATE TABLE-Anweisung in einem Batch-SQL-Anweisung, die eine Transaktion erforderlich ist einschließen, gibt der Treiber eine Fehlermeldung zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER TABLE - SQL-Befehl](../../odbc/microsoft/alter-table-sql-command.md)   
 [Unterstützte Datentypen (Visual FoxPro-ODBC-Treiber)](../../odbc/microsoft/supported-data-types-visual-foxpro-odbc-driver.md)   
 [INSERT - SQL-Befehl](../../odbc/microsoft/insert-sql-command.md)   
 [SELECT (SQL-Befehl)](../../odbc/microsoft/select-sql-command.md)
