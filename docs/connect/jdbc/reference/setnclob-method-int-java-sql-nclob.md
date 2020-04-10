---
title: setNClob(int, java.sql.NClob)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 48c8aa2a-4185-4837-b592-830e60f8ca0b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c8fcb66b008c5290000b7038796359496f545d3
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80901004"
---
# <a name="setnclob-method-int-javasqlnclob"></a>setNClob-Methode (int, java.sql.NClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf das angegebene NClob-Objekt fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setNClob(int parameterIndex,  
              java.sql.NClob value)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterIndex*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
 *value*  
  
 Ein NClob-Objekt zum Angeben des Parameterwerts.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setNClob-Methode wird von der setNClob-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setNClob-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
