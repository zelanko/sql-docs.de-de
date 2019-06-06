---
title: Cursortypen (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], types
ms.assetid: 7cc01544-e814-403b-bbfe-a2750bf921bd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 717229c9645384477b89e67b569c15179e9f3bc5
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704908"
---
# <a name="types-of-cursors-ado"></a>Cursortypen (ADO)
Als allgemeine Regel sollte Ihre Anwendung den einfachsten Cursor verwenden, der den Zugriff erforderlichen Daten bereitstellt. Jedes Merkmal zusätzliche Cursor über die Grundlagen (Vorwärtscursor, schreibgeschützte, statische, scrollen, ungepufferte) hat es sich um einen Preis – in den Clientspeicher, Netzwerkauslastung oder Leistung. In vielen Fällen generiert die Standardcursoroptionen einen komplexeren Cursor als die Anwendung tatsächlich benötigt.  
  
 Ihrer Wahl des Cursortyps hängt wie das Resultset von der Anwendung verwendet und auch auf mehrere entwurfsüberlegungen, einschließlich der Größe der das Resultset auf, der Prozentsatz der Daten wahrscheinlich verwendet werden, die Sensitivität gegenüber datenänderungen und Leistung der Anwendung ab. Anforderungen an.  
  
 Cursorauswahl hängt in seiner einfachsten gibt an, ob Sie ändern oder einfach nur die Daten anzeigen möchten:  
  
-   Wenn Sie nur einen Bildlauf durch einen Satz von Ergebnissen, jedoch keine Änderungsdaten müssen, verwenden Sie eine [Vorwärtscursor](../../../ado/guide/data/forward-only-cursors.md) oder [statische](../../../ado/guide/data/static-cursors.md) Cursor.  
  
-   Wenn Sie ein großes Resultset und müssen nur wenige Zeilen ausgewählt haben, verwenden Sie eine [Keyset](../../../ado/guide/data/keyset-cursors.md) Cursor.  
  
-   Wenn Sie synchronisieren möchten ein Resultset mit aktuellen hinzufügt, ändert und löscht alle gleichzeitigen Benutzer, verwenden Sie eine [dynamische](../../../ado/guide/data/dynamic-cursors.md) Cursor.  
  
 Obwohl alle Cursortypen unterscheiden, sollten Sie bedenken, dass diese Cursortypen nicht so viel verschiedenen Varianten wie einfach das Ergebnis von überlappenden und Optionen sind.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Vorwärtscursor](../../../ado/guide/data/forward-only-cursors.md)  
  
-   [Statische Cursor](../../../ado/guide/data/static-cursors.md)  
  
-   [KEYSET-Cursor](../../../ado/guide/data/keyset-cursors.md)  
  
-   [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Vorwärtscursor](../../../ado/guide/data/forward-only-cursors.md)   
 [Statische Cursor](../../../ado/guide/data/static-cursors.md)   
 [KEYSET-Cursor](../../../ado/guide/data/keyset-cursors.md)   
 [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)
