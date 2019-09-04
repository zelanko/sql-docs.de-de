---
title: getportnumber-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e5dc38d0-4340-4ad7-a56e-1d2a0f0fd846
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 20850d10352a583abd7e0a8bd9747b6346ec3aaa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980833"
---
# <a name="getportnumber-method-sqlserverdatasource"></a>getPortNumber-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt die aktuelle Portnummer für die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getPortNumber()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** mit der aktuellen Portnummer.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Portnummer ist die TCP/IP-Portnummer, die beim Öffnen einer Socketverbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet wird. Ist die portNumber-Eigenschaft nicht festgelegt, wird von der getPortNumber-Methode der Standardwert "1433" zurückgegeben.  
  
> [!NOTE]  
>  Die [setportnumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md) -Methode führt keine Bereichs Überprüfung für den übergebenen Portwert durch. Sie können zivilrechtlichen Delikten-Nummern übergeben, die nicht gültig sind, wie z. b. 99999, ohne dass ein Fehler ausgelöst wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
