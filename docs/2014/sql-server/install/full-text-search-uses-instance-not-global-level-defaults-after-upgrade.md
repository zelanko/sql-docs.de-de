---
title: Aktualisieren von führt dazu, dass die Volltextsuche auf Instanzebene und nicht auf globaler wörtertrennungen und Filter standardmäßig verwendet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d1974d81e36842f8c8d2c8ae70eceec26acb2dfe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175680"
---
# <a name="upgrading-will-cause-full-text-search-to-use-instance-level-not-global-word-breakers-and-filters-by-default"></a>Das Upgrade bewirkt, dass die Volltextsuche Wörtertrennungen und Filter standardmäßig auf Instanzebene statt auf globaler Ebene verwendet
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bietet eine Option, mit der die Registrierung von neuen Wörtertrennungen und Filtern auf der Instanzebene zugelassen werden kann.  
  
## <a name="component"></a>Komponente  
 Volltextsuche  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht die Registrierung neuer Wörtertrennungen und Filter auf Instanzebene. Durch diese Registrierung auf Instanzebene wird die Funktions- und Sicherheitsisolation zwischen Instanzen bereitgestellt.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden Sie nach dem Upgrade `sp_fulltext_service`, um die Diensteigenschaft und `load_os_resources` festzulegen. Dadurch wird das Laden der Komponenten ermöglicht. Führen Sie Folgendes aus:  
  
 `sp_fulltext_service 'load_os_resources', 1`  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
