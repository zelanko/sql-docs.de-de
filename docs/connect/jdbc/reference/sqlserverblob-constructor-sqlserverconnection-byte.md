---
title: SQLServerBlob-Konstruktor (SQLServerConnection, byte) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection, byte[].SQLServerBlob
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fe573e3-30db-4828-abab-e9346493e931
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a0b33640f9978b5b7b383e7bd89c62e026d5386
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789814"
---
# <a name="sqlserverblob-constructor-sqlserverconnection-byte"></a>SQLServerBlob-Konstruktor (SQLServerConnection, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialisiert eine neue Instanz der [SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)-Klasse, wenn ein [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt und ein **Bytearray** angegeben werden.  
  
> [!NOTE]  
>  Diese Methode ist seit Version 2.0 des JDBC-Treibers veraltet. Verwenden Sie stattdessen die [createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public SQLServerBlob(SQLServerConnection connection,  
                     byte[] data)  
```  
  
#### <a name="parameters"></a>Parameter  
 *connection*  
  
 Ein SQLServerConnection-Objekt.  
  
 *data*  
  
 Ein **Bytearray**.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerBlob-Konstruktoren](../../../connect/jdbc/reference/sqlserverblob-constructors.md)   
 [SQLServerBlob-Elemente](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob-Klasse](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
