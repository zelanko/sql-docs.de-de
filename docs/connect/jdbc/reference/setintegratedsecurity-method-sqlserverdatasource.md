---
title: setintegratedsecurity-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
ms.openlocfilehash: 79d9090df19851af3a778e23b7919f28081f32ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974151"
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
  
 **true** , wenn IntegratedSecurity aktiviert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Legen Sie diese Eigenschaft auf **TRUE** fest, wenn der Benutzer der Anwendung anhand der Windows-Anmeldeinformationen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] authentifiziert werden soll. Bei **TRUE** wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] im Cache für Anmeldeinformationen des lokalen Computers nach Anmeldeinformationen gesucht, die bei der Anmeldung am Computer oder Netzwerk bereits angegeben wurden. Bei **FALSE** müssen Benutzername und Kennwort angegeben werden.  
  
> [!NOTE]  
>  Diese Eigenschaft wird nur auf [!INCLUDE[msCoName](../../../includes/msconame_md.md)] Windows-Betriebssystemen unterstützt.  
  
 Weitere Informationen zur Verwendung der integrierten Authentifizierung finden Sie unter " [aufbauen der Verbindungs-URL](../../../connect/jdbc/building-the-connection-url.md)".  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
