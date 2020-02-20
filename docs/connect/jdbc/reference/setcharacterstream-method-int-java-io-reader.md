---
title: setCharacterStream-Methode (int, java.io.Reader) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8d4e1f7-14fc-4590-af98-1eda30d2ca6d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d97ed3360db0d1a81f71225e4664c6624cb9da37
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67974698"
---
# <a name="setcharacterstream-method-int-javaioreader"></a>setCharacterStream-Methode (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf das angegebene java.io.Reader-Objekt fest.  
  
> [!NOTE]
>  Dieses Feature wird mit Version 2.0 des JDBC-Treibers für [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eingeführt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setCharacterStream(int parameterIndex,  
                              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterIndex*  
  
 Ein Wert **ganzzahliger** Wert zum Angeben der Parameternummer.  
  
 *reader*  
  
 Das java.io.Reader-Objekt, das die Unicodedaten enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setCharacterStream-Methode wird von der setCharacterStream-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setCharacterStream-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
