---
title: Gebundene im Vergleich zu Ungebundenen Text- und Image-Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
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
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d77a71aae13c9601acc0ba56146e7882e6ee6e7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430629"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Gebundene im Vergleich zu Ungebundenen Text- und Image-Spalten
  Wenn Servercursor verwendet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber wurde optimiert, um überträgt keine Daten für ungebundene **Text**, **Ntext**, oder **Image** Spalten in der Zeit **SQLFetch** erfolgt. Die **Text**, **Ntext**, oder **Image** Daten werden erst die Anwendungsprobleme nicht tatsächlich vom Server abgerufen [SQLGetData](../native-client-odbc-api/sqlgetdata.md) für die die Spalte.  
  
 Viele Anwendungen können geschrieben werden, damit keine **Text**, **Ntext**, oder **Image** Daten werden angezeigt, während ein Benutzer einfach nach oben oder unten in einem Cursor einen Bildlauf ist. Wenn ein Benutzer eine Zeile aus, um weitere Informationen zu erhalten auswählt, wird die Anwendung kann dann aufrufen **SQLGetData** zum Abrufen der **Text**, **Ntext**, oder **Image** Daten. Dadurch wird verhindert, übertragen die **Text**, **Ntext**, oder **Image** Daten aus der Zeilen, die der Benutzer nicht auswählen, und kann daher zu verhindern, dass die Übertragung von sehr großen die Mengen von Daten.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Text- und Image-Spalten](managing-text-and-image-columns.md)   
 [Cursorverhalten](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  
