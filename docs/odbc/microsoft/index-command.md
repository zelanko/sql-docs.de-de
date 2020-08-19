---
description: INDEX-Befehl
title: Index Befehl | Microsoft-Dokumentation
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
ms.openlocfilehash: ec9ed3c0ec0e91f3c4fd3a0019c8ac463a8620c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449522"
---
# <a name="index-command"></a>INDEX-Befehl
Erstellt eine Indexdatei zum Anzeigen und Zugreifen auf Tabellendaten Sätze in einer logischen Reihenfolge.  
  
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
 *eexpression*  
 Gibt einen Index Ausdruck an, der den Namen eines Felds oder der Felder aus der aktuellen Tabelle enthalten kann. Ein Index Schlüssel, der auf dem Index Ausdruck basiert, wird in der Indexdatei für jeden Datensatz in der Tabelle erstellt. Visual FoxPro verwendet diese Schlüssel, um Datensätze in der Tabelle anzuzeigen und darauf zuzugreifen.  
  
> [!NOTE]  
>  Obwohl es nicht empfohlen wird, kann *eexpression* auch eine Speicher Variable, ein Array Element oder ein Feld-oder Feld Ausdruck aus einer Tabelle in einem anderen Arbeitsbereich sein. Memo Felder können nicht allein in Indexdatei Ausdrücken verwendet werden. Sie müssen mit anderen Zeichen Ausdrücken kombiniert werden. Wenn Sie auf einen Index zugreifen, der eine Variable oder ein Feld enthält, das nicht mehr vorhanden ist oder nicht gefunden werden kann, generiert Visual FoxPro eine Fehlermeldung.  
  
 Wenn Sie versuchen, einen Index mit einem Schlüssel zu erstellen, der die Länge unterscheidet, wird der Schlüssel mit Leerzeichen aufgefüllt. Index Schlüssel mit variabler Länge werden in Visual FoxPro nicht unterstützt.  
  
 Es ist möglich, einen Index Schlüssel mit der Länge 0 (null) zu erstellen. Beispielsweise wird ein Index Schlüssel der Länge 0 (null) erstellt, wenn der Index Ausdruck eine Teil Zeichenfolge eines leeren Memo Felds ist. Ein Index Schlüssel mit der Länge Null generiert eine Fehlermeldung. Wenn Visual FoxPro einen Index erstellt, wertet er Felder im ersten Datensatz in der Tabelle aus. Wenn ein Feld leer ist, kann es erforderlich sein, einige temporäre Daten im Feld im ersten Datensatz einzugeben, um einen Index Schlüssel mit der Länge 0 (null) zu verhindern.  
  
 An *idxfilename*  
 Erstellt eine IDX-Indexdatei. Der Indexdatei wird die standardmäßige Erweiterung. idx zugewiesen.  
  
 *Tagname*des Tags [von *cdxfilename*]  
 Erstellt eine Verbund Indexdatei. Eine Verbund Indexdatei ist eine einzelne Indexdatei, die aus einer beliebigen Anzahl von separaten Tags (Indexeinträge) besteht. Jedes Tag wird anhand seines eindeutigen Tagnamens identifiziert. Tagnamen müssen mit einem Buchstaben oder einem Unterstrich beginnen und können aus einer beliebigen Kombination von bis zu 10 Buchstaben, Ziffern oder Unterstrichen bestehen. Die Anzahl der Tags in einer Verbund Indexdatei wird nur durch den verfügbaren Arbeitsspeicher und Speicherplatz beschränkt.  
  
 Zusammengesetzte Indexdateien mit mehreren Eintrags sind immer kompakt. Beim Erstellen einer Verbund Indexdatei ist das Einschließen von Compact nicht erforderlich. Namen von Verbund Indexdateien erhalten die Erweiterung ". CDX".  
  
 Es können zwei Typen von Verbund Indexdateien erstellt werden: strukturell und nicht strukturell.  
  
 **Struktur zusammengesetzter Index Dateien** Sie können eine Struktur zusammengesetzte Indexdatei mit *Tagname Tagname* erstellen, indem Sie die optionale der *cdxfilename* -Klausel ausschließen. Eine Struktur zusammengesetzter Indexdatei hat immer denselben Basis Namen wie die Tabelle und wird automatisch geöffnet, wenn die Tabelle geöffnet wird.  
  
 **Nicht strukturelle Verbund Index Dateien** Sie können eine nicht strukturelle Verbund Indexdatei erstellen, indem Sie *cdxfilename* nach *Tagname*des Tags einschließen. Anders als bei einer strukturellen Verbund Indexdatei muss eine nicht strukturell zusammengesetzte Indexdatei explizit mit der verwendeten Index Klausel geöffnet werden.  
  
 Wenn bereits eine Verbund Indexdatei erstellt und geöffnet wurde, wird bei der Ausgabe von Index mit *Tagname* des Tags der Verbund Indexdatei ein Tag hinzugefügt.  
  
 Für *lExpression*  
 Gibt eine Bedingung an, bei der nur Datensätze, die den Filter Ausdruck " *lExpression* " erfüllen, für Anzeige und Zugriff verfügbar sind. Index Schlüssel werden in der Indexdatei nur für die Datensätze erstellt, die mit dem Filter Ausdruck übereinstimmen.  
  
 Visual FoxPro-Rushmore-Technologie optimiert einen Index... Für den *lExpression* -Befehl, wenn *lExpression* ein optimierbarer Ausdruck ist. Verwenden Sie für eine optimale Leistung einen optimier baren Ausdruck in der for-Klausel.  
  
 Theit  
 Erstellt eine Compact. idx-Datei.  
  
 Steigung  
 Gibt eine aufsteigende Reihenfolge für die CDX-Datei an. Standardmäßig werden CDX-Tags in aufsteigender Reihenfolge erstellt. (Sie können aufsteigend als Erinnerung an die Reihenfolge der Indexdateien einschließen.) Eine Tabelle kann in umgekehrter Reihenfolge indiziert werden, indem Sie absteigend einschließt.  
  
 Steig  
 Gibt eine absteigende Reihenfolge für die CDX-Datei an. Beim Erstellen von IDX-Indexdateien kann absteigend nicht eingeschlossen werden.  
  
 UNIQUE  
 Gibt an, dass nur der erste Datensatz mit einem bestimmten Index Schlüsselwert in einer IDX-Datei oder einem CDX-Tag enthalten ist. Unique kann verwendet werden, um die Anzeige von oder den Zugriff auf doppelte Datensätze zu verhindern. Alle Datensätze, die mit doppelten Index Schlüsseln hinzugefügt wurden, werden aus der Indexdatei ausgeschlossen. Die Verwendung der UNIQUE-Option des Indexes ist identisch mit der Ausführung von Set Unique für vor der Ausgabe von Index oder REINDEX.  
  
 Wenn ein eindeutiger Index oder Indextag aktiv ist und ein doppelter Datensatz auf eine Weise geändert wird, in der der Index Schlüssel geändert wird, wird der Index oder das Indextag aktualisiert. Der nächste doppelte Datensatz mit dem ursprünglichen Index Schlüssel kann jedoch erst aufgerufen oder angezeigt werden, wenn Sie die Datei mithilfe von REINDEX neu indizieren.  
  
 Anwärter  
 Erstellt ein strukturelles Indextag. Das Candidate-Schlüsselwort kann nur beim Erstellen eines strukturellen Indextags eingeschlossen werden. Andernfalls generiert Visual FoxPro eine Fehlermeldung.  
  
 Ein Kandidaten Indextag verhindert doppelte Werte in dem Feld oder in der Kombination von Feldern, die im *eexpression*-Index Ausdruck angegeben sind. Der Begriff *Candidate* bezieht sich auf den Indextyp. Da Kandidaten Indizes doppelte Werte verhindern, qualifizieren Sie sich als "Kandidat" als primär Index.  
  
 Visual FoxPro generiert einen Fehler, wenn Sie ein Kandidaten Indextag für ein Feld oder eine Kombination von Feldern erstellen, die bereits doppelte Werte enthalten.  
  
 Herstellen  
 Hält alle zuvor geöffneten Indexdateien offen. Wenn Sie die Additive-Klausel weglassen, wenn Sie eine Indexdatei oder Dateien für eine Tabelle mit Index erstellen, werden alle zuvor geöffneten Indexdateien (mit Ausnahme des Struktur Verbund Indexes) geschlossen.  
  
