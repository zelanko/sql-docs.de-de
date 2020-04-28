---
title: Internationaler Support (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4b0c758bb478ea6a468e6756c3d6f0f52c766f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299970"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Internationale Unterstützung (Visual FoxPro-ODBC-Treiber)
Der Microsoft Visual FoxPro-ODBC-Treiber unterstützt Folgendes:  
  
-   Doppelbyte-Zeichensätze (DBCS)  
  
-   Mehrere Sortier Sequenzen  
  
 Eine Sortierreihenfolge definiert die *Sortierreihenfolge* für Daten, die in einer Visual FoxPro-Tabelle oder-Datenbank gespeichert sind. Standardmäßig ist der Treiber für die Verwendung der Sortier Sequenzen konfiguriert, die die Sprachversion Ihres Betriebssystems unterstützen.  
  
 Eine Liste der unterstützten Sortierungs Sequenzen finden Sie unter [SET COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>locale  
 Der Satz von Informationen, der einer bestimmten Sprache und einem bestimmten Land/einer bestimmten Region entspricht. Ein Gebiets Schema gibt bestimmte Einstellungen an, z. b. Dezimaltrennzeichen, Datums-und Uhrzeit Formate und Zeichen Sortierreihenfolge.  
  
## <a name="sort-order"></a>Sortierreihenfolge  
 Sortier Reihenfolgen enthalten die Sortierungsregeln *für verschiedene Gebiets*Schemas, sodass Sie die Daten in diesen Sprachen richtig sortieren können. In Visual FoxPro bestimmt die aktuelle Sortierreihenfolge die Ergebnisse von Zeichen Ausdrucks vergleichen und die Reihenfolge, in der die Datensätze in indizierten oder sortierten Tabellen angezeigt werden.
