---
title: Verwenden von Autofetch mit ODBC-Cursor | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 177de8fe974d3aa4970f21607693a73c3da0b70e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047372"
---
# <a name="using-autofetch-with-odbc-cursors"></a>Verwenden von Autofetch mit ODBC-Cursorn
  Beim Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt eine automatische Abrufoption beim Server Cursortypen. Mit automatischer Abrufoption die **SQLExecute** oder **SQLExecDirect** -Funktion, die den Cursor öffnen verfügt auch über einen impliziten [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST)-Funktion. Die Zeilen des ersten Rowsets werden während der Ausführung der Anweisung an die gebundenen Anwendungsvariablen zurückgegeben, wodurch ein weiterer Roundtrip über das Netzwerk bis zum Server vermieden wird. [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) wird nicht unterstützt, wenn die automatische Abrufoption aktiviert ist; der Resultsetspalten an Programmvariablen gebunden werden müssen.  
  
 Autofetch wird von Anwendungen angefordert, wenn für das treiberspezifische SQL_SOPT_SS_CURSOR_OPTIONS-Anweisungsattribut SQL_CO_AF festgelegt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Details zum Programmieren von Cursorn &#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  