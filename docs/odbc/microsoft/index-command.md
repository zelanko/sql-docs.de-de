---
title: INDEX-Befehl | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 864f6fa78ab1ef23b7db3a0be4c85738b95ea72d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62471258"
---
# <a name="index-command"></a>INDEX-Befehl
Erstellt eine Indexdatei zum Anzeigen und Zugreifen auf Tabellendatensätze in einer logischen Reihenfolge.  
  
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
 Gibt einen Indexausdruck, der den Namen der ein Feld oder Felder aus der aktuellen Tabelle enthalten kann. Ein Indexschlüssel, die basierend auf der Indexausdruck wird in der Indexdatei für jeden Datensatz in der Tabelle erstellt. Visual FoxPro anhand dieser Schlüssel anzeigen und Zugreifen auf Datensätze in der Tabelle.  
  
> [!NOTE]  
>  Es wird jedoch nicht empfohlen, *eExpression* kann auch sein, eine Arbeitsspeicher-Variable, die ein Arrayelement oder ein Feld oder die Feldausdruck aus einer Tabelle in einem anderen Arbeitsbereich. Memo-Felder können nicht allein in Indexausdrücke-Datei verwendet werden. Sie müssen mit anderen Zeichenausdrücken kombiniert werden. Wenn Sie einen Index, der enthält eine Variable oder ein Feld, das nicht mehr vorhanden ist oder nicht gefunden werden kann zugreifen, generiert Visual FoxPro eine Fehlermeldung angezeigt.  
  
 Wenn Sie versuchen, einen Index mit einem Schlüssel zu erstellen, die Länge variiert, wird der Schlüssel mit Leerzeichen aufgefüllt werden. Indexschlüssel mit variabler Länge werden in der Visual FoxPro nicht unterstützt.  
  
 Es ist möglich, einen Indexschlüssel zu erstellen, mit der Länge Null. Beispielsweise wird keine Länge Schlüssel eines Indexes erstellt, wenn es sich bei der Indexausdruck eine Teilzeichenfolge des eine leere Memofelds darstellt. 0 (null) Länge Schlüssel eines Indexes wird eine Fehlermeldung generiert. Wenn Sie Visual FoxPro einen Index erstellt wird, wird Feldern in den ersten Datensatz in der Tabelle ausgewertet. Wenn ein Feld leer ist, kann es erforderlich, geben Sie einige temporäre Daten in das Feld in den ersten Datensatz aus, um zu verhindern, dass ein 0-Länge Indexschlüssel enthalten sein.  
  
 UM *IDXFileName*  
 Erstellt eine Index IDX-Datei. Die Indexdatei wird die standardmäßige Erweiterung IDX angegeben.  
  
 TAG *TagName*[OF *CDXFileName*]  
 Erstellt eine Datei zusammengesetzten Index. Eine zusammengesetzten Index-Datei ist ein einzelner Index-Datei, die einer beliebigen Anzahl von separaten Tags (Indexeinträge) besteht. Jedes Tag wird anhand seines Tagnamens des eindeutig identifiziert. Tag-Namen müssen mit einem Buchstaben oder einem Unterstrich beginnen und können aus einer beliebigen Kombination von bis zu 10 Buchstaben, Ziffern oder Unterstrichen bestehen. Die Anzahl der Tags in einer zusammengesetzten Index-Datei wird nur durch den verfügbaren Arbeitsspeicher und Speicherplatz beschränkt.  
  
 Unterschiedlichem zusammengesetzten Indexdateien sind stets compact. Es ist nicht erforderlich, COMPACT beim Erstellen einer zusammengesetzten Index-Datei eingeschlossen werden sollen. Namen von zusammengesetzten Indexdateien erhalten eine CDX-Erweiterung.  
  
 Zwei Arten von Dateien von zusammengesetzten Index erstellt werden können: strukturelle und nonstructural.  
  
 **Strukturelle Index Verbunddateien** können Sie eine strukturelle zusammengesetzten Index-Datei erstellen, mit TAG *TagName* durch Ausschließen des optionalen OF *CDXFileName* Klausel. Eine Datei strukturelle zusammengesetzten Index immer hat den gleichen Basisnamen wie die Tabelle und wird automatisch geöffnet, wenn die Tabelle geöffnet wird.  
  
 **Nonstructural Index Verbunddateien** können Sie eine nonstructural zusammengesetzten Index-Datei erstellen, durch Einschließen der *CDXFileName* nach TAG *TagName*. Im Gegensatz zu einer Datei strukturelle zusammengesetzten Index muss eine Datei nonstructural zusammengesetzten Index explizit mit der INDEX-Klausel verwendet geöffnet werden.  
  
 Wenn eine Datei zusammengesetzten Index bereits erstellt und geöffnet wurde, ausgeben INDEX mit TAG *TagName* der zusammengesetzten Index-Datei ein Tag hinzugefügt.  
  
 FOR *lExpression*  
 Gibt eine Bedingung, bei dem nur die Datensätze, die den Filterausdruck erfüllen *lExpression* stehen für Sie Anzeige- und Zugriff Indexschlüssel werden in der Indexdatei für nur die Datensätze, die mit dem Filterausdruck erstellt.  
  
 Visual FoxPro-Rushmore Technologie optimiert einen INDEX... FÜR *lExpression* -Befehl, wenn *lExpression* ist ein optimierbarer Ausdruck. Verwenden Sie für eine optimale Leistung einen optimierbaren Ausdruck in der FOR-Klausel.  
  
 KOMPRIMIEREN  
 Erstellt eine kompakte IDX-Datei.  
  
 AUFSTEIGEND  
 Gibt einer aufsteigenden Reihenfolge für die CDX-Datei an. Standardmäßig werden CDX-Tags erstellt, in aufsteigender Reihenfolge. (Sie können als Erinnerung an die Indexdatei Reihenfolge AUFSTEIGEND einschließen.) Eine Tabelle kann in umgekehrter Reihenfolge durch Einschließen von ABSTEIGEND indiziert werden.  
  
 ABSTEIGEND  
 Gibt eine absteigende Reihenfolge für die CDX-Datei an. Wenn IDX Indexdateien erstellen, können Sie keine ABSTEIGEND einschließen.  
  
 UNIQUE  
 Gibt an, dass nur der erste Datensatz mit einem bestimmten Indexschlüsselwert gefunden, die in einer IDX-Datei oder ein CDX-Tag enthalten ist. UNIQUE kann verwendet werden, um die Anzeige des oder der Zugriff auf doppelte Datensätze zu verhindern. Alle Datensätze mit Doppelte Indexschlüssel hinzugefügt werden, werden von der Indexdatei ausgeschlossen. Verwenden die Möglichkeit, EINDEUTIGEN INDEX ist identisch mit dem SET UNIQUE ON ausführen, bevor Sie die Index- oder REINDEX ausgeben.  
  
 Wenn ein EINDEUTIGER Index oder Index Tag aktiv ist und in einer Weise, die seinen Indexschlüssel ändert ein doppelter Datensatz geändert wird, wird der Index oder Index-Tag aktualisiert. Allerdings kann nicht der nächsten doppelte Datensatz mit der ursprünglichen Indexschlüssel zugegriffen oder angezeigt, bis Sie die Datei mit REINDEX neu indizieren.  
  
 KANDIDATEN  
 Erstellt ein Kandidat strukturelle Index-Tag. Die CANDIDATE-Schlüsselwort kann enthalten sein, nur, wenn ein Tag strukturelle Index zu erstellen; Visual FoxPro generiert, andernfalls eine Fehlermeldung angezeigt.  
  
 Ein Kandidat Index-Tag wird verhindert, dass doppelte Werte in das Feld oder eine Kombination von Feldern, angegeben in den Indexausdruck *eExpression*. Der Begriff *Candidate* bezieht sich auf den Typ des Indexes, da doppelte Werte von möglichen Indizes vermeiden, diese infrage kommt als "Kandidat" ein primärer Index.  
  
 Visual FoxPro generiert einen Fehler auf, wenn Sie erstellen ein Kandidat Index-Tag für ein Feld oder eine Kombination von Feldern, die bereits doppelte Werte enthält.  
  
 ADDITIVE  
 Behält alle zuvor geöffneten Indexdateien zu öffnen. Wenn Sie bei der Erstellung einer Index-Dateien für eine Tabelle mit dem INDEX die ADDITIVE-Klausel auslassen, werden alle zuvor geöffneten Indexdateien (mit Ausnahme der strukturellen zusammengesetzter Index) geschlossen.  
  
