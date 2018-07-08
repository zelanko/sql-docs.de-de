---
title: ISSCommandWithParameters (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ca1deccb70aeb15a9ea0b5422e84c35a40802c3d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410889"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **ISSCommandWithParameters** unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML und benutzerdefinierte Typen (UDT). Hierbei handelt es sich um eine optionale Schnittstelle, die von der OLE DB-Kernschnittstelle **ICommandWithParameters**erbt. Zusätzlich zu den drei von **ICommandWithParameters**geerbten Methoden **GetParameterInfo**, **MapParameterNames**und **SetParameterInfo**stellt **ISSCommandWithParameters** zur Verarbeitung serverspezifischer Datentypen zwei neue Methoden bereit.  
  
> [!NOTE]  
>  Die **ISSCommandWithParameters** -Schnittstelle kann bei Einsatz von Dienstkomponenten verwendet werden. Die Dienstkomponenten selbst verwenden diese Schnittstelle jedoch nicht.  
  
|Methode|Description|  
|------------|-----------------|  
|[Isscommandwithparameters:: Getparameterproperties &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|Gibt eine **SSPARAMPROPS** -Eigenschaftssatzstruktur im Array für jeden UDT- oder XML-Parameter zurück, der dem Befehl übergeben wurde. Für andere Parametertypen wird hingegen keine Struktur zurückgegeben.|  
|[Isscommandwithparameters:: SetParameterProperties &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|Legt die Parametereigenschaften auf einer Einzelparameterbasis nach Ordnungszahl fest oder legt Massenparametereigenschaften durch Angabe eines Arrays von **SSPARAMPROPS** -Strukturen fest.|  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE-DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [XML-Datentypen](../../relational-databases/native-client/features/using-xml-data-types.md)   
 [Verwenden von benutzerdefinierten Typen](../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
