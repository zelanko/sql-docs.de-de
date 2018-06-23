---
title: SQLSetEnvAttr | Microsoft Docs
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
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 663d274b13a8cc5ac8ac53a2d8f9da4f925c7d55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150126"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
  Die [ODBC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=45250) definiert, wie ODBC-Treiber die **SQLSetEnvAttr** -Attributspezifikationen aus Anwendungen interpretieren sollen, die in die ODBC 2.*x* - oder ODBC 3.*x* -API geschrieben wurden. Der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Native Client entspricht diesen Regeln.  
  
 Eines der Attribute ist, das von **SQLSetEnvAttr** gesteuert wird, bestimmt, ob Verbindungspooling verwendet werden soll. Wenn Verbindungspooling mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwendet wird, muss für den *DriverCompletion* -Parameter SQL_DRIVER_NOPROMPT festgelegt werden, wenn eine Verbindung mit [SQLDriverConnect](sqldriverconnect.md) oder **SQLConnect**hergestellt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLSetEnvAttr-Funktion](http://go.microsoft.com/fwlink/?LinkId=59369)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  