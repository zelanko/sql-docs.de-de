---
title: SetIntegratedSecurity-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
- SQLServerDataSource.setIntegratedSecurity
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ac959d60bb84fe4d63d2da80665c00c0783c4bf
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784412"
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
