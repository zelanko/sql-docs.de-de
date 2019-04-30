---
title: Volltextindizes für nicht persistente berechnete Spalten sind nicht zulässig. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 547ce7f80189cc15ea946f5cc8fab470ed83a754
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298278"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a>Volltextindizes sind für nicht permanente berechnete Spalten nicht zulässig
  Das Erstellen von Volltextindizes für nicht deterministische und unpräzise berechnete Spalten ist nicht zulässig. Solche Spalten können nicht als Typspalten bzw. nicht als Volltextschlüsselspalten verwendet werden.  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] kann ein Volltextindex mit einer nicht deterministischen und unpräzise berechneten Spalte als Typspalte oder als Volltextschlüsselspalte erstellt werden. Diese Funktionalität wird nicht unterstützt. Beim Upgrade werden ältere, nicht kompatible und nicht unterstützte Volltextindizes deaktiviert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um diese Volltextindizes zu aktivieren, ändern Sie die Spaltendefinitionen, sodass die Spalten deterministisch und präzise sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
