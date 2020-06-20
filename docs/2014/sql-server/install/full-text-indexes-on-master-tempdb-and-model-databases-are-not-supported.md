---
title: Volltextindizes für Master-, tempdb-und Model-Datenbanken werden nicht unterstützt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fbd5e3133ed87fed9bdaf6d668df62c6471df766
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012456"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>Volltextindizes werden für die Datenbanken 'master', 'tempdb' und 'model' nicht unterstützt
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt keine Volltextindizes für Systemdatenbanken zu.  
  
## <a name="description"></a>BESCHREIBUNG  
 Bei [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] wurden Volltextindizes für die Datenbanken master, tempdb und model unterstützt.  
  
 Alle voll Text Kataloge in den Datenbanken Master, tempdb und Model werden während des Upgrades entfernt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
