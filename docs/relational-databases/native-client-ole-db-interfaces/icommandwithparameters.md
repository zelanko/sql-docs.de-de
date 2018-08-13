---
title: ICommandWithParameters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 08acaa9ef4d1dae0a1cd104b4703edb8a0836437
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555450"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Verbesserungen in der Datenbank-Engine ab mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ICommandWithParameters:: GetParameterInfo, genauere Beschreibungen der erwarteten Ergebnisse abrufen können. Diese genaueren Ergebnisse unterscheiden sich möglicherweise aus den Werten, die vom CommandWithParameters::GetParameterInfo in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] muss beim Aufrufen von ICommandWithParameters::SetParameterInfo der an den Parameter *pwszName* übergebene Wert ein gültiger Bezeichner sein. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE-DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
