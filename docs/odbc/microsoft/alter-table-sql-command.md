---
title: ALTER TABLE - SQL-Befehl | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 587d721522503f9b392bb8be7433850fd7449efb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304711"
---
# <a name="alter-table---sql-command"></a>ALTER TABLE (SQL-Befehl)
Programmgesteuert wird die Struktur einer Tabelle geändert.  
  
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
 Gibt den Namen der Tabelle an, deren Struktur geändert wird.  
  
 ADD [COLUMN] *FieldName1*  
 Gibt den Namen des hinzuzufügenden Felds an.  
  
 ALTER [COLUMN] *FieldName1*  
 Gibt den Namen eines vorhandenen Felds an, das geändert werden soll.  
  
 *FieldType* [( *nFieldWidth* [, *nPrecision*]])  
 Gibt den Feldtyp, die Feldbreite und die Feldgenauigkeit (Anzahl der Dezimalstellen) für ein neues oder geändertes Feld an.  
  
 *FieldType* ist ein einzelner Buchstabe, der den [Datentyp](../../odbc/microsoft/visual-foxpro-field-data-types.md)des Felds angibt. Einige Felddatentypen erfordern, dass Sie *nFieldWidth* oder *nPrecision* oder beides angeben.  
  
 *nFieldWidth* und *nPrecision* werden für die Typen D, G, I, L, M, P, T und Y ignoriert. Standardmäßig ist *nPrecision* Null (keine Dezimalstellen), wenn *nPrecision* für die Typen B, F oder N nicht enthalten ist.  
  
 NULL &#124; NOT NULL  
 Ermöglicht oder verhindert NULL-Werte im Feld.  
  
 Wenn Sie NULL und NOT NULL weglassen, bestimmt die aktuelle Einstellung von SET NULL, ob NULL-Werte im Feld zulässig sind. Wenn Sie jedoch NULL und NOT NULL weglassen und die PRIMARY KEY- oder UNIQUE-Klausel einschließen, wird die aktuelle Einstellung von SET NULL ignoriert, und das Feld ist standardmäßig NICHT NULL.  
  
 CHECK *lExpression1*  
 Gibt eine Validierungsregel für das Feld an. *lExpression1* muss zu einem logischen Ausdruck ausgewertet werden und kann eine benutzerdefinierte Funktion oder eine gespeicherte Prozedur sein. Wenn ein leerer Datensatz angehängt wird, wird die Validierungsregel überprüft. Ein Fehler wird generiert, wenn die Validierungsregel keinen leeren Feldwert in einem angehängten Datensatz zulässt.  
  
 ERROR *cMessageText1*  
 Gibt die Fehlermeldung an, die angezeigt wird, wenn die Feldvalidierungsregel einen Fehler generiert.  
  
 DEFAULT *eExpression1*  
 Gibt einen Standardwert für das Feld an. Der Datentyp von *eExpression1* muss mit dem Datentyp für das Feld übereinstimmen.  
  
 PRIMARY KEY  
 Erstellt ein primäres Index-Tag. Das Index-Tag hat denselben Namen wie das Feld.  
  
 UNIQUE  
 Erstellt ein Kandidatenindex-Tag mit demselben Namen wie das Feld.  
  
