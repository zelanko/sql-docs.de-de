---
title: setClientInfo-Methode (java.lang.String, java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 177b92c12ba9daa410de1e65cc3a38b8744f4149
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927169"
---
# <a name="setclientinfo-method-javalangstring-javalangstring"></a>setClientInfo-Methode (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Wert der angegebenen Eigenschaft für Clientinformationen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setClientInfo (java.lang.String name,  
                           java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parameter  
 *name*  
  
 Eine Zeichenfolge mit dem Namen der festzulegenden Eigenschaft für Clientinformationen.  
  
 *value*  
  
 Eine Zeichenfolge mit dem Wert, auf den die Eigenschaft für Clientinformationen festgelegt werden soll  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setClientInfo-Methode wird von der setClientInfo-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] werden keine Eigenschaften für Clientinformationen unterstützt. In der JDBC Driver-Version 2.0 wird von dieser Methode eine Warnung für eine Eigenschaft generiert. Zum Abrufen einer Warnung sollte von Anwendungen die [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setClientInfo-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
