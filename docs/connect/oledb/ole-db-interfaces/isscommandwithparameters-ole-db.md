---
title: ISSCommandWithParameters (OLE DB) | Microsoft-Dokumentation
description: ISSCommandWithParameters (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSCommandWithParameters (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSCommandWithParameters interface
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 2ae4bee1e0dd4fea3a5f52e46085da53f75dcab9
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030387"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die **ISSCommandWithParameters**-Schnittstelle stellt Unterstützung für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-XML- und benutzerdefinierte Typen (UDT) zur Verfügung. Hierbei handelt es sich um eine optionale Schnittstelle, die von der OLE DB-Schnittstelle **ICommandWithParameters** erbt. Zusätzlich zu den drei von **ICommandWithParameters** geerbten Methoden **GetParameterInfo**, **MapParameterNames** und **SetParameterInfo** stellt **ISSCommandWithParameters** zwei neue Methoden zur Verarbeitung serverspezifischer Datentypen bereit.  
  
> [!NOTE]  
>  Die **ISSCommandWithParameters**-Schnittstelle kann bei Einsatz von Dienstkomponenten verwendet werden. Die Dienstkomponenten selbst verwenden diese Schnittstelle jedoch nicht.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Isscommandwithparameters:: Getparameterproperties &#40;OLE-DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|Gibt eine **SSPARAMPROPS** -Eigenschaftssatzstruktur im Array für jeden UDT- oder XML-Parameter zurück, der dem Befehl übergeben wurde. Für andere Parametertypen wird hingegen keine Struktur zurückgegeben.|  
|[Isscommandwithparameters:: SetParameterProperties &#40;OLE-DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|Legt die Parametereigenschaften auf einer Einzelparameterbasis nach Ordnungszahl fest oder legt Massenparametereigenschaften durch Angabe eines Arrays von **SSPARAMPROPS** -Strukturen fest.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Schnittstellen &#40;OLE-DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)    
 [Using XML Data Types (Verwenden von XML-Datentypen)](../../oledb/features/using-xml-data-types.md)   
 [Verwenden von benutzerdefinierten Typen](../../oledb/features/using-user-defined-types.md)  
  
  
