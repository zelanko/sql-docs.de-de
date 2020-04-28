---
title: Statische Cursor | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924120"
---
# <a name="static-cursors"></a>Statische Cursor
Der statische Cursor zeigt das Resultset immer so an, wie es beim ersten Öffnen des Cursors war. Abhängig von der Implementierung sind statische Cursor entweder schreibgeschützt oder Lese-/Schreibzugriff und bieten vorwärts und rückwärts Bildlauf. Der statische Cursor erkennt in der Regel keine Änderungen an der Mitgliedschaft, Reihenfolge oder den Werten des Resultsets, nachdem der Cursor geöffnet wurde. Statische Cursor können ihre eigenen UPDATE-, DELETE- und INSERT-Anweisungen erkennen, obwohl dies nicht erforderlich ist.  
  
 Statische Cursor erkennen nie andere Updates, Löschungen und Einfügungen. Angenommen ein statischer Cursor ruft eine Zeile ab, und eine andere Anwendung aktualisiert diese Zeile dann. Wenn die Anwendung die Zeile erneut vom statischen Cursor abruft, sind die erkannten Werte unverändert, obwohl die andere Anwendung Änderungen vorgenommen hat. Alle scrolltypen werden unterstützt, aber die Anbieter unterstützen Lesezeichen möglicherweise nicht.  
  
 Wenn Ihre Anwendung keine Datenänderungen erkennen muss und einen Bildlauf erfordert, ist der statische Cursor die beste Wahl. Verwenden Sie die " **adopconstatic cursortypeumum** ", um anzugeben, dass Sie einen statischen Cursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorwärts Cursor](../../../ado/guide/data/forward-only-cursors.md)   
 [Keysetcursor](../../../ado/guide/data/keyset-cursors.md)   
 [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)
