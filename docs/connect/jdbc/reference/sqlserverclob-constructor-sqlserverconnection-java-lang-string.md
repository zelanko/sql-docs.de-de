---
title: SQLServerClob-Konstruktor (SQLServerConnection, java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.SQLServerClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7058f4f7-ef3e-4d62-90d1-79299708b1eb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb6b459f8193daebb69ad67ffaab5beab526f710
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920390"
---
# <a name="sqlserverclob-constructor-sqlserverconnection-javalangstring"></a>SQLServerClob-Konstruktor (SQLServerConnection, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialisiert eine neue Instanz der [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)-Klasse, wenn ein [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt und eine Datenzeichenfolge angegeben werden.  
  
> [!NOTE]  
>  Diese Methode ist seit Version 2.0 des JDBC-Treibers veraltet. Verwenden Sie stattdessen die [createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public SQLServerClob(SQLServerConnection connection,  
                     java.lang.String data)  
```  
  
#### <a name="parameters"></a>Parameter  
 *connection*  
  
 Ein SQLServerConnection-Objekt.  
  
 *data*  
  
 Die CLOB-Daten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerClob-Konstruktoren](../../../connect/jdbc/reference/sqlserverclob-constructors.md)   
 [SQLServerClob-Elemente](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob-Klasse](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
