---
title: Bcp_columns | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
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
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c1107919200b3546274a3a78a89562c9ed715216
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427449"
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
  
  
