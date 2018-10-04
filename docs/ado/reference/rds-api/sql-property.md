---
title: SQL-Eigenschaft | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SQL property [RDS]
ms.assetid: e0dabf23-a159-4fe5-a962-3df544a21f5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4d665e2b2f9ac4d61951da3cccbd16db76127a5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727018"
---
# <a name="sql-property"></a>SQL-Eigenschaft
Gibt die Abfragezeichenfolge zum Abrufen der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Sie können festlegen, die **SQL** Eigenschaft zur Entwurfszeit in den [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekttags des Objekts, oder zur Laufzeit im Skriptcode.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>Parameter  
 *QueryString*  
 Ein **Zeichenfolge** Wert, der eine gültige SQL-Daten-Anforderung enthält.  
  
 *DataControl*  
 Eine Objektvariable, steht ein **RDS. DataControl** Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Im Allgemeinen ist dies eine SQL-Anweisung (mit den Dialekt des Datenbankservers), wie z. B. `"Select * from NewTitles"`. Um sicherzustellen, dass Datensätze übereinstimmen und richtig aktualisiert werden, muss eine aktualisierbare Abfrage ein Feld als ein Long Binary-Feld oder ein berechnetes Feld enthalten.  
  
 Die **SQL** Eigenschaft ist optional, wenn eine benutzerdefinierte serverseitige Geschäftsobjekt, das die Daten für den Client abruft.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL-Eigenschaft – Beispiel (VBScript)](../../../ado/reference/rds-api/sql-property-example-vbscript.md)   
 [Connect-Eigenschaft (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Abfragemethode (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Refresh-Methode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges-Methode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


