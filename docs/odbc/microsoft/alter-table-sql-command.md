---
title: ALTER TABLE - SQL-Befehl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- alter table [ODBC]
ms.assetid: 3a01a291-f4d9-43bc-a725-5a95546ff364
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f656396455a8d5669debc158c3edc866491fcb5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63457623"
---
# <a name="alter-table---sql-command"></a>ALTER TABLE (SQL-Befehl)
Programmgesteuertes Ändern der Struktur einer Tabelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ALTER TABLE TableName1  
   ADD | ALTER [COLUMN] FieldName1  
      FieldType [(nFieldWidth [, nPrecision])]  
      [NULL | NOT NULL]  
      [CHECK lExpression1 [ERROR cMessageText1]]  
      [DEFAULT eExpression1]  
      [PRIMARY KEY | UNIQUE]  
      [REFERENCES TableName2 [TAG TagName1]]  
      [NOCPTRANS]  
 - Or -  
ALTER TABLE TableName1  
   ALTER [COLUMN] FieldName2  
      [NULL | NOT NULL]  
      [SET DEFAULT eExpression2]  
      [SET CHECK lExpression2 [ERROR cMessageText2]]  
      [DROP DEFAULT]  
      [DROP CHECK]  
 - Or -  
ALTER TABLE TableName1  
   [DROP [COLUMN] FieldName3]  
   [SET CHECK lExpression3 [ERROR cMessageText3]]  
   [DROP CHECK]  
   [ADD PRIMARY KEY eExpression3 TAG TagName2]  
   [DROP PRIMARY KEY]  
   [ADD UNIQUE eExpression4 [TAG TagName3]]  
   [DROP UNIQUE TAG TagName4]  
   [ADD FOREIGN KEY [eExpression5] TAG TagName4  
      REFERENCES TableName2 [TAG TagName5]]  
   [DROP FOREIGN KEY TAG TagName6 [SAVE]]  
   [RENAME COLUMN FieldName4 TO FieldName5]  
   [NOVALIDATE]  
