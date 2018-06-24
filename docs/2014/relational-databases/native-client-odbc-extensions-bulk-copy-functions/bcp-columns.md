---
title: Bcp_columns | Microsoft Docs
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f2f7cb508f9b7715abbc2505f38b30795df2d142
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048719"
---
# <a name="bcpcolumns"></a>bcp_columns
  Legt die Gesamtanzahl der Spalten fest, die in der Benutzerdatei gefunden wurden und mit einem Massenkopiervorgang in oder aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden sollen. [Bcp_setbulkmode](bcp-setbulkmode.md) anstelle Bcp_columns verwendet werden können und [Bcp_colfmt](bcp-colfmt.md).  
  
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
 Die Gesamtzahl der Spalten in der Benutzerdatei. Auch wenn Sie zum Massenkopieren von Daten aus der Benutzerdatei zum Vorbereiten einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle und nicht alle Spalten in der Benutzerdatei kopieren möchten, müssen Sie immer noch festlegen *nColumns* auf die Gesamtzahl der benutzerdateispalten.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion kann aufgerufen werden, erst nach dem [Bcp_init](bcp-init.md) mit einem gültigen Dateinamen aufgerufen wurde.  
  
 Sie sollten diese Funktion nur aufrufen, wenn Sie ein Benutzerdateiformat verwenden möchten, das sich vom Standardformat unterscheidet. Weitere Informationen über eine Beschreibung des Benutzer-Standardformats für finden Sie unter **Bcp_init**.  
  
 Nach dem Aufruf `bcp_columns`, rufen Sie [Bcp_colfmt](bcp-colfmt.md)für jede Spalte in der Benutzerdatei, um benutzerdefinierte Dateiformat vollständig zu definieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  