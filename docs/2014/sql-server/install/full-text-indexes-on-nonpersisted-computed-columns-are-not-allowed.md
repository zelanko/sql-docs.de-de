---
title: Volltextindizes für nicht persistente berechnete Spalten sind nicht zulässig | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 417ca3c2e5e477960c4c905543f3a712a5ec7453
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095171"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a>Volltextindizes sind für nicht permanente berechnete Spalten nicht zulässig
  Das Erstellen von Volltextindizes für nicht deterministische und unpräzise berechnete Spalten ist nicht zulässig. Solche Spalten können nicht als Typspalten bzw. nicht als Volltextschlüsselspalten verwendet werden.  
  
## <a name="description"></a>Beschreibung  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] kann ein Volltextindex mit einer nicht deterministischen und unpräzise berechneten Spalte als Typspalte oder als Volltextschlüsselspalte erstellt werden. Dies wird nicht unterstützt. Beim Upgrade werden ältere, nicht kompatible und nicht unterstützte Volltextindizes deaktiviert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um diese Volltextindizes zu aktivieren, ändern Sie die Spaltendefinitionen, sodass die Spalten deterministisch und präzise sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
