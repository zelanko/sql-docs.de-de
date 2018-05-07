---
title: SetPortNumber-Methode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5665bd5ed6f10a755f3980607995b19887908379
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="setportnumber-method-sqlserverdatasource"></a>setPortNumber-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt die Portnummer für die Kommunikation zu verwendende [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Portnummer*  
  
 Ein **Int** Wert, der die Portnummer enthält.  
  
## <a name="remarks"></a>Hinweise  
 Die Portnummer ist die TCP/IP-Portnummer, die verwendet wird, beim Öffnen einer Socketverbindung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Wenn die PortNumber-Eigenschaft nicht festgelegt ist, die [GetPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md) Methode der Standardwert 1433 zurückgegeben.  
  
> [!NOTE]  
>  SetPortNumber-Methode keine bereichsprüfung auf dem Portwert übergeben. Sie können eine Portnummer übergeben, die nicht gültig ist, z. B. 99999, ohne dabei einen Fehler auszulösen ist.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
