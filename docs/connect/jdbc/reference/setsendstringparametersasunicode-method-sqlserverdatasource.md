---
title: SetSendStringParametersAsUnicode-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49198d63-76cb-4843-8d04-e49b1fbb6916
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b630f2bbe44f4484364aa1b99ea987c8888554c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637818"
---
# <a name="setsendstringparametersasunicode-method-sqlserverdatasource"></a>setSendStringParametersAsUnicode-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt einen Wert vom Typ **boolean** fest, mit dem angegeben wird, ob das Senden von Zeichenfolgenparametern an den Server im Unicode-Format aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setSendStringParametersAsUnicode(boolean sendStringParametersAsUnicode)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sendStringParametersAsUnicode*  
  
 Der Wert ist **true**, wenn Zeichenfolgenparameter im Unicode-Format an den Server gesendet werden. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Remarks  
 Ist die sendStringParametersAsUnicode-Eigenschaft auf **true** (Standardeinstellung) festgelegt, werden Zeichenfolgenparameter im Unicode-Format an den Server gesendet. Ist die sendStringParametersAsUnicode-Eigenschaft auf **false** festgelegt, werden Zeichenfolgenparameter nicht im Unicode-Format, sondern im ASCII-/MBCS-Format an den Server gesendet. Ist die sendStringParametersAsUnicode-Eigenschaft nicht festgelegt, wird von [getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md) der Standardwert **true** zurückgegeben.  
  
 Weitere Informationen zur SendStringParametersAsUnicode-Verbindungseigenschaft finden Sie unter [Festlegen der Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
