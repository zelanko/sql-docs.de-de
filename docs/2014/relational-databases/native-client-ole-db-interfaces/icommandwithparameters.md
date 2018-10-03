---
title: ICommandWithParameters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea85e526d99e586c2534eee8ab83c6ddc66939db
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125540"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
  Verbesserungen in der Datenbank-Engine ab mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ICommandWithParameters:: GetParameterInfo, genauere Beschreibungen der erwarteten Ergebnisse abrufen können. Diese genaueren Ergebnisse unterscheiden sich möglicherweise aus den Werten, die vom CommandWithParameters::GetParameterInfo in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
 Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] muss beim Aufrufen von ICommandWithParameters::SetParameterInfo der an den Parameter *pwszName* übergebene Wert ein gültiger Bezeichner sein. Weitere Informationen finden Sie unter [Datenbankbezeichner](../databases/database-identifiers.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE-DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
