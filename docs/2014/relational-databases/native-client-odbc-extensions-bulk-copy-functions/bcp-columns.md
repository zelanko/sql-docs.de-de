---
title: bcp_columns | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63225522"
---
# <a name="bcp_columns"></a>bcp_columns
  Legt die Gesamtanzahl der Spalten fest, die in der Benutzerdatei gefunden wurden und mit einem Massenkopiervorgang in oder aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden sollen. [bcp_setbulkmode](bcp-setbulkmode.md) können anstelle von bcp_columns und [bcp_colfmt](bcp-colfmt.md)verwendet werden.  
  
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
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *nColumns*  
 Die Gesamtzahl der Spalten in der Benutzerdatei. Auch wenn Sie das Massen Kopieren von Daten aus der Benutzerdatei in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle vorbereiten und nicht alle Spalten in der Benutzerdatei kopieren möchten, müssen Sie *nColumns* trotzdem auf die Gesamtzahl der Benutzerdatei Spalten festlegen.  
  
## <a name="returns"></a>Rückgabe  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion kann erst aufgerufen werden, nachdem [bcp_init](bcp-init.md) mit einem gültigen Dateinamen aufgerufen wurde.  
  
 Sie sollten diese Funktion nur aufrufen, wenn Sie ein Benutzerdateiformat verwenden möchten, das sich vom Standardformat unterscheidet. Weitere Informationen zu einer Beschreibung des standardmäßigen Benutzerdatei Formats finden Sie unter **bcp_init**.  
  
 Nach dem `bcp_columns`Aufrufen von müssen Sie für jede Spalte in der Benutzerdatei [bcp_colfmt](bcp-colfmt.md)aufrufen, um ein benutzerdefiniertes Dateiformat vollständig zu definieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
