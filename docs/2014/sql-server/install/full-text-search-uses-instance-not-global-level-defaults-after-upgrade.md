---
title: Aktualisieren von führt dazu, dass die Volltextsuche auf Instanzebene und nicht auf globaler wörtertrennungen und Filter standardmäßig verwendet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9c81892d6b83cef87a27a836d9691779a841104a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66095061"
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
  
  