> [!NOTE]  
>  Kandidatenindizes (erstellt durch Einschließen der UNIQUE-Option, die für DIE ANSI-Kompatibilität in ALTER TABLE oder CREATE TABLE bereitgestellt wird) unterscheiden sich von Indizes, die mit der Option UNIQUE im Befehl INDEX erstellt wurden. Ein Index, der mit UNIQUE im Index-Befehl erstellt wurde, ermöglicht doppelte Indexschlüssel. Kandidatenindizes lassen keine doppelten Indexschlüssel zu.  
  
 Nullwerte und doppelte Datensätze sind in einem Feld, das für einen Primär- oder Kandidatenindex verwendet wird, nicht zulässig.  
  
 Wenn Sie ein neues Feld mithilfe von ADD COLUMN erstellen, generiert Visual FoxPro keinen Fehler, wenn Sie einen Primär- oder Kandidatenindex für ein Feld erstellen, das NULL-Werte unterstützt. Visual FoxPro generiert jedoch einen Fehler, wenn Sie versuchen, einen Null- oder doppelten Wert in ein Feld einzugeben, das für einen Primär- oder Kandidatenindex verwendet wird.  
  
 Wenn Sie ein vorhandenes Feld ändern und der primäre oder Kandidatindexausdruck aus Feldern in der Tabelle besteht, überprüft Visual FoxPro die Felder, um festzustellen, ob sie NULL-Werte oder doppelte Datensätze enthalten. Wenn dies der Fall ist, generiert Visual FoxPro einen Fehler, und die Tabelle wird nicht geändert.  
  
 VERWEISE *TableName2* TAG *TagName1*  
 Gibt die übergeordnete Tabelle an, zu der eine persistente Beziehung eingerichtet wird. TAG *TagName1* gibt das Index-Tag der übergeordneten Tabelle an, auf dem die Beziehung basiert. Index-Tag-Namen können bis zu 10 Zeichen enthalten.  
  
 NOCPTRANS  
 Verhindert die Übersetzung in eine andere Codepage für Zeichen- und Memofelder. Wenn die Tabelle in eine andere Codepage konvertiert wird, werden die Felder, für die NOCPTRANS angegeben wurde, nicht übersetzt. NOCPTRANS kann nur für Zeichen- und Memofelder angegeben werden.  
  
 Im folgenden Beispiel wird eine Tabelle mit dem Namen mytable erstellt, die zwei Zeichenfelder und zwei Memofelder enthält. Das zweite Zeichenfeld, char2, und das zweite Memofeld, memo2, enthalten NOCPTRANS, um eine Übersetzung zu verhindern.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 ALTER [COLUMN] *FieldName2*  
 Gibt den Namen eines vorhandenen Felds an, das geändert werden soll.  
  
 SET DEFAULT *eExpression2*  
 Gibt einen neuen Standardwert für ein vorhandenes Feld an. Der Datentyp von *eExpression2* muss mit dem Datentyp für das Feld übereinstimmen.  
  
 SET CHECK *lExpression2*  
 Gibt eine neue Validierungsregel für ein vorhandenes Feld an. *lExpression2* muss zu einem logischen Ausdruck ausgewertet werden und kann eine benutzerdefinierte Funktion oder eine gespeicherte Prozedur sein.  
  
 FEHLER *cMessageText2*  
 Gibt die Fehlermeldung an, die angezeigt wird, wenn die Feldvalidierungsregel einen Fehler generiert. Die Meldung wird nur angezeigt, wenn Daten in einem Fenster Durchsuchen oder Bearbeiten geändert werden.  
  
 DROP DEFAULT  
 Entfernt den Standardwert für ein vorhandenes Feld.  
  
 DROP-CHECK  
 Entfernt die Validierungsregel für ein vorhandenes Feld.  
  
 DROP [COLUMN] *FieldName3*  
 Gibt ein Feld an, das aus der Tabelle entfernt werden soll. Durch das Entfernen eines Felds aus der Tabelle werden auch die Standardwerteinstellung und die Feldvalidierungsregel des Felds entfernt.  
  
 Wenn Indexschlüssel oder Triggerausdrücke auf das Feld verweisen, werden die Ausdrücke ungültig, wenn das Feld entfernt wird. In diesem Fall wird kein Fehler generiert, wenn das Feld entfernt wird, aber der ungültige Indexschlüssel oder Triggerausdrücke generiert Fehler zur Laufzeit.  
  
 SET CHECK *lExpression3*  
 Gibt die Tabellenvalidierungsregel an. *lExpression3* muss zu einem logischen Ausdruck ausgewertet werden und kann eine benutzerdefinierte Funktion oder eine gespeicherte Prozedur sein.  
  
 ERROR *cMessageText3*  
 Gibt die Fehlermeldung an, die angezeigt wird, wenn die Tabellenvalidierungsregel einen Fehler generiert. Die Meldung wird nur angezeigt, wenn Daten in einem Fenster Durchsuchen oder Bearbeiten geändert werden.  
  
 DROP-CHECK  
 Entfernt die Validierungsregel der Tabelle.  
  
 ADD PRIMARY KEY *eExpression3*TAG *TagName2*  
 Fügt der Tabelle einen primären Index hinzu. *eExpression3* gibt den primären Indexschlüsselausdruck an, und *TagName2* gibt den Namen des primären Indextags an. Index-Tag-Namen können bis zu 10 Zeichen enthalten. Wenn TAG *TagName2* weggelassen wird und *eExpression3* ein einzelnes Feld ist, hat das primäre Index-Tag denselben Namen wie das in *eExpression3*angegebene Feld.  
  
 DROP-PRIMÄRSCHLÜSSEL  
 Entfernt den primären Index und sein Index-Tag. Da eine Tabelle nur über einen Primärschlüssel verfügen kann, ist es nicht erforderlich, den Namen des Primärschlüssels anzugeben. Durch das Entfernen des primären Index werden auch alle persistenten Beziehungen basierend auf dem Primärschlüssel gelöscht.  
  
 ADD UNIQUE *eExpression4*[TAG *TagName3*]  
 Fügt der Tabelle einen Kandidatenindex hinzu. *eExpression4* gibt den Kandidatenindexschlüsselausdruck an, und *TagName3* gibt den Namen des Kandidatenindex-Tags an. Index-Tag-Namen können bis zu 10 Zeichen enthalten. Wenn Sie TAG *TagName3* weglassen und *eExpression4* ein einzelnes Feld ist, hat das Kandidatenindex-Tag denselben Namen wie das in *eExpression4*angegebene Feld.  
  
 DROP UNIQUE TAG *TagName4*  
 Entfernt den Kandidatenindex und sein Index-Tag. Da eine Tabelle über mehrere Kandidatenschlüssel verfügen kann, müssen Sie den Namen des Kandidatenindex-Tags angeben.  
  
 ADD FOREIGN KEY [ *eExpression5*]TAG *TagName4*  
 Fügt der Tabelle einen fremden (nicht primären) Index hinzu. *eExpression5* gibt den Fremdindexschlüsselausdruck an, und *TagName4* gibt den Namen des Fremdindex-Tags an. Index-Tag-Namen können bis zu 10 Zeichen enthalten.  
  
 VERWEISE *TableName2*[TAG *TagName5*]  
 Gibt die übergeordnete Tabelle an, zu der eine persistente Beziehung eingerichtet wird. Fügen Sie TAG *TagName5* ein, um eine Beziehung basierend auf einem vorhandenen Index-Tag für die übergeordnete Tabelle einzurichten. Index-Tag-Namen können bis zu 10 Zeichen enthalten. Wenn Sie TAG *TagName5*weglassen, wird die Beziehung mithilfe des primären Index-Tags der übergeordneten Tabelle eingerichtet.  
  
 DROP FOREIGN KEY *TAG TagName6*[SAVE]  
 Löscht einen Fremdschlüssel, dessen Index-Tag *TagName6*ist. Wenn Sie SAVE weglassen, wird das Index-Tag aus dem Strukturindex gelöscht. Fügen Sie SAVE ein, um das Löschen des Index-Tags aus dem Strukturindex zu verhindern.  
  
 RENAME COLUMN *FieldName4*TO *FieldName5*  
 Ermöglicht es Ihnen, den Namen eines Felds in der Tabelle zu ändern. *FieldName4* gibt den Namen des Felds an, das umbenannt wird. *FieldName5* gibt den neuen Namen des Felds an.  
  
