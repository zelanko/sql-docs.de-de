---
title: Gebundene im Vergleich zu Ungebundenen Text- und Image-Spalten | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c5129c6b865723721bbb6f176893c950cdf905fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050091"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Gebundene im Vergleich zu Ungebundenen Text- und Image-Spalten
  Wenn Servercursor verwendet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber optimiert und überträgt keine Daten für ungebundene **Text**, **Ntext**, oder **Image** Spalten in der Zeit **SQLFetch** erfolgt. Die **Text**, **Ntext**, oder **Image** Daten werden erst der Anwendungsprobleme nicht tatsächlich vom Server abgerufenen [SQLGetData](../native-client-odbc-api/sqlgetdata.md) für die die Spalte.  
  
 Viele Clientanwendungen können geschrieben werden, damit keine **Text**, **Ntext**, oder **Image** Daten werden angezeigt, während ein Benutzer in einem Cursor einfach nach oben oder unten scrollen ist. Wenn ein Benutzer eine Zeile aus, um weitere Details abzurufen auswählt, wird die Anwendung kann dann aufrufen **SQLGetData** zum Abrufen der **Text**, **Ntext**, oder **Image** Daten. Dies verhindert, dass Übertragung der **Text**, **Ntext**, oder **Image** Daten für alle Zeilen der Benutzer nicht auswählen, und kann daher zu verhindern, dass die Übertragung von sehr großen Datenmengen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Text- und Image-Spalten](managing-text-and-image-columns.md)   
 [Cursorverhalten](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  