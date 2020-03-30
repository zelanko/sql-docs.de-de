---
title: getSendStringParametersAsUnicode-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
ms.openlocfilehash: df27a5368dfea7f417fb84e2ebe38a8987165aec
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979969"
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
  
## <a name="remarks"></a>Bemerkungen  
 Ist die sendStringParametersAsUnicode-Eigenschaft auf **true** (Standardeinstellung) festgelegt, werden Zeichenfolgenparameter im Unicode-Format an den Server gesendet. Ist die sendStringParametersAsUnicode-Eigenschaft auf **false** festgelegt, werden Zeichenfolgenparameter nicht im Unicode-Format, sondern im ASCII-/MBCS-Format an den Server gesendet. Ist die sendStringParametersAsUnicode-Eigenschaft nicht festgelegt, wird von getSendStringParametersAsUnicode der Standardwert **true** zurückgegeben.  
  
 Weitere Informationen zur sendStringParametersAsUnicode-Verbindungseigenschaft finden Sie unter [Festlegen von Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
