---
title: ALTER TABLE-SQL-Befehl | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304711"
---
# <a name="alter-table---sql-command"></a>ALTER TABLE (SQL-Befehl)
Ändert die Struktur einer Tabelle Programm gesteuert.  
  
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
  
 Add [Column] *FieldName1*  
 Gibt den Namen des hinzu zufügenden Felds an.  
  
 Alter [Column] *FieldName1*  
 Gibt den Namen eines vorhandenen Felds an, das geändert werden soll.  
  
 *FieldType* [( *nfieldwidth* [, *nprecision*]])  
 Gibt den Feldtyp, die Feldbreite und die Feld Genauigkeit (Anzahl der Dezimalstellen) für ein neues oder geändertes Feld an.  
  
 *FieldType* ist ein einzelner Buchstabe, der den [Datentyp](../../odbc/microsoft/visual-foxpro-field-data-types.md)des Felds angibt. Einige Feld Datentypen erfordern, dass Sie *nfieldwidth* oder *nprecision* oder beides angeben.  
  
 *nfieldwidth* und *nprecision* werden für die Typen D, G, I, L, M, P, T und Y ignoriert. Standardmäßig ist " *nprecision* " NULL (keine Dezimalstellen), wenn " *nprecision* " für den Typ "B", "F" oder "N" nicht enthalten ist.  
  
 NULL &#124; NOT NULL  
 Erlaubt oder verhindert NULL-Werte im-Feld.  
  
 Wenn Sie NULL und NOT NULL weglassen, bestimmt die aktuelle Einstellung von SET NULL, ob NULL-Werte im Feld zulässig sind. Wenn Sie jedoch NULL und NOT NULL weglassen und die PRIMARY KEY-oder Unique-Klausel einschließen, wird die aktuelle Einstellung von SET NULL ignoriert, und das Feld ist standardmäßig nicht NULL.  
  
 *LExpression1* überprüfen  
 Gibt eine Validierungs Regel für das Feld an. *lExpression1* muss zu einem logischen Ausdruck ausgewertet werden und kann eine benutzerdefinierte Funktion oder eine gespeicherte Prozedur sein. Wenn ein leerer Datensatz angehängt wird, wird die Validierungs Regel überprüft. Ein Fehler wird generiert, wenn die Validierungs Regel keinen leeren Feldwert in einem angefügten Datensatz zulässt.  
  
 Fehler *cMessageText1*  
 Gibt die Fehlermeldung an, die angezeigt wird, wenn die Feld Validierungs Regel einen Fehler generiert.  
  
 Standard *eExpression1*  
 Gibt einen Standardwert für das Feld an. Der Datentyp von *eExpression1* muss mit dem Datentyp für das Feld identisch sein.  
  
 PRIMARY KEY  
 Erstellt ein primäres Indextag. Das Indextag hat denselben Namen wie das Feld.  
  
 UNIQUE  
 Erstellt ein Kandidaten Indextag, das denselben Namen wie das Feld hat.  
  
