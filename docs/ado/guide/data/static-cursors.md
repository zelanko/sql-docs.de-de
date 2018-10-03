---
title: Static-Cursor | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8815522ee4f9a4221887696a23a201910d7cfad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654188"
---
# <a name="static-cursors"></a>Statische Cursor
Der statische Cursor zeigt das Resultset, wie sie beim ersten Öffnen des Cursors wurde. Statische Cursor sind je nach Implementierung, entweder schreibgeschützt oder Lese-/Schreibzugriff und bieten Bildlauf vorwärts und rückwärts. Der statische Cursor erkennt in der Regel keine Änderungen an der Mitgliedschaft, Reihenfolge oder Werte im Resultset nach der der Cursor geöffnet wird. Statische Cursor erkennt möglicherweise eigene Updates, löschungen und einfügungen, obwohl sie nicht dazu erforderlich sind.  
  
 Statische Cursor erkennen nie anderen updates, Lösch- und Einfügevorgänge. Nehmen wir beispielsweise an ein statischer Cursor abruft, einer Zeile und eine andere Anwendung wird diese Zeile aktualisiert. Wenn die Anwendung die Zeile aus der statische Cursor refetches, sind die Werte, die es erkennt unverändert, obwohl die von der anderen Anwendung vorgenommenen Änderungen. Alle Typen von Durchführen eines Bildlaufs unterstützt, aber der Anbieter möglicherweise oder unterstützen möglicherweise keine Lesezeichen.  
  
 Wenn Ihre Anwendung keine Daten geändert werden und erfordert einen Bildlauf zu erkennen muss, ist der statische Cursor die beste Wahl. Verwenden Sie die **"adOpenStatic" CursorTypeEnum** , um anzugeben, dass Sie einen statischen Cursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorwärtscursor](../../../ado/guide/data/forward-only-cursors.md)   
 [KEYSET-Cursor](../../../ado/guide/data/keyset-cursors.md)   
 [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)
