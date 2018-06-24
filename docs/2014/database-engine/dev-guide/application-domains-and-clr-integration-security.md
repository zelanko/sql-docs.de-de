---
title: Anwendungsdomänen und Sicherheit der CLR-Integration | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0c97f958126dc7b19478bf0864a23ce4ab4fe07b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057251"
---
# <a name="application-domains-and-clr-integration-security"></a>Anwendungsdomänen und Sicherheit der CLR-Integration
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lädt Assemblys, die demselben Besitzer in der gleichen Anwendungsdomäne gehören. Bei einem Assemblysatz, die in derselben Anwendungsdomäne ausgeführt wird, können sich Assemblys während der Ausführung untereinander erkennen, indem sie den Reflektions-APIs von .NET Framework oder andere Verfahren anwenden, und können sich so auf spät gebundene Weise aufrufen. Da diese Aufrufe unter Assemblys stattfinden, die denselben Besitzer haben, werden dafür keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Berechtigungen überprüft. Das Platzierungsschema von Assemblys in Anwendungsdomänen wurde hauptsächlich mit Blick auf Skalierbarkeit, Sicherheit und Isolierung konzipiert und wird möglicherweise in zukünftigen Versionen geändert. Sie sollten sich daher nicht darauf verlassen, Assemblys mit später Bindung in derselben Anwendungsdomäne zu finden.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit der CLR-Integration](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  