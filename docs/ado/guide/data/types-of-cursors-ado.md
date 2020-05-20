---
title: Cursor Typen (ADO) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4953b0509cade52a8badd8d578c9fa13f0c2b42b
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759046"
---
# <a name="types-of-cursors-ado"></a>Cursortypen (ADO)
Als allgemeine Regel sollte Ihre Anwendung den einfachsten Cursor verwenden, der den erforderlichen Datenzugriff bereitstellt. Jedes zusätzliche Cursor Merkmal, das über die Grundlagen hinausgeht (vorwärts, schreibgeschützt, statisch, scrollen, nicht gepuffert), verfügt über einen Preis in Client Arbeitsspeicher, Netzwerk Auslastung oder Leistung. In vielen Fällen generieren die Standard Cursor Optionen einen komplexeren Cursor als die Anwendung tatsächlich benötigt.  
  
 Die Auswahl des Cursortyps hängt davon ab, wie die Anwendung das Resultset verwendet, und auch nach verschiedenen Entwurfs Überlegungen, einschließlich der Größe des Resultsets, dem Prozentsatz der Daten, die wahrscheinlich verwendet werden, der Vertraulichkeit von Datenänderungen und den Anwendungs Leistungsanforderungen.  
  
 Am grundlegendsten hängt die Cursor Auswahl davon ab, ob Sie die Daten ändern oder einfach anzeigen müssen:  
  
-   Wenn Sie nur einen Bildlauf durch einen Resultset ausführen, aber keine Daten ändern müssen, verwenden Sie einen [Vorwärts](../../../ado/guide/data/forward-only-cursors.md) Cursor oder einen [statischen](../../../ado/guide/data/static-cursors.md) Cursor.  
  
-   Wenn Sie ein großes Resultset haben und nur einige Zeilen auswählen müssen, verwenden Sie einen [Keysetcursor](../../../ado/guide/data/keyset-cursors.md) .  
  
-   Wenn Sie ein Resultset mit den aktuellen Ergänzungen, Änderungen und Löschungen von allen gleichzeitigen Benutzern synchronisieren möchten, verwenden Sie einen [dynamischen](../../../ado/guide/data/dynamic-cursors.md) Cursor.  
  
 Obwohl jeder Cursortyp eindeutig zu sein scheint, sollten Sie Bedenken, dass diese Cursor Typen nicht so viele verschiedene Variationen sind wie das Ergebnis von überlappenden Merkmalen und Optionen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Vorwärtscursor](../../../ado/guide/data/forward-only-cursors.md)  
  
-   [Statische Cursor](../../../ado/guide/data/static-cursors.md)  
  
-   [KEYSET-Cursor](../../../ado/guide/data/keyset-cursors.md)  
  
-   [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorwärts Cursor](../../../ado/guide/data/forward-only-cursors.md)   
 [Statische Cursor](../../../ado/guide/data/static-cursors.md)   
 [Keysetcursor](../../../ado/guide/data/keyset-cursors.md)   
 [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)
