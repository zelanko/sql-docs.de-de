---
title: Eigenschaften des Sperren-Manager | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8d228c006c3bb27dbdd3227abeae2882234a6042
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="lock-manager-properties"></a>Eigenschaften des Sperren-Managers
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden die in der folgenden Tabelle aufgeführten Sperren-Manager-Servereigenschaften unterstützt. Weitere Informationen zu zusätzlichen Servereigenschaften und zum Festlegen dieser Eigenschaften finden Sie unter [Servereigenschaften in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Gilt für:** mehrdimensionalen und Tabellenservermodus  
  
## <a name="properties"></a>Eigenschaften  
 **DefaultLockTimeoutMS**  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die das Standardsperrtimeout in Millisekunden für interne Sperranforderungen definiert.  
  
 Der Standardwert für diese Eigenschaft ist -1, d. h. es wurde kein Timeout für interne Sperranforderungen definiert.  
  
 **LockWaitGranularityMS**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **DeadlockDetectionGranularityMS**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
## <a name="see-also"></a>Siehe auch  
 [Servereigenschaften in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Bestimmen des Servermodus einer Analysis Services-Instanz](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
