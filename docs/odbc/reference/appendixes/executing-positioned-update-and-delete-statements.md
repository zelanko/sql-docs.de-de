---
title: Ausführen positionierter Update-und DELETE-Anweisungen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307001"
---
# <a name="executing-positioned-update-and-delete-statements"></a>Ausführen einer positionierten Aktualisierung und von DELETE-Anweisungen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Nachdem eine Anwendung einen Datenblock mit **SQLFetchScroll**abgerufen hat, kann Sie die Daten im-Block aktualisieren oder löschen. Um ein positioniertes Update oder DELETE auszuführen, führt die Anwendung Folgendes aus:  
  
1.  Ruft **SQLSetPos** auf, um den Cursor in der Zeile zu positionieren, die aktualisiert oder gelöscht werden soll.  
  
2.  Erstellt eine positionierte UPDATE-oder DELETE-Anweisung mit der folgenden Syntax:  
  
     **UPDATE** *Tabellennamen* aktualisieren  
  
     **Festlegen** des *Spalten Bezeichners* **=** {*Expression* &#124; **null**}  
  
     [**,** *Spalten Bezeichner* **=** {*Expression* &#124; **null**}]  
  
     **WHERE CURRENT of** *Cursor-Name*  
  
     **Aus** *Tabellenname* löschen, **wobei Current of** *Cursor Name*  
  
     Die einfachste Möglichkeit zum Erstellen der **Set** -Klausel in einer positionierten Update-Anweisung besteht darin, Parameter Markierungen für jede zu Aktualisier Ende Spalte zu verwenden und **SQLBindParameter** zu verwenden, um diese an die rowsetpuffer für die zu Aktualisier Ende Zeile zu binden. In diesem Fall ist der c-Datentyp des Parameters mit dem c-Datentyp des rowsetpuffers identisch.  
  
3.  Aktualisiert die rowsetpuffer für die aktuelle Zeile, wenn eine positionierte UPDATE-Anweisung ausgeführt wird. Nachdem eine positionierte UPDATE-Anweisung erfolgreich ausgeführt wurde, kopiert die Cursor Bibliothek die Werte aus jeder Spalte in der aktuellen Zeile in Ihren Cache.  
  
    > [!CAUTION]  
    >  Wenn die Anwendung die rowsetpuffer nicht ordnungsgemäß aktualisiert, bevor eine positionierte UPDATE-Anweisung ausgeführt wird, sind die Daten im Cache nach der Ausführung der Anweisung falsch.  
  
4.  Führt die positionierte UPDATE-oder DELETE-Anweisung mit einer anderen-Anweisung als der dem Cursor zugeordneten-Anweisung aus.  
  
    > [!CAUTION]  
    >  Die **Where** -Klausel, die von der Cursor Bibliothek zum Identifizieren der aktuellen Zeile erstellt wurde, kann keine Zeilen identifizieren, eine andere Zeile identifizieren oder mehr als eine Zeile identifizieren. Weitere Informationen finden Sie unter [Erstellen von durchsuchten Anweisungen](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Alle positionierten Update-und DELETE-Anweisungen erfordern einen Cursor Namen. Zum Angeben des Cursor namens Ruft eine Anwendung **SQLSetCursorName** auf, bevor der Cursor geöffnet wird. Um den vom Treiber generierten Cursor Namen zu verwenden, ruft eine Anwendung **SQLGetCursorName** auf, nachdem der Cursor geöffnet wurde.  
  
 Nachdem die Cursor Bibliothek eine positionierte UPDATE-oder DELETE-Anweisung ausgeführt hat, enthalten das Status Array, die rowsetpuffer und der Cache, die von der Cursor Bibliothek verwaltet werden, die in der folgenden Tabelle aufgeführten Werte.  
  
|Verwendete Anweisung|Wert im Zeilen Status Array|Werte in<br /><br /> rowsetpuffer|Werte in<br /><br /> Cache Puffer|  
|--------------------|-------------------------------|----------------------------------|---------------------------------|  
|Positioniertes Update|SQL_ROW_UPDATED|Neue Werte [1]|Neue Werte [1]|  
|Positionierter Löschvorgang|SQL_ROW_DELETED|Alte Werte|Alte Werte|  
  
 [1] die Anwendung muss die Werte in den rowsetpuffern aktualisieren, bevor die positionierte UPDATE-Anweisung ausgeführt wird. nach dem Ausführen der positionierten Update-Anweisung kopiert die Cursor Bibliothek die Werte in den rowsetpuffern in Ihren Cache.
