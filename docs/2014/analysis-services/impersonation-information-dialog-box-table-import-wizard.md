---
title: Identitätswechsel Informationen (Dialog Feld, Tabellen Import-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b29901213da4653c2d8867b9f450b359c39bded3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544253"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>Identitätswechselinformationen (Dialogfeld, Tabellenimport-Assistent)
  Verwenden Sie die Seite **Identitätswechselinformationen** , um die Anmeldeinformationen anzugeben, mit denen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] eine Verbindung mit der Datenquelle herstellt. Weitere Informationen zum Identitätswechsel mit Anmeldeinformationen finden Sie unter [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).  
  
## <a name="options"></a>Optionen  
 **Bestimmter Windows-Benutzername und bestimmtes Kennwort**  
 Wählen Sie diese Option aus, damit vom Tabellenmodell die Sicherheitsanmeldeinformationen eines angegebenen Windows-Benutzerkontos verwendet werden.  
  
 **Benutzername**  
 Geben Sie die Domäne und den Name des zu verwendenden Benutzerkontos ein. Verwenden Sie das folgende Format:  
  
 *\<Domain name>* **\\** *\<User account name>*  
  
 Die Option ist nur verfügbar, wenn die Option **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden** ausgewählt ist.  
  
 **Kennwort**  
 Geben Sie das Kennwort des Benutzerkontos ein, das vom Tabellenmodell verwendet werden soll.  
  
 Die Option ist nur verfügbar, wenn die Option **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden** ausgewählt ist.  
  
 **Dienstkonto**  
 Wählen Sie diese Option aus, damit die Sicherheitsanmeldeinformationen verwendet werden, die dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Dienst zugeordnet sind, der das Objekt verwaltet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Identitätswechsel &#40;SSAS – tabellarisch&#41;](tabular-models/impersonation-ssas-tabular.md)  
  
  