> [!NOTE]  
>  Kandidaten Indizes (erstellt durch einschließen der UNIQUE-Option, die für die ANSI-Kompatibilität in ALTER TABLE oder CREATE TABLE bereitgestellt werden) unterscheiden sich von Indizes, die mit der UNIQUE-Option im Index-Befehl erstellt wurden. Ein Index, der mithilfe von Unique im Index-Befehl erstellt wurde, ermöglicht doppelte Index Schlüssel. Kandidaten Indizes lassen keine doppelten Index Schlüssel zu.  
  
 NULL-Werte und doppelte Datensätze sind in einem Feld, das für einen primären Index oder einen Kandidaten Index verwendet wird, nicht zulässig.  
  
 Wenn Sie ein neues Feld mithilfe von "Spalte hinzufügen" erstellen, generiert Visual FoxPro keinen Fehler, wenn Sie einen primären Index oder einen Kandidaten Index für ein Feld erstellen, das NULL-Werte unterstützt. Von Visual FoxPro wird jedoch ein Fehler generiert, wenn Sie versuchen, einen NULL-oder einen doppelten Wert in ein Feld einzugeben, das für einen primären oder Kandidaten Index verwendet wird.  
  
 Wenn Sie ein vorhandenes Feld ändern und der primäre oder Kandidat Index Ausdruck aus Feldern in der Tabelle besteht, prüft Visual FoxPro die Felder, um zu überprüfen, ob Sie NULL-Werte oder doppelte Datensätze enthalten. Wenn dies der Fall ist, generiert Visual FoxPro einen Fehler, und die Tabelle wird nicht geändert.  
  
 Verweise *TableName2* Tag *TagName1*  
 Gibt die übergeordnete Tabelle an, mit der eine persistente Beziehung hergestellt wird. Tag *TagName1* gibt das Indextag der übergeordneten Tabelle an, auf dem die Beziehung basiert. Indextagnamen können bis zu 10 Zeichen enthalten.  
  
 Nocptrans  
 Verhindert die Übersetzung in eine andere Codepage für Zeichen-und Memo Felder. Wenn die Tabelle in eine andere Codepage konvertiert wird, werden die Felder, für die "nocptrans" angegeben wurde, nicht übersetzt. "Nocptrans" kann nur für Zeichen-und Memo Felder angegeben werden.  
  
 Im folgenden Beispiel wird eine Tabelle mit dem Namen MyTable erstellt, die zwei Zeichenfelder und zwei Memo Felder enthält. Das zweite Zeichenfeld, char2 und das zweite Memo Feld memo2, enthalten "nocptrans", um die Übersetzung zu verhindern.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 Alter [Column] *FieldName2*  
 Gibt den Namen eines vorhandenen Felds an, das geändert werden soll.  
  
 Standard *eExpression2* festlegen  
 Gibt einen neuen Standardwert für ein vorhandenes Feld an. Der Datentyp von *eExpression2* muss mit dem Datentyp für das Feld identisch sein.  
  
 Check *lExpression2* festlegen  
 Gibt eine neue Validierungs Regel für ein vorhandenes Feld an. *lExpression2* muss zu einem logischen Ausdruck ausgewertet werden und kann eine benutzerdefinierte Funktion oder eine gespeicherte Prozedur sein.  
  
 Fehler *cMessageText2*  
 Gibt die Fehlermeldung an, die angezeigt wird, wenn die Feld Validierungs Regel einen Fehler generiert. Die Meldung wird nur angezeigt, wenn Daten innerhalb eines Fensters zum Durchsuchen oder bearbeiten geändert werden.  
  
 DROP DEFAULT  
 Entfernt den Standardwert für ein vorhandenes Feld.  
  
 Drop Check  
 Entfernt die Validierungs Regel für ein vorhandenes Feld.  
  
 Drop [Column] *FieldName3*  
 Gibt ein Feld an, das aus der Tabelle entfernt werden soll. Wenn Sie ein Feld aus der Tabelle entfernen, werden auch die Standardwert Einstellung und Feld Validierungs Regel des Felds entfernt.  
  
 Wenn Index Schlüssel-oder auslöserausdrücke auf das Feld verweisen, werden die Ausdrücke ungültig, wenn das Feld entfernt wird. In diesem Fall wird kein Fehler generiert, wenn das Feld entfernt wird, aber der ungültige Index Schlüssel oder die auslöserausdrücke generieren zur Laufzeit Fehler.  
  
 Check *lExpression3* festlegen  
 Gibt die Tabellen Validierungs Regel an. *lExpression3* muss zu einem logischen Ausdruck ausgewertet werden und kann eine benutzerdefinierte Funktion oder eine gespeicherte Prozedur sein.  
  
 Fehler *cMessageText3*  
 Gibt die Fehlermeldung an, die angezeigt wird, wenn die Tabellen Validierungs Regel einen Fehler generiert. Die Meldung wird nur angezeigt, wenn Daten innerhalb eines Fensters zum Durchsuchen oder bearbeiten geändert werden.  
  
 Drop Check  
 Entfernt die Validierungs Regel der Tabelle.  
  
 *EExpression3*-Tag hinzufügen *TagName2*  
 Fügt der Tabelle einen primären Index hinzu. *eExpression3* gibt den primär Index Schlüssel Ausdruck an, und *TagName2* gibt den Namen des primären Indextags an. Indextagnamen können bis zu 10 Zeichen enthalten. Wenn Tag *TagName2* ausgelassen und *eExpression3* ein einzelnes Feld ist, hat das primäre Indextag denselben Namen wie das in *eExpression3*angegebene Feld.  
  
 Primärschlüssel löschen  
 Entfernt den primären Index und das zugehörige Indextag. Da eine Tabelle nur über einen Primärschlüssel verfügen kann, ist es nicht erforderlich, den Namen des Primärschlüssels anzugeben. Wenn Sie den primären Index entfernen, werden auch alle permanenten Beziehungen basierend auf dem Primärschlüssel gelöscht.  
  
 Eindeutige *eExpression4*hinzufügen [Tag *TagName3*]  
 Fügt der Tabelle einen Kandidaten Index hinzu. *eExpression4* gibt den Schlüssel Ausdruck für den Kandidaten Index an, und *TagName3* gibt den Namen des Kandidaten Index Tags an. Indextagnamen können bis zu 10 Zeichen enthalten. Wenn Sie Tag *TagName3* weglassen und *eExpression4* ein einzelnes Feld ist, hat das Kandidaten Indextag denselben Namen wie das in *eExpression4*angegebene Feld.  
  
 Löschen eines eindeutigen Tags *TagName4*  
 Entfernt den Kandidaten Index und das zugehörige Indextag. Da eine Tabelle über mehrere Kandidaten Schlüssel verfügen kann, müssen Sie den Namen des Kandidaten Index Tags angeben.  
  
 Hinzufügen eines fremd Schlüssels [ *eExpression5*] Tag *TagName4*  
 Fügt der Tabelle einen fremd Index (nonprimary) hinzu. *eExpression5* gibt den fremd Index Schlüssel Ausdruck an, und *TagName4* gibt den Namen des fremden Indextags an. Indextagnamen können bis zu 10 Zeichen enthalten.  
  
 Verweise *TableName2*[Tag *TagName5*]  
 Gibt die übergeordnete Tabelle an, mit der eine persistente Beziehung hergestellt wird. TagTagName5 *TagName5* einschließen, um eine Beziehung basierend auf einem vorhandenen Indextag für die übergeordnete Tabelle herzustellen. Indextagnamen können bis zu 10 Zeichen enthalten. Wenn Sie Tag *TagName5*weglassen, wird die Beziehung unter Verwendung des primären Indextags der übergeordneten Tabelle festgelegt.  
  
 Drop Foreign Key-Tag *TagName6*[Speichern]  
 Löscht einen Fremdschlüssel, dessen Indextag *TagName6*ist. Wenn Sie "Speichern" weglassen, wird das Indextag aus dem strukturellen Index gelöscht. Fügen Sie Save ein, um das Löschen des Indextags aus dem strukturellen Index zu verhindern.  
  
 Spalte *FieldName4*in *FieldName5* umbenennen  
 Ermöglicht es Ihnen, den Namen eines Felds in der Tabelle zu ändern. *FieldName4* gibt den Namen des Felds an, das umbenannt wird. *FieldName5* gibt den neuen Namen des Felds an.  
  