> [!CAUTION]  
>  Beim Umbenennen von Tabellenfeldern Vorsicht walten, da Indexausdrücke, Feld- und Tabellenvalidierungsregeln, Befehle und Funktionen auf die ursprünglichen Feldnamen verweisen können.  
  
 NOVALIDATE  
 Gibt an, dass Visual FoxPro Änderungen an der Struktur der Tabelle zulässt. Diese Änderungen können die Integrität der Daten in der Tabelle verletzen. Standardmäßig verhindert Visual FoxPro, dass ALTER TABLE Änderungen vornimmt, die die Integrität der Daten in der Tabelle verletzen. Schließen Sie NOVALIDATE ein, um dieses Standardverhalten zu überschreiben.  
  
## <a name="remarks"></a>Bemerkungen  
 ALTER TABLE kann verwendet werden, um die Struktur einer Tabelle zu ändern, die keiner Datenbank hinzugefügt wurde. Visual FoxPro generiert jedoch einen Fehler, wenn Sie beim Ändern einer freien Tabelle die Klauseln DEFAULT, FOREIGN KEY, PRIMARY KEY, REFERENCES oder SET einschließen.  
  
 ALTER TABLE kann die Tabelle neu erstellen, indem eine neue Tabellenüberschrift erstellt und Datensätze an den Tabellenkopf angehängt werden. Wenn Sie z. B. den Typ oder die Breite eines Felds ändern, kann dies dazu führen, dass die Tabelle neu erstellt wird.  
  
 Nachdem eine Tabelle neu erstellt wurde, werden Feldvalidierungsregeln für alle Felder ausgeführt, deren Typ oder Breite geändert wird. Wenn Sie den Typ oder die Breite eines Felds in der Tabelle ändern, wird die Tabellenregel ausgeführt.  
  
 Wenn Sie Feld- oder Tabellenvalidierungsregeln für eine Tabelle mit Datensätzen ändern, testet Visual FoxPro die neuen Feld- oder Tabellenvalidierungsregeln anhand der vorhandenen Daten und gibt eine Warnung beim ersten Auftreten einer Feld- oder Tabellenvalidierungsregel oder einer Triggerverletzung aus.  
  
 Wenn sich die geänderte Tabelle in einer Datenbank befindet, erfordert ALTER TABLE - SQL die ausschließliche Verwendung der Datenbank. Um eine Datenbank exklusiv zu öffnen, schließen Sie EXKLUSIV in OPEN DATABASE ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE TABLE - SQL-Befehl](../../odbc/microsoft/create-table-sql-command.md)   
 [Befehl INDEX](../../odbc/microsoft/index-command.md)
