---
title: Identitätswechsel (Dialogfeld) (Tabellenimport-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5c9d9b49d41d8f9320ff414925bb4532145d16f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245680"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>Identitätswechselinformationen (Dialogfeld, Tabellenimport-Assistent)
  Verwenden Sie die Seite **Identitätswechselinformationen** , um die Anmeldeinformationen anzugeben, mit denen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] eine Verbindung mit der Datenquelle herstellt. Weitere Informationen zum Identitätswechsel mit Anmeldeinformationen finden Sie unter [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).  
  
## <a name="options"></a>Tastatur  
 **Bestimmten Windows-Benutzernamen und Kennwort**  
 Wählen Sie diese Option aus, damit vom Tabellenmodell die Sicherheitsanmeldeinformationen eines angegebenen Windows-Benutzerkontos verwendet werden.  
  
 **Benutzername**  
 Geben Sie die Domäne und den Name des zu verwendenden Benutzerkontos ein. Verwenden Sie folgendes Format:  
  
 *\<Domänenname >* **\\**  *\<Benutzerkontonamen >*  
  
 Die Option ist nur verfügbar, wenn die Option **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden** ausgewählt ist.  
  
 **Kennwort**  
 Geben Sie das Kennwort des Benutzerkontos ein, das vom Tabellenmodell verwendet werden soll.  
  
 Die Option ist nur verfügbar, wenn die Option **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden** ausgewählt ist.  
  
 **Dienstkonto**  
 Wählen Sie diese Option aus, damit die Sicherheitsanmeldeinformationen verwendet werden, die dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Dienst zugeordnet sind, der das Objekt verwaltet.  
  
## <a name="see-also"></a>Siehe auch  
 [Identitätswechsel &#40;SSAS – tabellarisch&#41;](tabular-models/impersonation-ssas-tabular.md)  
  
  
