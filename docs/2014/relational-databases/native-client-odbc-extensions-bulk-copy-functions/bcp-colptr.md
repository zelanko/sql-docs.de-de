---
title: Bcp_colptr | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_colptr
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0c548a1decd7410cd1cbc8df3ee68126e62ca25
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413569"
---
# <a name="bcpcolptr"></a>bcp_colptr
  Legt die Datenadresse der Programmvariablen für die aktuelle Kopie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_colptr (  
HDBC   
hdbc  
,  
LPCBYTE   
pData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *HDBC*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *pData*  
 Ist ein Zeiger auf die zu kopierenden Daten. Wenn der gebundene Datentyp ein Typ mit umfangreichen Werten ist (beispielsweise SQLTEXT oder SQLIMAGE), dann kann *pData* NULL sein. Ein *pData* -Zeiger mit dem Wert NULL gibt an, dass lange Datenwerte mithilfe von [bcp_moretext](bcp-moretext.md)in Ausschnitten an SQL Server gesendet werden.  
  
 Wenn *pData* auf NULL festgelegt wird und die Spalte, die dem gebundenen Feld zugeordnet ist, keinen umfangreichen Datentyp enthält, dann schlägt **bcp_colptr** fehl.  
  
 Weitere Informationen zu Datentypen für umfangreiche Werte finden Sie unter [bcp_bind](bcp-bind.md)**.**  
  
 *idxServerCol*  
 Die Ordnungsposition der Spalte in der Datenbanktabelle, in die die Daten kopiert werden. Die erste Spalte einer Tabelle ist die Spalte 1. Die Ordnungsposition einer Spalte wird von [SQLColumns](../native-client-odbc-api/sqlcolumns.md)ausgegeben.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Die **Bcp_colptr** -Funktion können Sie die Adresse der Quelldaten für eine bestimmte Spalte ändern, wenn beim Kopieren von Daten zu SQL Server mit [Bcp_sendrow](bcp-sendrow.md).  
  
 Anfänglich wird der Zeiger auf Benutzerdaten durch einen Aufruf von **bcp_bind**festgelegt. Wenn sich die Datenadresse der Programmvariablen zwischen Aufrufen von **bcp_sendrow**ändert, können Sie den Zeiger mit einem Aufruf von **bcp_colptr** auf die Datenadresse zurücksetzen. Mit dem nächsten Aufruf von **bcp_sendrow** werden die Daten gesendet, die durch den Aufruf von **bcp_colptr**adressiert wurden.  
  
 Für jede Tabellenspalte, deren Datenadresse geändert werden soll, muss ein separater **bcp_colptr** -Aufruf angegeben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
