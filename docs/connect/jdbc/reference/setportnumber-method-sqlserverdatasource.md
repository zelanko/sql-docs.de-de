---
title: setportnumber-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c171e8fb78553275d6a1f5d4bcce485a470f94a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973189"
---
# <a name="setportnumber-method-sqlserverdatasource"></a>setPortNumber-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt die Portnummer für die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Parameter  
 *portNumber*  
  
 Ein Wert vom Typ **int**, der die Portnummer enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Portnummer ist die TCP/IP-Portnummer, die beim Öffnen einer Socketverbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet wird. Wenn die portNumber-Eigenschaft nicht festgelegt ist, gibt die [getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)-Methode den Standardwert „1433“ zurück.  
  
> [!NOTE]  
>  Die setportnumber-Methode führt keine Bereichs Überprüfung für den übergebenen Portwert durch. Sie können eine ungültige Portnummer wie 99999 übergeben, ohne dass ein Fehler ausgelöst wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
