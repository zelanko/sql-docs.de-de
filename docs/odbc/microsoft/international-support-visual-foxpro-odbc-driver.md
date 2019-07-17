---
title: Internationale Unterstützung (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e987c224f2d716fcab3bf898b1cb276e922e48ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085504"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Internationale Unterstützung (Visual FoxPro-ODBC-Treiber)
Der Microsoft Visual FoxPro-ODBC-Treiber unterstützt:  
  
-   Doppelbyte-Zeichensätze (DBCS)  
  
-   Mehrere sortierenden Sequenzen  
  
 Eine Sortierreihenfolge definiert die *Sortierreihenfolge* für Daten, die in einer Visual FoxPro-Tabelle oder einer Datenbank gespeichert. Standardmäßig ist der Treiber konfiguriert um die sortierenden Sequenzen zu verwenden, die die Sprachversion des Betriebssystems zu unterstützen.  
  
 Eine Liste der unterstützten sortierenden Sequenzen, finden Sie unter [festgelegt COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>Gebietsschema  
 Der Satz von Informationen, die eine bestimmte Sprache und Land/Region entspricht. Ein Gebietsschema gibt bestimmte Einstellungen wie z. B. Dezimaltrennzeichen, Datums- und Uhrzeitformaten und Reihenfolge sortieren von Zeichen an.  
  
## <a name="sort-order"></a>Sortierreihenfolge  
 Sortierreihenfolgen integrieren die Sortierungsregeln für verschiedene *Gebietsschema*s, sodass Sie zur richtigen Sortierung der Daten in diesen Sprachen. Im Visual FoxPro bestimmt die aktuelle Sortierreihenfolge für die Ergebnisse des Ausdrucks Zeichenvergleiche und die Reihenfolge, in der die Datensätze im angezeigt, sortiert Tabellen oder indizierte.
