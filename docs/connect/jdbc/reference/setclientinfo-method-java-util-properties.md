---
title: setClientInfo-Methode (Java. util. Properties) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b2a8ec0b-40a2-44d1-90d9-a810d4132e56
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a332f42c8193c851a33036af214ac31366986023
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974740"
---
# <a name="setclientinfo-method-javautilproperties"></a>setClientInfo-Methode (java.util.Properties)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Wert der Eigenschaften für Clientinformationen der Verbindung fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setClientInfo (java.util.Properties properties)  
```  
  
#### <a name="parameters"></a>Parameter  
 *properties*  
  
 Ein Properties-Objekt mit der Liste der festzulegenden Eigenschaften für Clientinformationen.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese setClientInfo-Methode wird von der setClientInfo-Methode in der Java. SQL. Connection-Schnittstelle angegeben.  
  
 Von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] werden keine Eigenschaften für Clientinformationen unterstützt. Von dieser Methode werden Warnungen generiert, sofern vom *properties*-Eingabeparameter nicht auf einen leeren Eigenschaftensatz verwiesen wird. Das heißt, dass von dieser Methode Warnungen für die Eigenschaften generiert werden, die von der Anwendung festgelegt werden sollen. Zum Abrufen der einzelnen Warnungen sollte von Anwendungen die [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setClientInfo-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
