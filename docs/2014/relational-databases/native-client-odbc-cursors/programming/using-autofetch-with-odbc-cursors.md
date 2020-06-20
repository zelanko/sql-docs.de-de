---
title: Verwenden von Autofetch mit ODBC-Cursorn | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: rothja
ms.author: jroth
ms.openlocfilehash: e3d9374cf9ceab4a7e73cc0059783486f2bf9c41
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85020755"
---
# <a name="using-autofetch-with-odbc-cursors"></a>Verwenden von Autofetch mit ODBC-Cursorn
  Wenn eine Verbindung mit einer Instanz von besteht [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt der Native Client ODBC-Treiber bei Verwendung eines beliebigen Server Cursor Typs eine Autofetch-Option. Mit Autofetch verfügt die **SQLExecute** -oder **SQLExecDirect** -Funktion, die den Cursor öffnet, auch über eine implizite [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST)-Funktion. Die Zeilen des ersten Rowsets werden während der Ausführung der Anweisung an die gebundenen Anwendungsvariablen zurückgegeben, wodurch ein weiterer Roundtrip über das Netzwerk bis zum Server vermieden wird. [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) wird nicht unterstützt, wenn die Autofetch-Option aktiviert ist. die Resultsetspalten müssen an Programmvariablen gebunden werden.  
  
 Autofetch wird von Anwendungen angefordert, wenn für das treiberspezifische SQL_SOPT_SS_CURSOR_OPTIONS-Anweisungsattribut SQL_CO_AF festgelegt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Details zur Cursor Programmierung &#40;ODBC-&#41;](cursor-programming-details-odbc.md)  
  
  
