---
title: GetSendStringParametersAsUnicode-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3dedc988bd4ddf32046a9a29abe5b83b293bf04
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683138"
---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>getSendStringParametersAsUnicode-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt einen Wert vom Typ **boolean** zurück, mit dem angegeben wird, ob das Senden von Zeichenfolgenparametern an den Server im Unicode-Format aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert ist **true**, wenn Zeichenfolgenparameter im Unicode-Format an den Server gesendet werden. Andernfalls lautet der Wert **false**.  
  
## <a name="remarks"></a>Remarks  
 Ist die sendStringParametersAsUnicode-Eigenschaft auf **true** (Standardeinstellung) festgelegt, werden Zeichenfolgenparameter im Unicode-Format an den Server gesendet. Ist die sendStringParametersAsUnicode-Eigenschaft auf **false** festgelegt, werden Zeichenfolgenparameter nicht im Unicode-Format, sondern im ASCII-/MBCS-Format an den Server gesendet. Ist die sendStringParametersAsUnicode-Eigenschaft nicht festgelegt, wird von getSendStringParametersAsUnicode der Standardwert **true** zurückgegeben.  
  
 Weitere Informationen zur SendStringParametersAsUnicode-Verbindungseigenschaft finden Sie unter [Festlegen der Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
