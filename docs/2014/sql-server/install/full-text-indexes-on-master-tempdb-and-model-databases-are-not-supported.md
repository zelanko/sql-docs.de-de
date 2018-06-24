---
title: Volltextindizes für Master-, tempdb- und Model-Datenbanken werden nicht unterstützt. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1d334a3626c11050418df3fae483f5b9029adeb4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047988"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>Volltextindizes werden für die Datenbanken 'master', 'tempdb' und 'model' nicht unterstützt
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt keine Volltextindizes für Systemdatenbanken zu.  
  
## <a name="description"></a>Description  
 Bei [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] wurden Volltextindizes für die Datenbanken master, tempdb und model unterstützt.  
  
 Alle Volltextkataloge in Master, Tempdb und Model-Datenbanken werden während des Upgrades entfernt.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  