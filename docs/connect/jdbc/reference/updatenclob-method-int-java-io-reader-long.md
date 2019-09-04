---
title: updatenclob-Methode (int, Java. IO. Reader, Long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2bdbb539-0cb9-4047-98e3-7d6906af68f8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 93b6fca31afd24a8992e442096117d9479b52b48
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67998646"
---
# <a name="updatenclob-method-int-javaioreader-long"></a>updateNClob-Methode (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte unter Verwendung des angegebenen Reader-Objekts, dessen Länge der angegebenen Zeichenanzahl entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateNClob(int columnIndex,  
                        java.io.Reader reader,  
                        long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
 *reader*  
  
 Ein Reader-Objekt.  
  
 *length*  
  
 Die Anzahl von Zeichen in den Parameterdaten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateNClob-Methode wird von der updateNClob-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Diese Methode wird nur für Spalten vom Typ " **nvarchar (max)** ", " **ntext**" und " **XML** " unterstützt. Bei Verwendung dieser Methode für andere Datentypen wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateNClob-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
