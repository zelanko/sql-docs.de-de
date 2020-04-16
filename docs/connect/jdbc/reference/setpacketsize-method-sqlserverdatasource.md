---
title: setPacketSize-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 297d37f6e0451e207d92dbc8a342b087c4d28895
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219369"
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>setPacketSize-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt die aktuelle Netzwerkpaketgröße (in Bytes) für die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Parameter  
 *packetSize*  
  
 Ein Wert vom Typ **int** mit der Netzwerkpaketgröße.  
  
## <a name="remarks"></a>Bemerkungen  
 Der akzeptable Wertebereich dieser Eigenschaft lautet "[-1 | 0 | 512..32767]". Wenn diese Eigenschaft auf einen Wert außerhalb des zulässigen Bereichs festgelegt wird, wird eine Ausnahme ausgelöst.  
  
 Die Anwendung versucht möglicherweise, die packetSize-Eigenschaft beim Herstellen einer Verbindung mit der Transport Layer Security (TLS) festzulegen, zuvor als Secure Sockets Layer-Verschlüsselung (SSL) bekannt. Die Paketgröße wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit dem Server ausgehandelt. Wenn die encrypt-Eigenschaft auf **TRUE** festgelegt ist und die ausgehandelte Paketgröße die TLS-Datensatzgröße des Standardsicherheitsanbieters der Java Virtual Machine-Instanz (JVM) übersteigt, wird vom Treiber ein Fehler ausgelöst, und die Verbindung wird getrennt.  
  
 Darüber hinaus wird von der Anwendung unter Umständen versucht, die packetSize-Eigenschaft ohne Anforderung der TLS-Verschlüsselung festzulegen. In diesem Fall gilt Folgendes: Wird vom Server vorausgesetzt, dass der Clientcomputer die TLS-Verschlüsselung unterstützt, wird vom Treiber die TLS-Datensatzgröße des Standardsicherheitsanbieters der JVM-Instanz überprüft. Übersteigt die packetSize-Eigenschaft die TLS-Datensatzgröße des Standardsicherheitsanbieters der Java Virtual Machine-Instanz (JVM), wird vom Treiber ein Fehler ausgelöst, und die Verbindung wird getrennt.  
  
 Weitere Informationen zur Verwendung von TLS finden Sie unter [Verwenden von Verschlüsselung](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