```  
  
## <a name="arguments"></a>Argumente  
 *TableName1*  
 Gibt den Namen der Tabelle, dessen Struktur geändert wird.  
  
 ADD [Spalte] *FieldName1*  
 Gibt den Namen des hinzuzufügenden Felds.  
  
 ALTER [Spalte] *FieldName1*  
 Gibt den Namen eines vorhandenen Felds ändern.  
  
 *FieldType* [( *nFieldWidth* [, *nPrecision*]])  
 Gibt den Feldtyp, Feldbreite und Feld-Genauigkeit (Anzahl der Dezimalstellen) für eine neue oder geänderte Feld an.  
  
 *Feldtyp* ist ein einzelner Buchstabe verwendet, der des Felds des angibt [Datentyp](../../odbc/microsoft/visual-foxpro-field-data-types.md). Einige Felddatentypen erfordern die Angabe *nFieldWidth* oder *nPrecision* oder beides.  
  
 *nFieldWidth* und *nPrecision* D, G, ich, L, M, P, T und Y werden ignoriert Typen. In der Standardeinstellung *nPrecision* ist 0 (null) (ohne Dezimalstellen) an, wenn *nPrecision* ist nicht für die B, F oder N-Typen enthalten.  
  
 NULL &#124; NOT NULL  
 Ermöglicht oder verhindert, dass null-Werte in das Feld.  
  
 Wenn Sie NULL weglassen und NOT NULL, bestimmt die aktuelle Einstellung von SET NULL an, ob null-Werte, in das Feld zulässig sind. Wenn Sie NULL lassen und nicht NULL und die PRIMARY KEY- oder UNIQUE-Klausel enthalten, jedoch die aktuelle Einstellung von SET NULL ignoriert, und das Feld ist nicht standardmäßig NULL.  
  
 Überprüfen Sie *lExpression1*  
 Gibt eine Überprüfungsregel für das Feld. *lExpression1* muss zu einem logischen Ausdruck ausgewertet und kann eine benutzerdefinierte Funktion oder eine gespeicherte Prozedur. Wenn Sie ein leerer Datensatz angefügt wird, wird die Validierungsregel überprüft. Ein Fehler wird generiert, wenn die Überprüfungsregel für ein leeres Feld-Wert in eine angefügte Datensatz nicht zulässt.  
  
 ERROR *cMessageText1*  
 Gibt an, die Fehlermeldung angezeigt, wenn die Validierungsregel Feld einen Fehler generiert.  
  
 Standard *eExpression1*  
 Gibt einen Standardwert für das Feld an. Der Datentyp des *eExpression1* muss den Datentyp für das Feld identisch sein.  
  
 PRIMARY KEY  
 Erstellt ein primärer Index-Tag. Der Indexname hat den gleichen Namen wie das Feld.  
  
 UNIQUE  
 Erstellt ein Kandidat Index-Tag mit dem gleichen Namen wie das Feld an.  
  
> [!NOTE]  
>  Kandidat Indizes (einschließlich der Möglichkeit, angegeben für ANSI-Kompatibilität in ALTER TABLE oder CREATE TABLE erstellt) unterscheiden sich von Indizes, die mit der Möglichkeit im INDEX-Befehl erstellt. Ein Index erstellt werden, mithilfe von UNIQUE in den INDEX-Befehl können doppelte Indexschlüssel; Doppelte Indexschlüssel zulassen kandidatenindizes nicht.  
  
 NULL-Werte und Duplikate sind nicht in einem Feld zulässig, die für einen primären oder Kandidatenschlüssel Index verwendet wird.  
  
 Wenn Sie mithilfe der Spalte hinzufügen ein neues Feld erstellen, generiert Visual FoxPro keinen Fehler, wenn Sie einen primären oder Kandidatenschlüssel Index für ein Feld erstellen, die null-Werte unterstützt. Visual FoxPro wird jedoch ein Fehler generiert, wenn Sie versuchen, einen Nullwerte oder doppelten Wert in ein Feld eingeben, die für einen primären oder Kandidatenschlüssel Index verwendet wird.  
  
 Wenn Sie ein vorhandenes Feld, und der Primärschlüssel ändern oder Indexausdruck Candidate besteht aus Feldern in der Tabelle, überprüft Visual FoxPro, die Felder aus, um festzustellen, ob sie null-Werte oder doppelte Datensätze enthalten. Ist dies der Fall ist, Visual FoxPro-generiert einen Fehler, und die Tabelle nicht geändert wird.  
  
 Verweise *TableName2* TAG *TagName1*  
 Gibt die übergeordnete Tabelle mit der eine persistente Beziehung hergestellt wird. TAG *TagName1* gibt an, der übergeordneten Tabelle Indexname, die auf der die Beziehung basiert. Tag-Namen des Index können bis zu 10 Zeichen enthalten.  
  
 NOCPTRANS  
 Verhindert die Übersetzung in eine andere Codepage für Zeichen und Memo Felder. Wenn die Tabelle in einer anderen Codepage konvertiert wird, werden die Felder für die NOCPTRANS angegeben wurde nicht übersetzt. NOCPTRANS können nur für Zeichen- und Memo Felder angegeben werden.  
  
 Das folgende Beispiel erstellt eine Tabelle namens Mytable, die zwei Zeichenfelder und zwei Memofelder enthält. Das zweite Zeichenfeld char2 und das zweite Feld der Gutschrift, memo2, enthalten NOCPTRANS, um zu verhindern, dass bei der Übersetzung an.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 ALTER [Spalte] *FieldName2*  
 Gibt den Namen eines vorhandenen Felds ändern.  
  
 Standard festlegen *eExpression2*  
 Gibt einen neuen Standardwert für ein vorhandenes Feld an. Der Datentyp des *eExpression2* muss den Datentyp für das Feld identisch sein.  
  
 SET-CHECK *lExpression2*  
 Gibt eine neue Überprüfungsregel für ein vorhandenes Feld. *lExpression2* muss zu einem logischen Ausdruck ausgewertet und eine benutzerdefinierte Funktion oder eine gespeicherte Prozedur sein.  
  
 ERROR *cMessageText2*  
 Gibt an, die Fehlermeldung angezeigt, wenn die Validierungsregel Feld einen Fehler generiert. Die Nachricht wird nur angezeigt, wenn Daten in einem Fenster "Durchsuchen" oder "Bearbeiten" geändert werden.  
  
 DROP DEFAULT  
 Der Standardwert für ein vorhandenes Feld wird entfernt.  
  
 LÖSCHEN SIE DIE KONTROLLKÄSTCHEN  
 Entfernt die Überprüfungsregel für ein vorhandenes Feld.  
  
 DROP [Spalte] *FieldName3*  
 Gibt ein Feld aus der Tabelle zu entfernen. Entfernen ein Feld aus der Tabelle entfernt Festlegen von Standardwerten des Felds "und" Validierungsregel Feld.  
  
 Wenn Schlüssel oder einem Trigger Indexausdrücke auf das Feld verweisen, werden die Ausdrücke ungültig, wenn das Feld entfernt wird. In diesem Fall wird ein Fehler mit nicht generiert werden, wenn das Feld entfernt, aber die ungültige Index-Schlüssel oder einem Trigger-Ausdrücke werden Fehler zur Laufzeit generiert wird.  
  
 SET-CHECK *lExpression3*  
 Gibt die Validierungsregel für die Tabelle an. *lExpression3* muss zu einem logischen Ausdruck ausgewertet und eine benutzerdefinierte Funktion oder eine gespeicherte Prozedur sein.  
  
 ERROR *cMessageText3*  
 Gibt an, die Fehlermeldung angezeigt, wenn die Validierungsregel für die Tabelle einen Fehler generiert. Die Nachricht wird nur angezeigt, wenn Daten in einem Fenster "Durchsuchen" oder "Bearbeiten" geändert werden.  
  
 LÖSCHEN SIE DIE KONTROLLKÄSTCHEN  
 Entfernt die Validierungsregel für der Tabelle.  
  
 Hinzufügen von PRIMÄRSCHLÜSSEL *eExpression3*TAG *TagName2*  
 Einen primären Index hinzugefügt der Tabelle. *eExpression3* gibt an, der primäre Index-Schlüsselausdruck und *TagName2* gibt den Namen des primären Indexes-Tags. Tag-Namen des Index können bis zu 10 Zeichen enthalten. Wenn TAG *TagName2* ausgelassen wird und *eExpression3* ist ein einzelnes Feld, das Tag primärer Index hat den gleichen Namen wie das im angegebenen Feld *eExpression3*.  
  
 LÖSCHEN VON PRIMÄRSCHLÜSSEL  
 Entfernt den primären Index und der Indexname. Da eine Tabelle nur einen Primärschlüssel verfügen kann, ist es nicht erforderlich, um den Namen des primären Schlüssels anzugeben. Entfernen des primären Indexes löscht auch alle permanenten Beziehungen basierend auf dem primären Schlüssel.  
  
 ADD UNIQUE *eExpression4*[TAG *TagName3*]  
 Einen Kandidat Index hinzugefügt der Tabelle. *eExpression4* gibt an, die möglichen Schlüssel Indexausdruck, und *TagName3* gibt den Namen des Kandidaten Index Tags. Tag-Namen des Index können bis zu 10 Zeichen enthalten. Wenn Sie Tags weglassen *TagName3* und, wenn *eExpression4* ist ein einzelnes Feld, das Tag des möglichen Index hat den gleichen Namen wie das im angegebenen Feld *eExpression4*.  
  
 DROP EINDEUTIGES TAG *TagName4*  
 Entfernt die Candidate-Index und der Indexname. Da eine Tabelle mehrere Kandidatenschlüssel enthalten kann, müssen Sie den Namen des Tags die Candidate-Index angeben.  
  
 FREMDSCHLÜSSEL für hinzufügen [ *eExpression5*]-Tag *TagName4*  
 Einen Fremdschlüssel (nicht primäre) Index hinzugefügt der Tabelle. *eExpression5* gibt an, die foreign Key Indexausdruck, und *TagName4* gibt den Namen des Tags foreign Index. Tag-Namen des Index können bis zu 10 Zeichen enthalten.  
  
 Verweise *TableName2*[TAG *TagName5*]  
 Gibt die übergeordnete Tabelle mit der eine persistente Beziehung hergestellt wird. Include (TAG) *TagName5* zu, um eine Beziehung, die basierend auf einem vorhandenen Index enthalten, für die übergeordnete Tabelle herzustellen. Tag-Namen des Index können bis zu 10 Zeichen enthalten. Wenn Sie Tags weglassen *TagName5*, die Beziehung mit der übergeordneten Tabelle Primärindex Tag eingerichtet.  
  
 DROP FOREIGN KEY-TAG *TagName6*[speichern]  
 Löscht einen foreign Key, dessen Index-Tag ist *TagName6*. Wenn Sie auf "Speichern" weglassen, wird das Tag Index aus der strukturellen Index gelöscht. Gehören Sie speichern, um das Löschen des Index aus der strukturellen Index Tags zu verhindern.  
  
 Benennen Sie Spalte *FieldName4*für *FieldName5*  
 Können Sie den Namen eines Felds in der Tabelle zu ändern. *FieldName4* gibt den Namen des Felds, das umbenannt wird. *FieldName5* gibt den neuen Namen des Felds.  
  
> [!CAUTION]  
>  Walten Sie Sorgfalt, wenn die Felder der Tabelle umbenannt werden, da die ursprünglichen Feldnamen auf Indizieren von Ausdrücken, Feld- und Validierungsregeln, Befehle und Funktionen verweisen können.  
  
 NOVALIDATE  
 Gibt an, dass es sich bei Visual FoxPro, Änderungen an der Struktur der Tabelle vorgenommen werden können; diese Änderungen können die Integrität der Daten in der Tabelle verletzt. In der Standardeinstellung verhindert, dass Visual FoxPro ALTER TABLE vornehmen von Änderungen, die die Integrität der Daten in der Tabelle zu verletzen. Umfassen Sie NOVALIDATE, um dieses Standardverhalten zu überschreiben.  
  
## <a name="remarks"></a>Hinweise  
 ALTER TABLE kann verwendet werden, um die Struktur einer Tabelle ändern, die nicht in einer Datenbank hinzugefügt wurde. Visual FoxPro generiert jedoch einen Fehler aus, wenn Sie die STANDARDEINSTELLUNG, FOREIGN KEY, PRIMARY KEY-, Verweise enthalten oder Klauseln festgelegt, wenn Sie eine kostenlose Tabelle ändern.  
  
 ALTER TABLE kann in der Tabelle neu erstellen, indem das Erstellen einer neuen Tabellenüberschrift und Anfügen von Datensätzen an der Tabellenkopf. Beispielsweise kann die ändern, Typ oder die Breite eines Felds in der Tabelle neu erstellt werden führen.  
  
 Nachdem eine Tabelle neu erstellt wird, werden die Überprüfungsregeln für alle Felder ausgeführt, deren Typ oder Breite geändert wird. Wenn Sie den Typ oder die Breite eines Felds in der Tabelle ändern, wird die Regel für die Tabelle ausgeführt.  
  
 Wenn Sie Feld oder eine Tabelle Validierungsregeln für eine Tabelle, die Einträge besitzt ändern, wird von Visual FoxPro testet die neuen Feld oder eine Tabelle Validierungsregeln für die vorhandenen Daten und gibt eine Warnung auf dem ersten Vorkommen einer Validierungsregel Feld oder eine Tabelle oder eines Verstoßes Trigger.  
  
 Wenn die Tabelle, die Sie ändern in einer Datenbank, die ALTER TABLE - erfordert SQL die exklusive Verwendung der Datenbank. Schließen Sie zum Öffnen einer Datenbank für die ausschließliche Verwendung exklusiver, in Datenbank öffnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen Sie Tabelle - SQL-Befehl.](../../odbc/microsoft/create-table-sql-command.md)   
 [Befehl INDEX](../../odbc/microsoft/index-command.md)