## <a name="remarks"></a>Bemerkungen  
 Datensätze in einer Tabelle mit einer Indexdatei werden angezeigt, und der Zugriff erfolgt in der vom Index Ausdruck angegebenen Reihenfolge. Die physische Reihenfolge der Datensätze in der Tabelle wird nicht durch eine Indexdatei geändert.  
  
## <a name="index-types"></a>Index Typen  
 Mit Visual FoxPro können Sie zwei Typen von Indexdateien erstellen:  
  
-   Zusammengesetzte CDX-Indexdateien, die mehrere Indexeinträge Namens Tags enthalten  
  
-   idx-Indexdateien, die einen Index Eintrag enthalten  
  
 Sie können auch eine Struktur zusammengesetzter Indexdatei erstellen, die automatisch mit der-Tabelle geöffnet wird.  
  
> [!NOTE]  
>  Da strukturelle Verbund Indexdateien beim Öffnen der Tabelle automatisch geöffnet werden, sind Sie der bevorzugte Indextyp.  
  
 Schließen Sie Compact ein, um Compact. idx-Indexdateien zu erstellen. Zusammengesetzte Indexdateien sind immer kompakt.  
  
## <a name="index-order-and-updating"></a>Index Reihenfolge und-Aktualisierung  
 Nur eine Indexdatei (die Master Indexdatei) oder ein Tag (das mastertag) steuert die Reihenfolge, in der die Tabelle angezeigt oder aufgerufen wird. Bestimmte Befehle (z. b. suchen) verwenden die Master Indexdatei oder das Tag, um nach Datensätzen zu suchen. Alle geöffneten IDX-und CDX-Indexdateien werden jedoch aktualisiert, wenn Änderungen an der Tabelle vorgenommen werden.  
  
