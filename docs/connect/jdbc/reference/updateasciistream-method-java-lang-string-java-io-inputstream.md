---
title: updateAsciiStream-Methode (java.io.InputStream) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 747b0308-1ce6-4eba-bdfc-af29c21c18cf
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a9fbb5f5c74a549a84e54980d585b7b5c30f61a5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66798925"
---
# <a name="updateasciistream-method-javalangstring-javaioinputstream"></a>updateAsciiStream-Methode (java.lang.String, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem ASCII-Datenstromwert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateAsciiStream(java.lang.String columnLabel,  
                              java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnLabel*  
  
 Eine **Zeichenfolge**, die die Spaltenbezeichnung enthält.  
  
 *x*  
  
 Ein InputStream-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese UpdateAsciiStream-Methode wird von der UpdateAsciiStream-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode werden ASCII-Zeichen (Bytes) von einem InputStream-Objekt an konvertierbare Zeichenspalten übergeben, bei denen es sich um den ASCII-Bereich „[0x00 – 0x7F]“ von Unicode sowie um die Codepages 874, 932, 936, 949, 950 und 1250 bis 1258 handelt. Von dieser Methode wird eine Konvertierung zur Zielsortierseite vorgenommen. Beim Versuch, eine nicht konvertierbare Zielspalte zu aktualisieren, wird eine Ausnahme ausgelöst. Für Binärspalten werden Rohbytes übergeben.  
  
 Mit dieser Methode für die **Image**, **Text**, und **Ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datentypen können die Leistung beeinträchtigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateAsciiStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
