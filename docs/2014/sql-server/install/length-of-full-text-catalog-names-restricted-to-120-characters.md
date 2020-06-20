---
title: Länge von voll Text Katalog-Namen, die auf 120 Zeichen beschränkt sind | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fa9b06fa6fe4acd79782c19a8814357721e59c24
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85045205"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a>Länge von Volltextkatalognamen auf 120 Zeichen beschränkt
  Die Länge der Volltextkatalognamen ist auf 120 Zeichen beschränkt. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lag die Beschränkung bei 128 Zeichen.  
  
## <a name="description"></a>BESCHREIBUNG  
 Diese Änderung betrifft bestehende Katalognamen nicht. Skripts, die Volltextkatalognamen erstellen, die länger als 120 Zeichen sind, führen zu einem Fehler. Die Katalognamen werden dazu verwendet, logische Dateinamen zu generieren, die Katalogen entsprechen.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie alle Skripts, die Volltextkataloge erstellen, um sicherzustellen, dass die Katalognamen maximal 120 Zeichen umfassen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
