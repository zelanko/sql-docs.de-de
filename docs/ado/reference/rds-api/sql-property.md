---
description: SQL-Eigenschaft
title: SQL-Eigenschaft | Microsoft-Dokumentation
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5da63f3c5a5acbf217a5bc585dc1be9d9af7feab
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88981081"
---
# <a name="sql-property"></a>SQL-Eigenschaft
Gibt die Abfrage [Zeichenfolge](../ado-api/recordset-object-ado.md)an, mit der das Recordset abgerufen wird.  
  
 Sie können die **SQL** -Eigenschaft zur Entwurfszeit im [RDS festlegen. Objekt Tags des DataControl](./datacontrol-object-rds.md) -Objekts oder zur Laufzeit im Skriptcode.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>Parameter  
 *QueryString*  
 Ein **Zeichen** folgen Wert, der eine gültige SQL-Daten Anforderung enthält.  
  
 *DataControl*  
 Eine Objekt Variable, die einen **RDS darstellt. DataControl** -Objekt.  
  
## <a name="remarks"></a>Bemerkungen  
 Im Allgemeinen handelt es sich hierbei um eine SQL-Anweisung (mit dem Dialekt des Datenbankservers), z `"Select * from NewTitles"` . b.. Um sicherzustellen, dass Datensätze korrekt abgeglichen und aktualisiert werden, muss eine aktualisierbare Abfrage ein anderes Feld als ein langes binäres Feld oder ein berechnetes Feld enthalten.  
  
 Die **SQL** -Eigenschaft ist optional, wenn ein benutzerdefiniertes serverseitiges Geschäftsobjekt die Daten für den Client abruft.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL-Eigenschafts Beispiel (VBScript)](./sql-property-example-vbscript.md)   
 [Connect-Eigenschaft (RDS)](./connect-property-rds.md)   
 [Query-Methode (RDS)](./query-method-rds.md)   
 [Refresh-Methode (RDS)](./refresh-method-rds.md)   
 [SubmitChanges-Methode (RDS)](./submitchanges-method-rds.md)