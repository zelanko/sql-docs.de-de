---
title: Sqltenvattr | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 113c4508489e0f1dad8d134db7f86fc42371b456
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702148"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
  Die [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250) definiert, wie ODBC-Treiber die **SQLSetEnvAttr** -Attributspezifikationen aus Anwendungen interpretieren sollen, die in die ODBC 2.*x* - oder ODBC 3.*x* -API geschrieben wurden. Der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Native Client entspricht diesen Regeln.  
  
 Eines der Attribute ist, das von **SQLSetEnvAttr** gesteuert wird, bestimmt, ob Verbindungspooling verwendet werden soll. Wenn Verbindungspooling mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwendet wird, muss für den *DriverCompletion* -Parameter SQL_DRIVER_NOPROMPT festgelegt werden, wenn eine Verbindung mit [SQLDriverConnect](sqldriverconnect.md) oder **SQLConnect**hergestellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlsettenvattr-Funktion](https://go.microsoft.com/fwlink/?LinkId=59369)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
