---
title: SQLServerDataSourceObjectFactory-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cf4c90644282ff420e064e7a7b5b99a93c257194
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971381"
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
  
 Wenn der Java-Anwendungs Server das Verweis Objekt dereferenzieren muss, wird eine Instanz des SQLServerDataSourceObjectFactory-Objekts erstellt und die [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md) -Methode aufgerufen, wobei das Verweis Objekt übergeben wird, um die Datenquelle abzurufen. lichen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSourceObjectFactory-Elemente](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
