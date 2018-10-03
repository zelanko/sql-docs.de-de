---
title: Vergleich von gebundenen und Ungebundenen Text- und Image-Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1bf8ac0cf868394d9aa8063220939feee69ac2f6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108260"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Vergleich von gebundenen und ungebundenen Text- und Image-Spalten
  Wenn Servercursor verwendet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber wurde optimiert, um überträgt keine Daten für ungebundene **Text**, **Ntext**, oder **Image** Spalten in der Zeit **SQLFetch** erfolgt. Die **Text**, **Ntext**, oder **Image** Daten werden erst die Anwendungsprobleme nicht tatsächlich vom Server abgerufen [SQLGetData](../native-client-odbc-api/sqlgetdata.md) für die die Spalte.  
  
 Viele Anwendungen können geschrieben werden, damit keine **Text**, **Ntext**, oder **Image** Daten werden angezeigt, während ein Benutzer einfach nach oben oder unten in einem Cursor einen Bildlauf ist. Wenn ein Benutzer eine Zeile aus, um weitere Informationen zu erhalten auswählt, wird die Anwendung kann dann aufrufen **SQLGetData** zum Abrufen der **Text**, **Ntext**, oder **Image** Daten. Dadurch wird verhindert, übertragen die **Text**, **Ntext**, oder **Image** Daten aus der Zeilen, die der Benutzer nicht auswählen, und kann daher zu verhindern, dass die Übertragung von sehr großen die Mengen von Daten.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Text- und Image-Spalten](managing-text-and-image-columns.md)   
 [Cursorverhalten](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  
