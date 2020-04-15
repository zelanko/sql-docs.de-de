---
title: Gebunden vs. Ungebundene Text- und Bildspalten | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0cfa05f7019342d63ab6f3092c3b6df5ae6e8daa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297734"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Vergleich von gebundenen und ungebundenen Text- und Image-Spalten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verwendung von Servercursorn ist der Native Client ODBC-Treiber so optimiert, dass die Daten für ungebundene **Text-,** **ntext-** oder **Bildspalten** zum Zeitpunkt der **SqlFetch-Arbeit** nicht übertragen werden. Die **Text-,** **ntext-** oder **Bilddaten** werden erst dann vom Server abgerufen, wenn die Anwendung [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) für die Spalte ausgibt.  
  
 Viele Anwendungen können so geschrieben werden, dass keine **Text-,** **ntext-** oder **Bilddaten** angezeigt werden, während ein Benutzer einfach in einem Cursor nach oben und unten scrollt. Wenn ein Benutzer eine Zeile auswählt, um mehr Details zu erhalten, kann die Anwendung **SQLGetData** aufrufen, um den **Text,** **ntext**oder **Bilddaten** abzurufen. Dadurch wird verhindert, dass die **Text-,** **ntext-** oder **Bilddaten** für eine der Zeilen übertragen werden, die der Benutzer nicht auswählt, und kann daher die Übertragung sehr großer Datenmengen verhindern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Text- und Bildspalten](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Cursorverhalten](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
