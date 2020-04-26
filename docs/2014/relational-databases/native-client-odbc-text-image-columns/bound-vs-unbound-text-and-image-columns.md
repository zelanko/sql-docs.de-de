---
title: Gebundene und ungebundene Text-und image-Spalten | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62626583"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Vergleich von gebundenen und ungebundenen Text- und Image-Spalten
  Bei der Verwendung von Server Cursorn wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Native Client-ODBC-Treiber so optimiert, dass die Daten für ungebundene **Text**-, **ntext**-oder **Image** -Spalten zum Zeitpunkt der Ausführung von **SQLFetch** nicht übertragen werden. Die **Text**-, **ntext**-oder **Image** -Daten werden erst dann vom Server abgerufen, wenn die Anwendung [SQLGetData](../native-client-odbc-api/sqlgetdata.md) für die Spalte ausgibt.  
  
 Viele Anwendungen können so geschrieben werden, dass keine Text-, **ntext**-oder **Image** -Daten angezeigt werden, während ein Benutzer einfach einen **Bildlauf**nach oben und unten in einem Cursor durchführt. Wenn ein Benutzer eine Zeile auswählt, um weitere Details zu erhalten, kann die Anwendung **SQLGetData** aufrufen, um die **Text**-, **ntext**-oder **Image** -Daten abzurufen. Dadurch wird verhindert, dass die **Text**-, **ntext**-oder **Image** -Daten für eine der Zeilen übertragen werden, die der Benutzer nicht ausgewählt hat, und daher kann die Übertragung sehr großer Datenmengen verhindert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Text-und image-Spalten](managing-text-and-image-columns.md)   
 [Cursorverhalten](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  
