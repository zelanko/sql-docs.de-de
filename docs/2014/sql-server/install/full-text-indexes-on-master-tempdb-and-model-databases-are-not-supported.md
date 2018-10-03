---
title: Volltextindizes für Master-, tempdb- und Model-Datenbanken werden nicht unterstützt. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f055640dbdbf4ece491b2d8552c1581b122faed3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064910"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>Volltextindizes werden für die Datenbanken 'master', 'tempdb' und 'model' nicht unterstützt
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt keine Volltextindizes für Systemdatenbanken zu.  
  
## <a name="description"></a>Description  
 Bei [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] wurden Volltextindizes für die Datenbanken master, tempdb und model unterstützt.  
  
 Alle Volltextkataloge in Master, Tempdb und Model-Datenbanken werden während des Upgrades entfernt.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
