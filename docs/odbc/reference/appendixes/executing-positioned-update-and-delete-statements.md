---
title: Ausführen von positionierten Aktualisierungs- und Löschanweisungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- cursor library [ODBC], positioned update or delete
- positioned updates [ODBC]
- ODBC cursor library [ODBC], positioned update or delete
ms.assetid: 1d64f309-2a6e-4ad1-a6b5-e81145549c56
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96a1aa891ef8ba26c6c239cf35e62a8f36018e65
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307001"
---
# <a name="executing-positioned-update-and-delete-statements"></a>Ausführen einer positionierten Aktualisierung und von DELETE-Anweisungen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Nachdem eine Anwendung einen Datenblock mit **SQLFetchScroll**abgerufen hat, kann sie die Daten im Block aktualisieren oder löschen. Um eine positionierte Aktualisierung oder Löschung auszuführen, wird die Anwendung:  
  
1.  Ruft **SQLSetPos** auf, um den Cursor in der zu aktualisierenden oder zu löschenden Zeile zu positionieren.  
  
2.  Erstellt eine positionierte Aktualisierungs- oder Löschanweisung mit der folgenden Syntax:  
  
     **UPDATE** *UPDATE-Tabellenname*  
  
     **SET** SET-Spaltenbezeichner *column-identifier* **=** -*Ausdruck* &#124; **NULL**  
  
     [ , **=** **,** *Spaltenbezeichner* -*Ausdruck* &#124; **NULL**]  
  
     **WO STROM VON** *Cursor-NAME*  
  
     **AUS** *TABELLENNAME* **LÖSCHEN, WOBEI DER AKTUELLE** *CURSORNAME*  
  
     Die einfachste Möglichkeit, die **SET-Klausel** in einer positionierten Update-Anweisung zu erstellen, besteht darin, Parametermarkierungen für jede zu aktualisierende Spalte zu verwenden und **SQLBindParameter** zu verwenden, um diese an die Rowsetpuffer für die zu aktualisierende Zeile zu binden. In diesem Fall entspricht der C-Datentyp des Parameters dem C-Datentyp des Rowsetpuffers.  
  
3.  Aktualisiert die Rowsetpuffer für die aktuelle Zeile, wenn eine positionierte Aktualisierungsanweisung ausgeführt wird. Nach erfolgreicher Ausführung einer positionierten Updateanweisung kopiert die Cursorbibliothek die Werte aus jeder Spalte in der aktuellen Zeile in ihren Cache.  
  
    > [!CAUTION]  
    >  Wenn die Anwendung die Rowsetpuffer vor dem Ausführen einer positionierten Aktualisierungsanweisung nicht ordnungsgemäß aktualisiert, sind die Daten im Cache nach der Ausführung der Anweisung falsch.  
  
4.  Führt die positionierte Aktualisierungs- oder Löschanweisung mit einer anderen Anweisung als der dem Cursor zugeordneten Anweisung aus.  
  
    > [!CAUTION]  
    >  Die **WHERE** WHERE-Klausel, die von der Cursorbibliothek erstellt wurde, um die aktuelle Zeile zu identifizieren, kann keine Zeilen identifizieren, eine andere Zeile identifizieren oder mehr als eine Zeile identifizieren. Weitere Informationen finden Sie unter [Erstellen von durchsuchten Anweisungen](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Alle positionierten Aktualisierungs- und Löschanweisungen erfordern einen Cursornamen. Um den Cursornamen anzugeben, ruft eine Anwendung **SQLSetCursorName auf,** bevor der Cursor geöffnet wird. Um den vom Treiber generierten Cursornamen zu verwenden, ruft eine Anwendung **SQLGetCursorName** auf, nachdem der Cursor geöffnet wurde.  
  
 Nachdem die Cursorbibliothek eine positionierte Aktualisierungs- oder Löschanweisung ausgeführt hat, enthalten das Statusarray, die Rowset-Puffer und der Cache, der von der Cursorbibliothek verwaltet wird, die in der folgenden Tabelle angezeigten Werte.  
  
|Verwendete Anweisung|Wert im Zeilenstatusarray|Werte in<br /><br /> Rowset-Puffer|Werte in<br /><br /> Cache-Puffer|  
|--------------------|-------------------------------|----------------------------------|---------------------------------|  
|Positioniertes Update|SQL_ROW_UPDATED|Neue Werte[1]|Neue Werte[1]|  
|Positioniertes Löschen|SQL_ROW_DELETED|Alte Werte|Alte Werte|  
  
 [1] Die Anwendung muss die Werte in den Rowset-Puffern aktualisieren, bevor die positionierte Update-Anweisung ausgeführt wird. Nach dem Ausführen der positionierten Update-Anweisung kopiert die Cursorbibliothek die Werte in den Rowset-Puffern in ihren Cache.
