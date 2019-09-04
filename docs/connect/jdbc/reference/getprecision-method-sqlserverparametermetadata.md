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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b0c6b7d8c69e1cc6bc4a9e8d239c3a47c24573d9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980780"
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
 Diese getPrecision-Methode wird von der getPrecision-Methode in der Java. SQL. parametermetadata-Schnittstelle angegeben.  
  
 Für Zahlentypen wird von dieser Methode die Anzahl von Dezimalstellen abgerufen. Für Zeichentypen wird die maximale Länge in Zeichen abgerufen. Für binäre Typen wird die maximale Länge in Bytes abgerufen. Ist die Dezimalstellenanzahl unbekannt, wird von der Methode "0" zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerParameterMetaData-Methoden](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData-Elemente](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData-Klasse](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
