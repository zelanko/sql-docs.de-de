---
title: Sqlgetcurrsorname | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 603a2b5be4ca75495f094aa838d0373a9689a523
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62657776"
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
  Wenn die Anwendung keinen Cursornamen angibt, generiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber bei der Cursorerstellung einen Namen für die Anwendung. Die Anwendung kann **SQLGetCursorName** verwenden, um den treiberdefinierten Cursornamen für positionierte UPDATE- und DELETE-Anweisungen abzurufen. Die Anwendung muss **SQLSetCursorName** nicht aufrufen, um positionierte Datenbearbeitungsanweisungen zu nutzen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlgetcurrsorname-Funktion](https://go.microsoft.com/fwlink/?LinkId=59349)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