## <a name="user-defined-functions"></a>Benutzerdefinierte Funktionen  
 Obwohl ein Index Ausdruck eine benutzerdefinierte Funktion enthalten kann, sollten Sie keine benutzerdefinierten Funktionen in einem Index Ausdruck verwenden. Benutzerdefinierte Funktionen in einem Index Ausdruck erhöhen die Zeit, die benötigt wird, um den Index zu erstellen oder zu aktualisieren. Außerdem werden Index Aktualisierungen möglicherweise nicht ausgeführt, wenn eine benutzerdefinierte Funktion für einen Index Ausdruck verwendet wird.  
  
 Wenn Sie eine benutzerdefinierte Funktion in einem Index Ausdruck verwenden, muss Visual FoxPro in der Lage sein, die benutzerdefinierte Funktion zu finden. Wenn Visual FoxPro einen Index erstellt, wird der Index Ausdruck in der Indexdatei gespeichert, aber nur ein Verweis auf die benutzerdefinierte Funktion ist im Index Ausdruck enthalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER TABLE-SQL-Befehl](../../odbc/microsoft/alter-table-sql-command.md)   
 [Befehl zum Löschen von Tags](../../odbc/microsoft/delete-tag-command.md)   
 [Befehl "COLLATE festlegen"](../../odbc/microsoft/set-collate-command.md)   
 [Befehl SET UNIQUE](../../odbc/microsoft/set-unique-command.md)
