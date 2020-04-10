---
title: Klasse „SQLServerConnection“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 937292a6-1525-423e-a2b2-a18fd34c2893
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6248e126806b15592bbc3d6c458045ca7d9db042
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920678"
---
# <a name="sqlserverconnection-class"></a>SQLServerConnection-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt eine JDBC-Verbindung mit einer [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Implementiert:** [ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md), java.io.Serializable  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerConnection  
```  
  
## <a name="remarks"></a>Bemerkungen  
 SQLServerConnection unterstützt JDBC-Verbindungspooling und kann entweder eine physische JDBC-Verbindung oder eine logische JDBC-Verbindung sein. SQLServerConnection verwaltet die Transaktionssteuerung für alle Anweisungen, die aus ihr erstellt wurden, und kann an verteilten XA-Transaktionen teilnehmen, die über einen XAResource-Adapter verwaltet werden.  
  
 SQLServerConnection verwaltet einen Pool vorbereiteter Anweisungshandles. Vorbereitete Anweisungen werden einmal vorbereitet und werden normalerweise mehrere Male mit unterschiedlichen Parameterdatenwerten ausgeführt. Vorbereitete Anweisungen werden ebenfalls über logische (als Poolverbindung verwendete) Verbindungsgrenzen hinweg beibehalten.  
  
> [!NOTE]  
>  SQLServerConnection ist nicht threadsicher. Mehrere aus einer einzelnen Verbindung erstellte Anweisungen können simultan in parallelen Threads verarbeitet werden.  
  
 Diese Klasse unterstützt das Entpacken in die SQLServerConnection-Klasse, die java.sql.connection-Schnittstelle und die ISQLServerConnection-Schnittstelle. Weitere Informationen finden Sie im Artikel [Wrapper und Schnittstellen](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
