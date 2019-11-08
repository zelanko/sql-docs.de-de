---
title: Gebundene und ungebundene Text-und image-Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d23b999c40aaa6a7cd8200185f18f14ac759403f
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73778872"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Gebundene im Vergleich zu ungebundenen Text- und Image-Spalten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bei der Verwendung von Server Cursorn wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber so optimiert, dass die Daten für ungebundene **Text**-, **ntext**-oder **Image** -Spalten zum Zeitpunkt der Ausführung von **SQLFetch** nicht übertragen werden. Die **Text**-, **ntext**-oder **Image** -Daten werden erst dann vom Server abgerufen, wenn die Anwendung [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) für die Spalte ausgibt.  
  
 Viele Anwendungen können so geschrieben werden, dass keine Text-, **ntext**-oder **Image** -Daten angezeigt werden, während ein Benutzer einfach einen **Bildlauf**nach oben und unten in einem Cursor durchführt. Wenn ein Benutzer eine Zeile auswählt, um weitere Details zu erhalten, kann die Anwendung **SQLGetData** aufrufen, um die **Text**-, **ntext**-oder **Image** -Daten abzurufen. Dadurch wird verhindert, dass die **Text**-, **ntext**-oder **Image** -Daten für eine der Zeilen übertragen werden, die der Benutzer nicht ausgewählt hat, und daher kann die Übertragung sehr großer Datenmengen verhindert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Text-und image-Spalten](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Cursorverhalten](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
