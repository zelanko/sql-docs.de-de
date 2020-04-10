---
title: getPrecision-Methode (SQLServerParameterMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getPrecision
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bd79484-bab6-423b-978f-d7ec7132ebeb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dbca77be55cd855f2e293324d6cd7c4ca5471b7e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925218"
---
# <a name="getprecision-method-sqlserverparametermetadata"></a>getPrecision-Methode (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Anzahl von Dezimalstellen des angegebenen Parameters ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getPrecision(int param)  
```  
  
#### <a name="parameters"></a>Parameter  
 *param*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int**, der die Genauigkeit des angegebenen Parameters angibt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getPrecision-Methode wird von der getPrecision-Methode in der java.sql.ParameterMetaData-Schnittstelle angegeben.  
  
 Für Zahlentypen wird von dieser Methode die Anzahl von Dezimalstellen abgerufen. Für Zeichentypen wird die maximale Länge in Zeichen abgerufen. Für binäre Typen wird die maximale Länge in Bytes abgerufen. Ist die Dezimalstellenanzahl unbekannt, wird von der Methode "0" zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerParameterMetaData-Methoden](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData-Elemente](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData-Klasse](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
