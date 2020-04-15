---
title: INDEX-Befehl | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- index command [ODBC]
ms.assetid: 694e8cf5-2f69-4001-9c1e-b735a4da3aff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bcb30a49cb9f11ddd4c61621116aa4bd8ddcf186
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300030"
---
# <a name="index-command"></a>INDEX-Befehl
Erstellt eine Indexdatei zum Anzeigen und Zugreifen auf Tabellendatensätze in logischer Reihenfolge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
INDEX ON eExpression TO IDXFileName | TAG TagName [OF CDXFileName]  
   [FOR lExpression]  
   [COMPACT]  
   [ASCENDING | DESCENDING]  
   [UNIQUE | CANDIDATE]  
   [ADDITIVE]  
```  
  
## <a name="arguments"></a>Argumente  
 *eExpression*  
 Gibt einen Indexausdruck an, der den Namen eines Feldes oder felder aus der aktuellen Tabelle enthalten kann. Ein Indexschlüssel, der auf dem Indexausdruck basiert, wird in der Indexdatei für jeden Datensatz in der Tabelle erstellt. Visual FoxPro verwendet diese Tasten, um Datensätze in der Tabelle anzuzeigen und darauf zuzugreifen.  
  
> [!NOTE]  
>  Obwohl *eExpression* nicht empfohlen wird, kann es sich auch um eine Speichervariable, ein Arrayelement oder einen Feld- oder Feldausdruck aus einer Tabelle in einem anderen Arbeitsbereich erstrecken. Memo-Felder können nicht allein in Indexdateiausdrücken verwendet werden. sie müssen mit anderen Zeichenausdrücken kombiniert werden. Wenn Sie auf einen Index zugreifen, der eine Variable oder ein Feld enthält, die nicht mehr vorhanden sind oder nicht mehr gefunden werden können, generiert Visual FoxPro eine Fehlermeldung.  
  
 Wenn Sie versuchen, einen Index mit einem Schlüssel zu erstellen, der in der Länge variiert, wird der Schlüssel mit Leerzeichen aufgepolstert. Indexschlüssel variabler Länge werden in Visual FoxPro nicht unterstützt.  
  
 Es ist möglich, einen Indexschlüssel mit Nulllänge zu erstellen. Beispielsweise wird ein Indexschlüssel mit einer Länge von Null erstellt, wenn der Indexausdruck eine Teilzeichenfolge eines leeren Memofelds ist. Ein Indexschlüssel mit einer Länge von Null generiert eine Fehlermeldung. Wenn Visual FoxPro einen Index erstellt, werden Felder im ersten Datensatz in der Tabelle ausgewertet. Wenn ein Feld leer ist, kann es erforderlich sein, einige temporäre Daten in das Feld im ersten Datensatz einzugeben, um einen Indexschlüssel mit 0 Länge zu verhindern.  
  
 TO *IDXFileName*  
 Erstellt eine .idx Indexdatei. Die Indexdatei erhält die Standarderweiterung .idx.  
  
 *TAG-Tagname*[VON *CDXFileName*]  
 Erstellt eine zusammengesetzte Indexdatei. Eine zusammengesetzte Indexdatei ist eine einzelne Indexdatei, die aus einer beliebigen Anzahl separater Tags (Indexeinträge) besteht. Jedes Tag wird durch seinen eindeutigen Tagnamen identifiziert. Tag-Namen müssen mit einem Buchstaben oder einem Unterstrich beginnen und können aus einer beliebigen Kombination von bis zu 10 Buchstaben, Ziffern oder Unterstrichen bestehen. Die Anzahl der Tags in einer zusammengesetzten Indexdatei ist nur durch verfügbaren Arbeitsspeicher und Speicherplatz begrenzt.  
  
 Zusammengesetzte Indexdateien mit mehreren Einträgen sind immer kompakt. Es ist nicht erforderlich, COMPACT beim Erstellen einer zusammengesetzten Indexdatei einzuschließen. Namen von zusammengesetzten Indexdateien erhalten eine .cdx-Erweiterung.  
  
 Es können zwei Arten von zusammengesetzten Indexdateien erstellt werden: strukturelle und nicht strukturelle.  
  
 **Strukturelle zusammengesetzte Indexdateien** Sie können eine strukturelle zusammengesetzte Indexdatei mit TAG *TagName* erstellen, indem Sie die optionale OF *CDXFileName-Klausel* ausschließen. Eine strukturelle zusammengesetzte Indexdatei hat immer denselben Basisnamen wie die Tabelle und wird automatisch geöffnet, wenn die Tabelle geöffnet wird.  
  
 **Nicht strukturelle zusammengesetzte Indexdateien** Sie können eine nicht strukturelle zusammengesetzte Indexdatei erstellen, indem Sie OF *CDXFileName* nach TAG *TagName*einschließen. Im Gegensatz zu einer strukturellen zusammengesetzten Indexdatei muss eine nicht strukturelle zusammengesetzte Indexdatei explizit mit der INDEX-Klausel in USE geöffnet werden.  
  
 Wenn bereits eine zusammengesetzte Indexdatei erstellt und geöffnet wurde, fügt die Ausgabe von INDEX mit TAG *TagName* der zusammengesetzten Indexdatei ein Tag hinzu.  
  
 FÜR *lExpression*  
 Gibt eine Bedingung an, bei der nur Datensätze verfügbar sind, die den Filterausdruck *lExpression* erfüllen. Indexschlüssel werden in der Indexdatei für nur die Datensätze erstellt, die dem Filterausdruck entsprechen.  
  
 Visual FoxPro Rushmore Technologie optimiert einen INDEX ... FOR *lExpression-Befehl,* wenn *lExpression* ein optimierbarer Ausdruck ist. Verwenden Sie einen optimierten Ausdruck in der FOR-Klausel, um eine optimale Leistung zu erzielen.  
  
 Kompakte  
 Erstellt eine kompakte .idx-Datei.  
  
 Aufsteigender  
 Gibt eine aufsteigende Reihenfolge für die .cdx-Datei an. Standardmäßig werden .cdx-Tags in aufsteigender Reihenfolge erstellt. (Sie können ASCENDING als Erinnerung an die Reihenfolge der Indexdatei einschließen.) Eine Tabelle kann in umgekehrter Reihenfolge indiziert werden, indem DESCENDING eingebunden wird.  
  
 Absteigend  
 Gibt eine absteigende Reihenfolge für die .cdx-Datei an. Sie können DESCENDING nicht beim Erstellen von .idx Indexdateien einschließen.  
  
 UNIQUE  
 Gibt an, dass nur der erste Datensatz, der mit einem bestimmten Indexschlüsselwert gefunden wurde, in einer IDX-Datei oder einem .cdx-Tag enthalten ist. UNIQUE kann verwendet werden, um die Anzeige oder den Zugriff auf doppelte Datensätze zu verhindern. Alle Datensätze, die mit doppelten Indexschlüsseln hinzugefügt werden, werden aus der Indexdatei ausgeschlossen. Die Verwendung der UNIQUE-Option von INDEX ist identisch mit der Ausführung von SET UNIQUE ON vor der Ausgabe von INDEX oder REINDEX.  
  
 Wenn ein UNIQUE-Index- oder Index-Tag aktiv ist und ein doppelter Datensatz so geändert wird, dass sein Indexschlüssel geändert wird, wird das Index- oder Index-Tag aktualisiert. Auf den nächsten doppelten Datensatz mit dem ursprünglichen Indexschlüssel kann jedoch erst zugegriffen oder angezeigt werden, wenn Sie die Datei mit REINDEX neu indizieren.  
  
 Kandidat  
 Erstellt ein Kandidatenstrukturindex-Tag. Das CANDIDATE-Schlüsselwort kann nur beim Erstellen eines strukturellen Index-Tags eingeschlossen werden. Andernfalls generiert Visual FoxPro eine Fehlermeldung.  
  
 Ein Kandidatenindex-Tag verhindert doppelte Werte im Feld oder in der Kombination von Feldern, die im Indexausdruck *eExpression*angegeben sind. Der Begriff *Kandidat* bezieht sich auf die Art des Index; Da Kandidatenindizes doppelte Werte verhindern, qualifizieren sie sich als "Kandidat" als Primärindex.  
  
 Visual FoxPro generiert einen Fehler, wenn Sie ein Kandidatenindex-Tag für ein Feld oder eine Kombination von Feldern erstellen, die bereits doppelte Werte enthalten.  
  
 Additiv  
 Öffnet alle zuvor geöffneten Indexdateien. Wenn Sie die ADDITIVE-Klausel beim Erstellen einer Indexdatei oder dateien für eine Tabelle mit INDEX weglassen, werden alle zuvor geöffneten Indexdateien (mit Ausnahme des strukturellen zusammengesetzten Indexes) geschlossen.  
  
## <a name="remarks"></a>Bemerkungen  
 Datensätze in einer Tabelle mit einer Indexdatei werden in der vom Indexausdruck angegebenen Reihenfolge angezeigt und darauf zugegriffen. Die physische Reihenfolge der Datensätze in der Tabelle wird durch eine Indexdatei nicht geändert.  
  
## <a name="index-types"></a>Indextypen  
 Mit Visual FoxPro können Sie zwei Arten von Indexdateien erstellen:  
  
-   Zusammengesetzte .cdx Indexdateien, die mehrere Indexeinträge enthalten, die als Tags bezeichnet werden  
  
-   .idx Indexdateien, die einen Indexeintrag enthalten  
  
 Sie können auch eine strukturelle zusammengesetzte Indexdatei erstellen, die automatisch mit der Tabelle geöffnet wird.  
  
> [!NOTE]  
>  Da strukturelle zusammengesetzte Indexdateien automatisch geöffnet werden, wenn die Tabelle geöffnet wird, sind sie der bevorzugte Indextyp.  
  
 Schließen Sie COMPACT ein, um kompakte .idx Indexdateien zu erstellen. Zusammengesetzte Indexdateien sind immer kompakt.  
  
## <a name="index-order-and-updating"></a>Indexreihenfolge und Aktualisierung  
 Nur eine Indexdatei (die Masterindexdatei) oder ein Tag (das Master-Tag) steuert die Reihenfolge, in der die Tabelle angezeigt oder zugegriffen wird. Bestimmte Befehle (z. B. SEEK) verwenden die Masterindexdatei oder das Tag, um nach Datensätzen zu suchen. Alle geöffneten .idx- und .cdx-Indexdateien werden jedoch aktualisiert, wenn Änderungen an der Tabelle vorgenommen werden.  
  
## <a name="user-defined-functions"></a>Benutzerdefinierte Funktionen  
 Obwohl ein Indexausdruck eine benutzerdefinierte Funktion enthalten kann, sollten Sie keine benutzerdefinierten Funktionen in einem Indexausdruck verwenden. Benutzerdefinierte Funktionen in einem Indexausdruck erhöhen die Zeit, die zum Erstellen oder Aktualisieren des Indexes benötigt wird. Außerdem können Indexaktualisierungen möglicherweise nicht auftreten, wenn eine benutzerdefinierte Funktion für einen Indexausdruck verwendet wird.  
  
 Wenn Sie eine benutzerdefinierte Funktion in einem Indexausdruck verwenden, muss Visual FoxPro in der Lage sein, die benutzerdefinierte Funktion zu finden. Wenn Visual FoxPro einen Index erstellt, wird der Indexausdruck in der Indexdatei gespeichert, aber nur ein Verweis auf die benutzerdefinierte Funktion wird im Indexausdruck enthalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER TABLE - SQL-Befehl](../../odbc/microsoft/alter-table-sql-command.md)   
 [LÖSCHEN TAG-Befehl](../../odbc/microsoft/delete-tag-command.md)   
 [SET COLLATE-Befehl](../../odbc/microsoft/set-collate-command.md)   
 [Befehl SET UNIQUE](../../odbc/microsoft/set-unique-command.md)
