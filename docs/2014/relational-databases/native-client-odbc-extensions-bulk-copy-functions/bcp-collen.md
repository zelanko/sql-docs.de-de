---
title: bcp_collen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3fe50863656db9faf60613c0ff9f4de7a9d18875
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019724"
---
# <a name="bcp_collen"></a>bcp_collen
  Legt die Datenlänge in der Programmvariable für das aktuelle Massenkopieren nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *cbData*  
 Die Länge der Daten in der Programmvariable ohne die Länge eines Längenindikators oder Längenabschlusszeichens. Wenn Sie *cbData* auf SQL_NULL_DATA setzen, wird angegeben, dass alle zum Server kopierten Zeilen einen NULL-Wert für die Spalte enthalten. Wenn Sie es auf SQL_VARLEN_DATA setzen, geben Sie damit an, dass ein Zeichenfolgenabschlusszeichen oder eine andere Methode verwendet wird, um die Länge der kopierten Daten zu bestimmen. Wenn sowohl ein Längenindikator als auch ein Abschlusszeichen vorliegen, bestimmt das System, was verwendet werden soll, daran, bei welchem Vorgang weniger Daten kopiert werden.  
  
 *idxServerCol*  
 Die Ordnungsposition der Spalte in der Tabelle, in die die Daten kopiert werden. Die erste Spalte ist 1. Die Ordnungsposition einer Spalte wird von [SQLColumns](../native-client-odbc-api/sqlcolumns.md)ausgegeben.  
  
## <a name="returns"></a>Gibt zurück  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Mit der **bcp_collen** -Funktion können Sie die Datenlänge in der Programmvariable für eine bestimmte Spalte ändern, wenn Sie Daten mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bcp_sendrow [nach](bcp-sendrow.md)kopieren.  
  
 Anfänglich wird die Datenlänge beim Aufrufen von [bcp_bind](bcp-bind.md) bestimmt. Wenn sich die Datenlänge zwischen den Aufrufen von **bcp_sendrow** ändert und kein Längenpräfix oder -abschlusszeichen verwendet wird, können Sie **bcp_collen** aufrufen, um die Länge zurückzusetzen. Mit dem nächsten Aufruf von **bcp_sendrow** wird der Längensatz vom Aufruf von **bcp_collen**verwendet.  
  
 Für jede Spalte in der Tabelle, deren Datenlänge Sie ändern möchten, muss **bcp_collen** einmal aufgerufen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
