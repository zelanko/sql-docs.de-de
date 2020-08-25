---
description: Query-Methode (RDS)
title: Query-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Query method [ADO]
ms.assetid: 20f2480f-3758-405d-a379-05a0dce74796
author: rothja
ms.author: jroth
ms.openlocfilehash: 39bd8ccc67b0181088c267a60d6af2bf99035c02
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767929"
---
# <a name="query-method-rds"></a>Query-Methode (RDS)
Verwendet eine gültige SQL-Abfrage [Zeichenfolge](../ado-api/recordset-object-ado.md)zum Zurückgeben eines Recordsets.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set Recordset = DataFactory.Query(Connection, Query)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Recordset*  
 Eine Objekt Variable, die ein **Recordset** -Objekt darstellt.  
  
 *DataFactory*  
 Eine Objekt Variable, die ein [RDSServer. DataFactory](./datafactory-object-rdsserver.md) -Objekt darstellt.  
  
 *Connection*  
 Ein **Zeichen** folgen Wert, der die Server Verbindungsinformationen enthält. Dies ähnelt der [Connect](./connect-property-rds.md) -Eigenschaft.  
  
 *Abfrage*  
 Eine **Zeichenfolge** , die die SQL-Abfrage enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Abfrage sollte den SQL-Dialekt des Datenbankservers verwenden. Wenn ein Fehler mit der ausgeführten Abfrage vorliegt, wird ein Ergebnis Status zurückgegeben. Die **Abfrage** Methode führt keine Syntax Überprüfung der **Abfrage** Zeichenfolge aus.  
  
## <a name="applies-to"></a>Gilt für  
 [DataFactory-Objekt (RDSServer)](./datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [DataFactory-Objekt, Abfragemethode und CreateObject-Methode – Beispiel (VBScript)](./datafactory-object-query-method-and-createobject-method-example-vbscript.md)