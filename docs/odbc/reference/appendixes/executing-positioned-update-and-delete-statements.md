---
title: Ausführen von Update- und Delete-Anweisungen positioniert | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2391c01d93c876562ab9d870ab0dba22bf74cea5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772048"
---
# <a name="executing-positioned-update-and-delete-statements"></a>Ausführen einer positionierten Aktualisierung und von DELETE-Anweisungen
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Nachdem eine Anwendung einen Block von Daten mit abgerufen hat **SQLFetchScroll**, diese später aktualisieren oder löschen Sie die Daten im-Block. Zum Ausführen eines positionierten Updates oder löschen, die Anwendung:  
  
1.  Aufrufe **SQLSetPos** , positionieren Sie den Cursor in der Zeile, die aktualisiert oder gelöscht werden.  
  
2.  Erstellt ein positioniertes Update oder Delete-Anweisung mit der folgenden Syntax:  
  
     **UPDATE** *Tabellenname*  
  
     **Legen Sie** *Spaltenbezeichner* **=** {*Ausdruck* &#124; **NULL**}  
  
     [**,** *Spaltenbezeichner* **=** {*Ausdruck* &#124; **NULL**}]  
  
     **WHERE CURRENT OF** *Cursorname*  
  
     **DELETE FROM** *Tabellenname* **WHERE CURRENT OF** *Cursorname*  
  
     Die einfachste Möglichkeit zum Erstellen der **festgelegt** Klausel in einer positioniertes Update-Anweisung ist die Verwendung von parametermarkierungen für jede Spalte aktualisiert werden, und verwenden **SQLBindParameter** binden diese an die Rowset-Puffer für die die Zeile aktualisiert werden. In diesem Fall werden die C-Datentyp des Parameters identisch mit der C-Datentyp, der der Rowset-Puffer.  
  
3.  Die Rowset-Puffer für die aktuelle Zeile aktualisiert, wenn es eine positioniertes Update-Anweisung ausgeführt wird. Nach der erfolgreichen Ausführung eine positionierte Update-Anweisung, kopiert die Cursorbibliothek die Werte aus den einzelnen Spalten in der aktuellen Zeile aus, dem Cache.  
  
    > [!CAUTION]  
    >  Wenn die Anwendung nicht ordnungsgemäß die Rowset-Puffer aktualisiert wird vor der Ausführung einer positioniertes Update-Anweisung, sind die Daten im Cache fehlerhaft, nachdem die Anweisung ausgeführt wird.  
  
4.  Führt die positioniertes Update oder Delete-Anweisung, die mit einer anderen Anweisung als die Anweisung, die dem Cursor zugeordnet.  
  
    > [!CAUTION]  
    >  Die **, in denen** Klausel erstellt, die von der Cursorbibliothek zum Identifizieren der aktuellen Zeile kann möglicherweise keine Zeilen zu identifizieren, identifizieren eine andere Zeile oder mehr als eine Zeile zu identifizieren. Weitere Informationen finden Sie unter [durchsucht-Anweisungen konstruieren](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Alle positioniert Update und Delete-Anweisungen erfordern ein Cursorname. Um den Cursornamen angeben, die eine Anwendung ruft **SQLSetCursorName** , bevor der Cursor geöffnet wird. Um den Cursornamen, die vom Treiber generierten zu verwenden, eine Anwendung ruft **SQLGetCursorName** nach der der Cursor geöffnet wird.  
  
 Nach dem Cursor-Bibliothek führt ein positioniertes Update oder Delete-Anweisung, die Statusarray, Rowset-Puffer und Beibehalten von der Cursorbibliothek-Cache enthalten in der folgenden Tabelle aufgelisteten Werte.  
  
|-Anweisung verwendet|Wert in zeilenstatusarray|Werte in<br /><br /> Rowset-Puffer|Werte in<br /><br /> Cache-Puffer|  
|--------------------|-------------------------------|----------------------------------|---------------------------------|  
|Positioniertes Update|SQL_ROW_UPDATED|Neue Werte [1]|Neue Werte [1]|  
|Positionierte delete|SQL_ROW_DELETED|Alte Werte|Alte Werte|  
  
 [1] die Anwendung muss die Werte in den Puffern Rowset aktualisieren, bevor die positionierte Update-Anweisung ausgeführt; nach dem Ausführen der positionierte Update-Anweisung, kopiert die Cursorbibliothek die Werte in den Puffern Rowset aus, dem Cache.
