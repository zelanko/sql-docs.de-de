---
title: Anwendungs Domänen und Sicherheit der CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 85d6e66b1d51cc9d7c5829b8e83c510bea750e2a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933761"
---
# <a name="application-domains-and-clr-integration-security"></a>Anwendungsdomänen und Sicherheit der CLR-Integration
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lädt Assemblys, die demselben Besitzer gehören, in dieselbe Anwendungsdomäne. Bei einem Assemblysatz, die in derselben Anwendungsdomäne ausgeführt wird, können sich Assemblys während der Ausführung untereinander erkennen, indem sie den Reflexions-APIs von .NET Framework oder andere Verfahren anwenden, und können sich so auf spät gebundene Weise aufrufen. Da diese Aufrufe unter Assemblys stattfinden, die denselben Besitzer haben, werden dafür keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Berechtigungen überprüft. Das Platzierungsschema von Assemblys in Anwendungsdomänen wurde hauptsächlich mit Blick auf Skalierbarkeit, Sicherheit und Isolierung konzipiert und wird möglicherweise in zukünftigen Versionen geändert. Sie sollten sich daher nicht darauf verlassen, Assemblys mit später Bindung in derselben Anwendungsdomäne zu finden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit der CLR-Integration](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
