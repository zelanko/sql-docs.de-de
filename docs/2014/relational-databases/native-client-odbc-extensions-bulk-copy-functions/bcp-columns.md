---
title: Bcp_columns | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_columns
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fcfbbdb1881662401e791ea197115120444cf855
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096920"
---
# <a name="bcpcolumns"></a>bcp_columns
  Legt die Gesamtanzahl der Spalten fest, die in der Benutzerdatei gefunden wurden und mit einem Massenkopiervorgang in oder aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden sollen. [Bcp_setbulkmode](bcp-setbulkmode.md) anstelle von Bcp_columns verwendet werden können und [Bcp_colfmt](bcp-colfmt.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_columns (  
HDBC   
hdbc  
,  
INT   
nColumns  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *HDBC*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *nColumns*  
 Die Gesamtzahl der Spalten in der Benutzerdatei. Auch wenn Sie zum Massenkopieren von Daten aus der Benutzerdatei zum Vorbereiten einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle und nicht alle Spalten in der Benutzerdatei kopieren möchten, müssen Sie immer noch festlegen *nColumns* die Gesamtzahl der benutzerdateispalten.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion kann aufgerufen werden, erst nach dem [Bcp_init](bcp-init.md) mit einem gültigen Dateinamen aufgerufen wurde.  
  
 Sie sollten diese Funktion nur aufrufen, wenn Sie ein Benutzerdateiformat verwenden möchten, das sich vom Standardformat unterscheidet. Weitere Informationen zu der eine Beschreibung des Benutzer-Standardformats für, finden Sie unter **Bcp_init**.  
  
 Nach dem Aufruf `bcp_columns`, rufen Sie [Bcp_colfmt](bcp-colfmt.md)für jede Spalte in der Benutzerdatei, um benutzerdefinierte Dateiformat vollständig zu definieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