## <a name="remarks"></a>Hinweise  
 Datensätze in einer Tabelle, der einen Index hat, werden angezeigt und in der Reihenfolge, die dem angegebenen Indexausdruck zugegriffen. Die physische Reihenfolge der Datensätze in der Tabelle ist nicht durch eine Indexdatei geändert.  
  
## <a name="index-types"></a>Typen von Indizes  
 Visual FoxPro können Sie zwei Arten von Indexdateien zu erstellen:  
  
-   Zusammengesetzte CDX-Indexdateien, die mehrere Indexeinträge, sogenannten Tags enthält.  
  
-   IDX-Indexdateien, enthält einen Indexeintrag  
  
 Sie können auch eine Datei strukturelle zusammengesetzten Index erstellen, die automatisch, mit der Tabelle geöffnet wird.  
  
> [!NOTE]  
>  Da es sich bei strukturellen zusammengesetzten Indexdateien automatisch geöffnet werden, wenn die Tabelle geöffnet wird, sind sie der bevorzugte Indextyp an.  
  
 Umfassen Sie COMPACT um compact IDX Indexdateien zu erstellen. Zusammengesetzter Indexdateien sind stets compact.  
  
## <a name="index-order-and-updating"></a>Indexreihenfolge und aktualisieren  
 Nur ein Index (die Datei Masterindex) oder ein Tag (der master-Tag) steuert die Reihenfolge, in der in der Tabelle angezeigt werden oder auf die zugegriffen wird. Bestimmte Befehle (z. B. "SEEK") werden die Masterindex-Datei oder das Tag verwenden, um für Datensätze zu suchen. Allerdings alle IDX öffnen und CDX-Indexdateien werden aktualisiert, wenn Änderungen in der Tabelle vorgenommen werden.  
  
