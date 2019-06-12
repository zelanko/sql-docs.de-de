---
title: SetIntegratedSecurity-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setIntegratedSecurity
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7d922c2c2fcfadb6b7807b8d2845f8d3e6c5188c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66780446"
---
# <a name="setintegratedsecurity-method-sqlserverdatasource"></a>setIntegratedSecurity-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob die integratedSecurity-Eigenschaft aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setIntegratedSecurity(boolean enable)  
```  
  
#### <a name="parameters"></a>Parameter  
 *enable*  
  
 **"true"** Wenn IntegratedSecurity aktiviert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Remarks  
 Legen Sie diese Eigenschaft auf **TRUE** fest, wenn der Benutzer der Anwendung anhand der Windows-Anmeldeinformationen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] authentifiziert werden soll. Bei **TRUE** wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] im Cache für Anmeldeinformationen des lokalen Computers nach Anmeldeinformationen gesucht, die bei der Anmeldung am Computer oder Netzwerk bereits angegeben wurden. Bei **FALSE** müssen Benutzername und Kennwort angegeben werden.  
  
> [!NOTE]  
>  Diese Eigenschaft wird nur auf [!INCLUDE[msCoName](../../../includes/msconame_md.md)] Windows-Betriebssystemen unterstützt.  
  
 Weitere Informationen über die integrierte Authentifizierung finden Sie unter [Building the Connection URL](../../../connect/jdbc/building-the-connection-url.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
