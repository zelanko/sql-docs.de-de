---
title: SQLServerDataSourceObjectFactory-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ecec8f58587d6a57468f8078e1f680675bede77
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046848"
---
# <a name="sqlserverdatasourceobjectfactory-class"></a>SQLServerDataSourceObjectFactory-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt ein Objektfactory zum Materialisieren von Datenquellen aus der JNDI (Java Naming and Directory Interface) dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert:** java.lang.Object  
  
 **Implementiert:** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>Remarks  
 Diese Methode wird von allen Datenquellenklassen geerbt. Diese Klasse, von der ein ObjectFactory-Objekt implementiert wird, wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] als Teil der Unterstützung der Referenceable-Schnittstelle verfügbar gemacht. Von Java-Anwendungsservern wird getReference für Datenquellenklassen aufgerufen, wodurch ein Reference-Objekt erstellt wird, von dem der Klassenname intern als Klassenfactory verwendet wird.  
  
 Wenn das [-Objekt vom Java-Anwendungsserver dereferenziert werden muss, wird eine Instanz des ](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md)-Objekts erstellt und die getObjectInstance-Methode aufgerufen, um die Datenquellinstanz abzurufen. Dabei wird das -Objekt übergeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSourceObjectFactory-Elemente](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
