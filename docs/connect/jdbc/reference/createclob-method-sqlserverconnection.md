---
description: createClob-Methode (SQLServerConnection)
title: createClob-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58b0865a-1cde-4046-9761-51e471294023
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2b9e017c42737eeed2df281c4e817dff99a45821
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437962"
---
# <a name="createclob-method-sqlserverconnection"></a>createClob-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt ein CLOB-Objekt ohne Daten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Clob createClob()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Clob-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese createClob-Methode wird von der createClob-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Dank dieser Methode wird der [SQLServerBlob-Konstruktor &#40;SQLServerConnection, java.lang.String&#41;](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md) nicht mehr benötigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
