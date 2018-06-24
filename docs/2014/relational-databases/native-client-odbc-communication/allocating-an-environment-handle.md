---
title: Zuordnen eines Umgebungshandles | Microsoft Docs
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
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 89bf5353b37858c12212eed4567e0bae7f49d77f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056487"
---
# <a name="allocating-an-environment-handle"></a>Zuordnen eines Umgebungshandles
  Bevor eine Anwendung eine ODBC-Funktion aufrufen kann, muss sie die ODBC-Umgebung initialisieren und ein Umgebungshandle zuordnen. Dies ist das globale Kontexthandle und der Platzhalter für die anderen Handles in ODBC. Dazu rufen **SQLAllocHandle** mit der *HandleType* Parametersatz auf SQL_HANDLE_ENV und *InputHandle* auf SQL_NULL_HANDLE festgelegt wird.  
  
 Nachdem das Umgebungshandle zugewiesen wurde, muss die Anwendung Umgebungsattribute festlegen, um anzugeben, welche Version der ODBC-Funktionsaufrufe verwendet wird. Die ODBC 3. verwenden zu können. *x* -Funktionen aufrufen [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) mit der *Attribut* Parametersatz auf SQL_ATTR_ODBC_VERSION und *ValuePtr* SQL_OV_ festgelegt ODBC3.  
  
## <a name="see-also"></a>Siehe auch  
 [Bei der Kommunikation mit SQLServer &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  