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
ms.openlocfilehash: 520c484bdaaa6eb59488900208993a607c5b0f7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924120"
---
# <a name="static-cursors"></a>Statische Cursor
Der statische Cursor zeigt das Resultset, wie sie beim ersten Öffnen des Cursors wurde. Statische Cursor sind je nach Implementierung, entweder schreibgeschützt oder Lese-/Schreibzugriff und bieten Bildlauf vorwärts und rückwärts. Der statische Cursor erkennt in der Regel keine Änderungen an der Mitgliedschaft, Reihenfolge oder Werte im Resultset nach der der Cursor geöffnet wird. Statische Cursor können ihre eigenen UPDATE-, DELETE- und INSERT-Anweisungen erkennen, obwohl dies nicht erforderlich ist.  
  
 Statische Cursor erkennen nie anderen updates, Lösch- und Einfügevorgänge. Angenommen ein statischer Cursor ruft eine Zeile ab, und eine andere Anwendung aktualisiert diese Zeile dann. Wenn die Anwendung die Zeile erneut vom statischen Cursor abruft, sind die erkannten Werte unverändert, obwohl die andere Anwendung Änderungen vorgenommen hat. Alle Typen von Durchführen eines Bildlaufs unterstützt, aber der Anbieter möglicherweise oder unterstützen möglicherweise keine Lesezeichen.  
  
 Wenn Ihre Anwendung keine Daten geändert werden und erfordert einen Bildlauf zu erkennen muss, ist der statische Cursor die beste Wahl. Verwenden Sie die **"adOpenStatic" CursorTypeEnum** , um anzugeben, dass Sie einen statischen Cursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorwärtscursor](../../../ado/guide/data/forward-only-cursors.md)   
 [KEYSET-Cursor](../../../ado/guide/data/keyset-cursors.md)   
 [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)
