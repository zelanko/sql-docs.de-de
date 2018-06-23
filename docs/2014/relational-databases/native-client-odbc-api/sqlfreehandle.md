---
title: SQLFreeHandle | Microsoft Docs
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
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8ba108cf9efcd6e7e8fd91ccc026fe616c113d1d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149369"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
  Im Manualcommit-Modus führt das Aufrufen von **SQLFreeHandle** für ein Anweisungshandle mit einer offenen Transaktion zu einem Rollback ausstehender Änderungen an der Datenbank. Durch das Aufrufen von **SQLFreeHandle** für ein Anweisungshandle werden immer alle geöffneten Cursor geschlossen und ausstehende Ergebnisse verworfen. Auf diese Weise werden alle zum Anweisungshandle gehörenden Ressourcen freigegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLFreeHandle-Funktion](http://go.microsoft.com/fwlink/?LinkId=59345)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  