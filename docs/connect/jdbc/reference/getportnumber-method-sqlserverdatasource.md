---
title: getPortNumber-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8fcd2c1260ee69cbd3a50573f53b07bf429da402
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925239"
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
>  Die [setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)-Methode führt keine Bereichsüberprüfung für den übergebenen Portwert durch. Sie können also eine ungültige Portnummer wie 99999 übergeben, ohne dass ein Fehler ausgelöst wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
