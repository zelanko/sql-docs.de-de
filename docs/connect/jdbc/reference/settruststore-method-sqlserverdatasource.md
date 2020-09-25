---
description: setTrustStore-Methode (SQLServerDataSource)
title: setTrustStore-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be69bd333d0264e4833dd053979f1e3dfe5a9b39
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88354926"
---
# <a name="settruststore-method-sqlserverdatasource"></a>setTrustStore-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Pfad (einschließlich Dateiname) zur trustStore-Zertifikatsdatei fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setTrustStore(java.lang.String trustStore)  
```  
  
#### <a name="parameters"></a>Parameter  
 *trustStore*  
  
 Eine **Zeichenfolge** mit dem Pfad (einschließlich des Dateinamens) der trustStore-Zertifikatsdatei.  
  
## <a name="remarks"></a>Bemerkungen  
 Ist die trustStore-Eigenschaft nicht angegeben oder auf NULL festgelegt, wird der zu verwendende Zertifikatspeicher von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mithilfe der Suchregeln der Trust-Manager-Factory ermittelt. Die Vertrauenswürdigkeitsinformationen werden von der SunX509-Standardklasse „TrustManagerFactory“ an folgenden Speicherorten und in der folgenden Reihenfolge gesucht:  
  
-   1. Eine von der Java Virtual Machine (JVM)-Systemeigenschaft "javax.net.ssl.trustStore" angegebene Datei  
  
-   2. Datei "\<java-home>/lib/security/jssecacerts".  
  
-   3. Datei "\<java-home>/lib/security/cacerts".  
  
 Weitere Informationen finden Sie in der Dokumentation zur SunX509 TrustManager-Schnittstelle auf der Website von Sun Microsystems.  
  
 Ist die trustStore-Eigenschaft auf eine Zeichenfolge oder auf eine leere Zeichenfolge ("") festgelegt, sucht der Treiber anhand dieses Werts die trustStore-Datei, um das TLS-/SSL-Serverzertifikat zu überprüfen.  
  
 Die trustStorePassword-Eigenschaft kann zusammen mit der trustStore-Eigenschaft angegeben werden, und deren Wert wird zum Öffnen der trustStore-Datei verwendet. Weitere Informationen finden Sie unter [setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