## <a name="user-defined-functions"></a>Benutzerdefinierte Funktionen  
 Obwohl ein Indexausdruck eine benutzerdefinierte Funktion enthalten kann, sollten Sie benutzerdefinierte Funktionen nicht in einem Indexausdruck verwenden. Benutzerdefinierte Funktionen in einem Indexausdruck zu einem größeren Zeitaufwand, die zum Erstellen oder aktualisieren den Index benötigt. Darüber hinaus auftreten indexaktualisierungen nicht, wenn eine benutzerdefinierte Funktion für einen Indexausdruck verwendet wird.  
  
 Wenn Sie eine benutzerdefinierte Funktion in einem Indexausdruck verwenden, muss Visual FoxPro finden Sie die benutzerdefinierte Funktion sein. Wenn Visual FoxPro einen Index erstellt, der Indexausdruck wird in der Indexdatei gespeichert, aber nur ein Verweis auf die benutzerdefinierte Funktion im Indexausdruck enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER TABLE - SQL-Befehl](../../odbc/microsoft/alter-table-sql-command.md)   
 [Befehl DELETE TAG](../../odbc/microsoft/delete-tag-command.md)   
 [Befehl SET COLLATE](../../odbc/microsoft/set-collate-command.md)   
 [Befehl SET UNIQUE](../../odbc/microsoft/set-unique-command.md)
