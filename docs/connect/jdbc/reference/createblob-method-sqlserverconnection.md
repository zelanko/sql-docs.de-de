---
title: createBlob-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 630a93b0-6e3c-4255-a007-1097ce0ee243
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3d70c72b860044a7e61b4a6dc5474c465fb60e89
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955405"
---
# <a name="createblob-method-sqlserverconnection"></a>createBlob-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt ein Blobobjekt ohne Daten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Blob createBlob()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Blob-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese createBlob-Methode wird von der createBlob-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Dank dieser Methode wird der [SQLServerBlob-Konstruktor &#40;SQLServerConnection, byte&#41;](../../../connect/jdbc/reference/sqlserverblob-constructor-sqlserverconnection-byte.md) nicht mehr benötigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