> [!CAUTION]  
>  Achten Sie auf das Umbenennen von Tabellen Feldern, da Index Ausdrücke, Feld-und Tabellen Validierungsregeln, Befehle und Funktionen möglicherweise auf die ursprünglichen Feldnamen verweisen.  
  
 NOVALIDATE  
 Gibt an, dass Visual FoxPro Änderungen an der Struktur der Tabelle zulässt. Diese Änderungen können die Integrität der Daten in der Tabelle verletzen. Standardmäßig verhindert Visual FoxPro, dass ALTER TABLE Änderungen vornimmt, die die Integrität der Daten in der Tabelle verletzen. Fügen Sie novalidate ein, um dieses Standardverhalten zu überschreiben.  
  
## <a name="remarks"></a>Bemerkungen  
 ALTER TABLE kann verwendet werden, um die Struktur einer Tabelle zu ändern, die einer Datenbank nicht hinzugefügt wurde. Allerdings generiert Visual FoxPro einen Fehler, wenn Sie beim Ändern einer freien Tabelle die Standard-, Fremdschlüssel-, Primary Key-, References-oder Set-Klauseln einschließen.  
  
 ALTER TABLE kann die Tabelle neu erstellen, indem ein neuer Tabellenheader erstellt und Datensätze an den Tabellenheader angehängt werden. Beispielsweise kann das Ändern des Typs oder der Breite eines Felds dazu führen, dass die Tabelle neu erstellt wird.  
  
 Nachdem eine Tabelle neu erstellt wurde, werden Feld Validierungsregeln für alle Felder ausgeführt, deren Typ oder Breite geändert wird. Wenn Sie den Typ oder die Breite eines Felds in der Tabelle ändern, wird die Tabellen Regel ausgeführt.  
  
 Wenn Sie Feld-oder Tabellen Validierungsregeln für eine Tabelle ändern, die Datensätze enthält, testet Visual FoxPro die neuen Feld-oder Tabellen Validierungsregeln für die vorhandenen Daten und gibt eine Warnung aus, wenn das erste Vorkommen einer Feld-oder Tabellen Validierungs Regel oder einer auslöserverletzung eine Warnung ausgegeben wird.  
  
 Wenn sich die Tabelle, die Sie ändern, in einer Datenbank befindet, ist für ALTER TABLE-SQL eine exklusive Verwendung der Datenbank erforderlich. Wenn Sie eine Datenbank für die exklusive Verwendung öffnen möchten, schließen Sie exklusive in Open Database ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE TABLE-SQL-Befehl](../../odbc/microsoft/create-table-sql-command.md)   
 [Befehl INDEX](../../odbc/microsoft/index-command.md)
