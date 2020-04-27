---
title: Eigenschaften des Sperren-Managers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- lock manager properties [Analysis Services]
- LockWaitGranularityMS property
- DefaultLockTimeoutMS property
- DeadlockDetectionGranularityMS property
ms.assetid: 15fe9ead-825b-4ac3-9191-7a07caa2861b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 607654924a9f7e2d071bbce1ee4797792cb760c9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068941"
---
# <a name="lock-manager-properties"></a>Eigenschaften des Sperren-Managers
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden die in der folgenden Tabelle aufgeführten Sperren-Manager-Servereigenschaften unterstützt. Weitere Informationen zu zusätzlichen Servereigenschaften und zum Festlegen dieser Eigenschaften finden Sie unter [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Gilt für:** mehrdimensionalen und Tabellenservermodus  
  
## <a name="properties"></a>Eigenschaften  
 `DefaultLockTimeoutMS`  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die das Standardsperrtimeout in Millisekunden für interne Sperranforderungen definiert.  
  
 Der Standardwert für diese Eigenschaft ist -1, d. h. es wurde kein Timeout für interne Sperranforderungen definiert.  
  
 `LockWaitGranularityMS`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `DeadlockDetectionGranularityMS`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Server Eigenschaften in Analysis Services](server-properties-in-analysis-services.md)   
 [Bestimmen des Servermodus einer Analysis Services-Instanz](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
