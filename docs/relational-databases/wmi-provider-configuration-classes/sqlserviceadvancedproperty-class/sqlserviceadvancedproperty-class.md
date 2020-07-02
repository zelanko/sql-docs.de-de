---
title: SqlServiceAdvancedProperty-Klasse
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- SqlServiceAdvancedProperty Class
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceAdvancedProperty class
ms.assetid: a5d06bde-6058-464c-a4aa-444d83f2331f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8dc6c2294d089ca86f571eec5f348c4270782740
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734299"
---
# <a name="sqlserviceadvancedproperty-class"></a>SqlServiceAdvancedProperty-Klasse
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Die [SqlServiceAdvancedProperty-Klasse](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) stellt eine erweiterte Eigenschaft des Dienst dar, auf den durch das Objekt der [SqlService-Klasse](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) verwiesen wird.  
  
 Die [AdvancedProperties-Eigenschaft (SqlService-Klasse)](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/advancedproperties-property-sqlservice-class.md) verweist auf ein Array von [SqlServiceAdvancedProperty-Klassenobjekten](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) .  
  
 Die Klasse zum [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx) stellt Eigenschaften dar, die spezifisch für den Dienst sind. Diese Eigenschaften sind nicht in der Liste der Eigenschaften aufgeführt, die der [SqlService-Klasse](https://technet.microsoft.com/library/ms186497.aspx) zugeordnet sind. Mit der [SqlServiceAdvancedProperty-Klasse](https://technet.microsoft.com/library/ms182447.aspx) können Eigenschaften vom Typ string, numeric oder Boolean dargestellt werden. Sie können mithilfe dieser Klasse die einzigartigen Eigenschaften des angegebenen Diensts anzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten, Beenden und Anhalten von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
